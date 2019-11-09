# Multistage build
# Step 1
FROM golang:alpine AS builder

RUN apk update --no-cache

ADD helloworld/ $GOPATH/src/hello/
WORKDIR $GOPATH/src/hello/

RUN go get -d -v
RUN go build -o /go/bin/hello

# Step 2
FROM scratch
COPY --from=builder /go/bin/hello /go/bin/hello
ENTRYPOINT ["/go/bin/hello"]
