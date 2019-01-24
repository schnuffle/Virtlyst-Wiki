
To be able to build a debian package the created artefacts have to be extracted from the docker image. I create a build_dep.sh which does exactly that.

So creating a debian package consists of four steps:
- Build the docker image
- Extract artefacts into build folder virtlyst-deb
- Cleanup unnecessary files
- Create .deb package

For the moment there's still a problem that some libs aren't located and LD_LIBRARY_PATH has to be set. 
A solution is to create a file /etc/ld.so.conf.d/virtlyst.conf adding the lib paths.
