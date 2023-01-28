# Docker Use Cases

Some Use Cases of Docker Here

## Run C++ Hello World Application

In a project root folder. We have this main.cpp file

main.cpp
```cpp
#include <iostream>

int main() {
    std::cout << "Hello World";
    return 0;
}
```

We can create Dockerfile in this same folder to describe how we want to run this.

```dockerfile
FROM ubuntu:latest

RUN apt-get update && apt-get install -y build-essential

COPY main.cpp /app/main.cpp

WORKDIR /app

RUN g++ -std=c++11 main.cpp -o main

CMD ["./main"]
```

The exaplanation of the updated code (Thanks to CHAT-GPT)

- The code apt-get update && apt-get install -y build-essential is used to update the package list of the base image and install the build-essential package on the Docker container.

- apt-get update is used to update the package list of the base image. This ensures that the package list is up to date and that the latest versions of packages are available to be installed.

- apt-get install -y build-essential is used to install the build-essential package on the Docker container. The build-essential package is a metapackage that installs a set of packages necessary to build software on a Debian-based system. It includes the g++ compiler, make, and other development tools that are necessary to build and compile C++ code.

- The -y flag tells apt-get to assume "yes" as an answer to any question that is asked during the installation process, avoiding any manual interaction.

- This command is commonly used in Dockerfile as a part of installing dependencies for building software, in this case, a C++ application,

- By including this command in the Dockerfile, you can ensure that your C++ application has all the necessary dependencies and tools to build and run correctly in the container.
```
