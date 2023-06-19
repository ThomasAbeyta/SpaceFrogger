# PDS transform in Docker

- Installing Java on Ubuntu: https://ubuntu.com/tutorials/install-jre#2-installing-openjdk-jre
- Install PDS tranform: https://nasa-pds.github.io/transform/install/index.html

## Build the image
```bash
docker image build --tag pds-transform:1.11.5 .
```

## Run an instance in the background
```bash
docker container run -d -v ${PWD}:/tmp/zfoo -w /tmp/zfoo --name pds pds-transform:1.11.5 sleep inf
```

## Download sample data
```bash
docker container exec -i pds /bin/bash <<'eof'
  wget https://sbnarchive.psi.edu/pds4/non_mission/gbo.ast.52-color-survey.zip
  unzip gbo.ast.52-color-survey.zip '*511*'
eof
```

## Tranform sample data
Transforming an xml file to csv requires both the xml and the tab file.
```bash
docker container exec -i pds /bin/bash <<'eof'
  transform gbo.ast.52-color-survey/data/data3/511davida.xml -f csv -o gbo.ast.52-color-survey/data/data3/
eof
```

## Enter an interactive session
```bash
docker container exec -it pds /bin/bash
````

## Destroy the instance
```bash
docker container stop pds
docker container rm pds
```



