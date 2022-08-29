from openjdk as build
WORKDIR /app
COPY app /app
RUN javac Calculator.java
CMD java Calculator

from openjdk as prod
ENV TZ="Europe/Minsk"
WORKDIR /app
COPY /app/Calculator /app/Calculator
CMD java Calculator
