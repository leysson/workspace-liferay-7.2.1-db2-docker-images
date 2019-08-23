# How to build a Docker Liferay 7.2 image with the Oracle Database support

![](https://www.dontesta.it/wp-content/uploads/2019/08/HowToBuildLiferay72DockerImageFeatureImage.png)

This is the repository of the Liferay Workspace (version 7.2) linked to the article [How to build Docker Liferay 7.2 image with the Oracle Database support](https://www.dontesta.it/en/2019/08/21/how-to-build-a-docker-liferay-7-2-image-with-the-oracle-database-support/) published on the blog [Antonio Musarra's Blog](https://www.dontesta.it).

The content of this repository is ready for use. The steps you need to perform to start your container immediately is:



1. An instance of an Oracle 12c Release 2 database
2. Clone this repository
3. Review JDBC Connection on **configs/docker/portal-ext.properties**
4. Build custom image
5. Start custom image



```bash
$ git clone https://github.com/amusarra/liferay-72-oracledb-docker-images.git
$ cd liferay-72-oracledb-docker-images
$ vi configs/docker/portal-ext.properties # For review JDBC Connection settings
$ blade gw clean buildDockerImage -Pliferay.workspace.environment=docker
$ docker run -d -it --name Liferay72-Oracle \
	-p 8080:8080 -p 11311:11311 \
	-v $(pwd)/build/docker:/etc/liferay/mount \
	-P liferay-72-oracledb-docker-images:docker
```

Console 1 - Commands to execute to start the custom image



You can now manage Liferay’s Docker images in Liferay Workspace and push your Docker custom image on Docker Hub or other registry ! 😉

## Project License

The MIT License (MIT)

Copyright © 2019 Antonio Musarra's Blog - [https://www.dontesta.it](https://www.dontesta.it/), antonio.musarra@gmail.com

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.