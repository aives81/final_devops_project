FROM golang:1.23 AS build

WORKDIR /app
COPY . .

RUN go build
RUN mkdir /bin/app
RUN mv vote-api /bin/app

FROM alpine:3.21
COPY --from=build /bin/app /bin/app

ARG PG_PASSWORD

ENV PG_URL="postgresql://neondb_owner:${PG_PASSWORD}@ep-hidden-mountain-a53rwzo1.us-east-2.aws.neon.tech/neondb?sslmode=require"
EXPOSE 8080
CMD ["/bin/app/vote-api"]