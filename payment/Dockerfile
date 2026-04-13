FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
COPY ./requirements.txt .
COPY *.py .
COPY payment.ini .
RUN apk add --no-cache build-base linux-headers python3-dev
RUN pip3 install --prefix /install -r requirements.txt

FROM python:3.9.25-alpine3.22
WORKDIR /app
COPY --from=builder /install /usr/local
EXPOSE 8080
RUN addgroup -S roboshop && adduser -SG roboshop roboshop
USER roboshop
CMD ["payment.ini" ]
ENTRYPOINT [ "uwsgi", "--ini"]


# FROM python:3.9
# EXPOSE 8080
# WORKDIR /app
# COPY ./requirements.txt .
# COPY *.py .
# COPY payment.ini .
# RUN pip3 install -r requirements.txt
# CMD [ "uwsgi", "--ini", "payment.ini" ]
