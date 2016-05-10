# ymcdull/emojicode
- This repository is built based on emojicode: www.emojicode.org
- The Github URL: https://github.com/emojicode/emojicode

## Dockerfile
```sh
FROM ubuntu

RUN apt-get update
RUN apt-get -y install wget vim ttf-ancient-fonts git
WORKDIR /home
RUN wget https://github.com/emojicode/emojicode/releases/download/v0.2.0-beta.5/Emojicode-0.2.0-beta.5-x86_64-linux-gnu.tar.gz
RUN tar -zxvf Emojicode-0.2.0-beta.5-x86_64-linux-gnu.tar.gz
WORKDIR Emojicode-0.2.0-beta.5-x86_64-linux-gnu
RUN git clone https://github.com/emojicode/emojicode sourcefile
ENV TERM xterm
RUN ./install.sh
```

## Usage 
Create a docker container and use bash to enter
```sh
$ docker run -it ymcdull/emojicode:0.1 bash 
```
Already inside of the container as the root identity, enter the test cases directory
```sh
$ cd sourcefile/tests/
```
Compile the ".emojic" file, and will generate ".emojib" file. Like compiling C language from .c to .o file, emojicode is from .emojic to .emojib
```sh
$ emojicodec rangeTest.emojic
```
Run the ".emojib" file
```sh
$ emojicode rangeTest.emojib
```
