# Multistage build
# Step 1
FROM golang:alpine AS builder

RUN apk update && apk add --no-cache git

COPY helloworld.go $GOPATH/src/hello/
WORKDIR $GOPATH/src/hello/

RUN go get -d -v
RUN CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build -o /go/bin/hello

# Step 2
FROM scratch
COPY --from=builder /go/bin/hello /go/bin/hello
ENTRYPOINT ["/go/bin/hello"]
