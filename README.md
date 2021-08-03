# Jenkinks-jobs-cloning-Github-repo
This repository shows the steps I took in creating a job that would clone an app from a given Github repo. 

## Method 1 - Freestyle job

**Step 1** - Create the job. From the Jenkins dashboard, select the New Item option. Enter a suggestive name for your job; in my case, it is called it *CloneRepo*. Next, choose the Freestyle project and click OK.

**Step 2** - Set up the job. The menu that just appeared is divided into several tabs: General, Source Code Management, Build Triggers, Build Environment, Build, and Post-build Access. Go to Source Code Management, choose the Git option, then provide the repository URL you intend to copy. For my assignment, I used https://github.com/MarilenaIstrate/simple-java-maven-app. 

I left Credentials set as none, and finally I specified the branches I wanted to build, i.e. the master branch, by typing "branch" into the Branch Specifier option. Click on Apply, then Save.

**Step 3** - Build the project. Return to the dashboard and select Build now. Since everything went right, compiling my project returned SUCCESS. The output console result can be seen below:

```sh
Started by user admin
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/CloneRepo
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/MarilenaIstrate/simple-java-maven-app
 > git init /var/lib/jenkins/workspace/CloneRepo # timeout=10
Fetching upstream changes from https://github.com/MarilenaIstrate/simple-java-maven-app
 > git --version # timeout=10
 > git --version # 'git version 2.17.1'
 > git fetch --tags --progress -- https://github.com/MarilenaIstrate/simple-java-maven-app +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/MarilenaIstrate/simple-java-maven-app # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse origin/master^{commit} # timeout=10
Checking out Revision 47e8488dece89ed322a9cada0cdcbfebbad80f8c (origin/master)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 47e8488dece89ed322a9cada0cdcbfebbad80f8c # timeout=10
Commit message: "Update pom.xml"
First time build. Skipping changelog.
Finished: SUCCESS
```

**Step 4** - Publish the JUnit test result. Access the target/surefire-reports/ path to find the .xml file containing the unit test results. Below I attached the contents of my .xml file.

```sh
<?xml version="1.0" encoding="UTF-8"?>
<testsuite xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://maven.apache.org/surefire/maven-surefire-plugin/xsd/surefire-test-report.xsd" name="unitTests.amgrads.MockitoCheckNameTest" time="2.835" tests="1" errors="0" skipped="0" failures="0">
  <properties>
    <property name="java.runtime.name" value="Java(TM) SE Runtime Environment"/>
    <property name="sun.boot.library.path" value="/opt/jdk/jdk1.8.0_202/jre/lib/amd64"/>
    <property name="java.vm.version" value="25.202-b08"/>
    <property name="java.vm.vendor" value="Oracle Corporation"/>
    <property name="maven.multiModuleProjectDirectory" value="/vagrant/source"/>
    <property name="java.vendor.url" value="http://java.oracle.com/"/>
    <property name="path.separator" value=":"/>
    <property name="guice.disable.misplaced.annotation.check" value="true"/>
    <property name="java.vm.name" value="Java HotSpot(TM) 64-Bit Server VM"/>
    <property name="file.encoding.pkg" value="sun.io"/>
    <property name="user.country" value="US"/>
    <property name="sun.java.launcher" value="SUN_STANDARD"/>
    <property name="sun.os.patch.level" value="unknown"/>
    <property name="java.vm.specification.name" value="Java Virtual Machine Specification"/>
    <property name="user.dir" value="/vagrant/source"/>
    <property name="java.runtime.version" value="1.8.0_202-b08"/>
    <property name="java.awt.graphicsenv" value="sun.awt.X11GraphicsEnvironment"/>
    <property name="java.endorsed.dirs" value="/opt/jdk/jdk1.8.0_202/jre/lib/endorsed"/>
    <property name="os.arch" value="amd64"/>
    <property name="java.io.tmpdir" value="/tmp"/>
    <property name="line.separator" value="&#10;"/>
    <property name="java.vm.specification.vendor" value="Oracle Corporation"/>
    <property name="os.name" value="Linux"/>
    <property name="classworlds.conf" value="/usr/local/apache-maven/bin/m2.conf"/>
    <property name="sun.jnu.encoding" value="UTF-8"/>
    <property name="java.library.path" value="/usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib"/>
    <property name="maven.conf" value="/usr/local/apache-maven/conf"/>
    <property name="java.specification.name" value="Java Platform API Specification"/>
    <property name="java.class.version" value="52.0"/>
    <property name="sun.management.compiler" value="HotSpot 64-Bit Tiered Compilers"/>
    <property name="os.version" value="3.13.0-170-generic"/>
    <property name="library.jansi.path" value="/usr/local/apache-maven/lib/jansi-native"/>
    <property name="user.home" value="/home/vagrant"/>
    <property name="user.timezone" value="Etc/UTC"/>
    <property name="java.awt.printerjob" value="sun.print.PSPrinterJob"/>
    <property name="java.specification.version" value="1.8"/>
    <property name="file.encoding" value="UTF-8"/>
    <property name="user.name" value="vagrant"/>
    <property name="java.class.path" value="/usr/local/apache-maven/boot/plexus-classworlds-2.5.2.jar"/>
    <property name="java.vm.specification.version" value="1.8"/>
    <property name="sun.arch.data.model" value="64"/>
    <property name="java.home" value="/opt/jdk/jdk1.8.0_202/jre"/>
    <property name="sun.java.command" value="org.codehaus.plexus.classworlds.launcher.Launcher clean deploy"/>
    <property name="java.specification.vendor" value="Oracle Corporation"/>
    <property name="user.language" value="en"/>
    <property name="awt.toolkit" value="sun.awt.X11.XToolkit"/>
    <property name="java.vm.info" value="mixed mode"/>
    <property name="java.version" value="1.8.0_202"/>
    <property name="java.ext.dirs" value="/opt/jdk/jdk1.8.0_202/jre/lib/ext:/usr/java/packages/lib/ext"/>
    <property name="securerandom.source" value="file:/dev/./urandom"/>
    <property name="sun.boot.class.path" value="/opt/jdk/jdk1.8.0_202/jre/lib/resources.jar:/opt/jdk/jdk1.8.0_202/jre/lib/rt.jar:/opt/jdk/jdk1.8.0_202/jre/lib/sunrsasign.jar:/opt/jdk/jdk1.8.0_202/jre/lib/jsse.jar:/opt/jdk/jdk1.8.0_202/jre/lib/jce.jar:/opt/jdk/jdk1.8.0_202/jre/lib/charsets.jar:/opt/jdk/jdk1.8.0_202/jre/lib/jfr.jar:/opt/jdk/jdk1.8.0_202/jre/classes"/>
    <property name="java.vendor" value="Oracle Corporation"/>
    <property name="maven.home" value="/usr/local/apache-maven"/>
    <property name="file.separator" value="/"/>
    <property name="java.vendor.url.bug" value="http://bugreport.sun.com/bugreport/"/>
    <property name="sun.cpu.endian" value="little"/>
    <property name="sun.io.unicode.encoding" value="UnicodeLittle"/>
    <property name="sun.cpu.isalist" value=""/>
  </properties>
  <testcase name="checkDate" classname="unitTests.amgrads.MockitoCheckNameTest" time="2.273"/>
</testsuite>
```
