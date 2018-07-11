[linuxserverurl]: https://linuxserver.io
[forumurl]: https://forum.linuxserver.io
[ircurl]: https://www.linuxserver.io/irc/
[podcasturl]: https://www.linuxserver.io/podcast/
[huburl]: https://hub.docker.com/r/linuxserver/ci/
[pipelineurl]: https://github.com/linuxserver/pipeline-triggers

[![linuxserver.io](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/linuxserver_medium.png?v=4&s=4000)][linuxserverurl]


## Contact information:-

| Type | Address/Details |
| :---: | --- |
| Discord | [Discord](https://discord.gg/YWrKVTn) |
| Forum | [Linuserver.io forum][forumurl] |
| IRC | freenode at `#linuxserver.io` more information at:- [IRC][ircurl]
| Podcast | Covers everything to do with getting the most from your Linux Server plus a focus on all things Docker and containerisation! [Linuxserver.io Podcast][podcasturl] |

# [linuxserver/ci][huburl]

**This container is not meant for public consumption as it is hard coded to LinuxServer endpoints for storage of resulting reports**

The purpose of this container is to accept environment variables from our build system [linuxserver/pipeline-triggers][pipelineurl] to perform basic continuous integration on the software being built.

## Usage

The container can be run locally, but it is meant to be integrated into the LinuxServer build process:

```
sudo docker run --rm -i \
-v /var/run/docker.sock:/var/run/docker.sock \
-e IMAGE="linuxserver/<dockerimage>" \
-e DELAY_START=<time in seconds> \
-e TAGS="<single tag or array seperated by |>" \
-e META_TAG=<manifest main dockerhub tag> \
-e PORT=<port web application listens on internal docker port> \
-e SSL=<true/false> \
-e BASE=<alpine or debian based distro> \
-e SECRET_KEY=<Digital Ocean spaces secret> \
-e ACCESS_KEY=<Digital Ocean spaces key> \
-e DOCKER_ENV="<optional, Array of env vars seperated by | IE test=test|test2=test2 or single var>" \
-e WEB_AUTH="<optional, format user:passord>" \
-e WEB_PATH="<optional, format /yourpath>" \
-t linuxserver/ci:latest \
python /ci/ci.py
```
