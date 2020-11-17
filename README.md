# Install Jupyter notebook and Java Kernel

------

Pre request Softwares
----------------------------------------------
1. Java11 JDK https://www.oracle.com/java/technologies/javase-jdk11-downloads.html
2. Python3 https://www.python.org/downloads/release/python-386/
3. pip https://phoenixnap.com/kb/install-pip-windows
4. Install Jupyter: python -m pip install jupyter
5. set PYTHON_HOME, PYTHON_SCRIPT in environment variables after jupyter,pip installed all exe resides in %PYTHON_HOME%/script so add them in path
6. Installing Gradle https://gradle.org/install/#manually
and set Gradle in the system path (Environment variables)
6. Download git clone https://github.com/SpencerPark/IJava.git
7.  Go to the extracted folder IJava> and run below Gradle commands
- gradle wrapper
-   gradlew
- gradlew installKernel

Troubleshoot: To fix python classpath issue
 Run ,/gradlew installKernel --python python
Note: sometimes java kernel would have already installed so better to check with jupyter kernelspec list

Checkout output:
C:\Users\Dell\IJava>jupyter kernelspec list
Available kernels:
  java       C:\Users\Dell\AppData\Roaming\jupyter\kernels\java
  python3    c:\users\dell\appdata\local\programs\python\python38\share\jupyter\kernels\python3
