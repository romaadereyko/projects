from openjdk as build
WORKDIR /app
COPY app /app
RUN javac Hello.java
#CMD javac Hello.java
#CMD /bin/sh
CMD java HelloWorld

from openjdk as prod
ENV TZ="Europe/Minsk"
WORKDIR /app
copy --from=build HelloWorld.class HelloWorld.class
CMD java HelloWorld
