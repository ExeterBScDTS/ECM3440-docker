# ECM3440-docker

## Getting started with docker

Hello world

```shell
$ docker run hello-world
```

Containers can provide interactive shells, like this.

```shell
C:\> docker run -it ubuntu

root@e123af1ae953:/#
```

Or this.

```shell
$ docker run -it python:3.8
Python 3.8.5 (default, Sep 10 2020, 16:47:10) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

To learn much more, see <https://docs.docker.com/get-started/overview/>

If you're working in VS Code install the extension <https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker>

If you don't have Docker installed and want to try Docker then you can use the docker command in VS Code online Codespaces. 

<https://online.visualstudio.com/login>

And in Google Cloud Shell.

<https://cloud.google.com/shell/docs/>


## Our aim is to use custom containers for Azure Functions

<https://docs.microsoft.com/en-gb/azure/azure-functions/functions-create-function-linux-custom-image?tabs=bash%2Cportal&pivots=programming-language-python>

But first try some experiments.

## Some useful Docker images



### pandoc

Pandoc is a Haskell library for converting from one markup format to another, and a command-line tool that uses this library.

Pandoc can convert between numerous markup and word processing formats, including, but not limited to, various flavors of Markdown, HTML, LaTeX and Word docx. Pandoc can also produce PDF output.

<https://pandoc.org>

<https://hub.docker.com/r/jpbernius/pandoc/>

Windows PowerShell or Linux bash

```shell
$ docker run --rm -v ${PWD}:/data jpbernius/pandoc -o README.docx README.md
```

Or try the demo script.

```shell
$ convertdoc README.md README.pdf
```

Note that Docker rarely runs inside another Docker container, so we need to know where directories are actually mounted when running
inside a container.

```shell
$ docker inspect -f "{{ .Mounts }}" `sudo docker ps -q`
```

### ffmpeg

FFmpeg is open source software for *transcoding* - the conversion of digital audio and visual streams from one format to another. <https://ffmpeg.org/>

<https://hub.docker.com/r/jrottenberg/ffmpeg>

### Microsoft SQL Server

<https://hub.docker.com/_/microsoft-mssql-server>

Example. Note that port is forwarded.

```sh
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -p 1433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

See <https://docs.docker.com/config/containers/container-networking/>

