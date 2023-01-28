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

```
FROM ubuntu:latest

RUN apt-get update && apt-get install -y build-essential

COPY main.cpp /app/main.cpp

WORKDIR /app

RUN g++ -std=c++11 main.cpp -o main

CMD ["./main"]
```
