from golang as build
WORKDIR /app
COPY app /app
RUN go build main.go
CMD ./main

from debian as prod
ENV TZ="Europe/Minsk"
WORKDIR /app
copy --from=build /app/main /app/main
CMD ./main
