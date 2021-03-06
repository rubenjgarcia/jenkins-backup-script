# Jenkins backup script

Archive Jenkins settings and plugins

* $JENKINS_HOME/*.xml
* $JENKINS_HOME/plugins/*.jpi
* $JENKINS_HOME/jobs/*/*.xml

# Usage
```sh
./jenkins-backup.sh /path/to/jenkins_home archive.tar.gz

# add timestamp suffix
./jenkins-backup.sh /path/to/jenkins_home backup_`date +"%Y%m%d%H%M%S"`.tar.gz
```

# run with Jenkins Job
## 1. install Exclusive Execution Plugin
https://wiki.jenkins-ci.org/display/JENKINS/Exclusive+Execution+Plugin

## 2. New Job
![img](http://cdn-ak.f.st-hatena.com/images/fotolife/s/sue445/20131208/20131208001948.png)

## 3. Configure
### Source Code Management > Repository URL
```
git@github.com:sue445/jenkins-backup-script.git
```

**Recommended** : specify Branch Specifier with latest release tag (ex. 0.0.3)

![0.0.3](http://f.st-hatena.com/images/fotolife/s/sue445/20140331/20140331010645.png)

### Build Triggers > Build periodically
![img](http://cdn-ak.f.st-hatena.com/images/fotolife/s/sue445/20131110/20131110180825.png)

### Build Environment > Set exclusive Execution
![img](http://cdn-ak.f.st-hatena.com/images/fotolife/s/sue445/20131110/20131110194540.png)

### Build > Execute shell
![img](http://cdn-ak.f.st-hatena.com/images/fotolife/s/sue445/20131110/20131110193935.png)

ex.

```
./jenkins-backup.sh $JENKINS_HOME /path/to/backup_`date +"%Y%m%d%H%M%S"`.tar.gz
```

# Operability confirmed
* Debian lenny
* CentOS 6

# Changelog
## master
[full changelog](https://github.com/sue445/jenkins-backup-script/compare/0.0.3...master)

## 0.0.3
[full changelog](https://github.com/sue445/jenkins-backup-script/compare/0.0.2...0.0.3)

* There are cases where the directory is not created

## 0.0.2
[full changelog](https://github.com/sue445/jenkins-backup-script/compare/0.0.1...0.0.2)

* remove archive file if exixts

## 0.0.1
* first release
