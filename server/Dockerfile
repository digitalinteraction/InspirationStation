FROM python:3.11-alpine

RUN mkdir -p /app \
  && apk add --no-cache tini postgresql-dev \
  && adduser -D python \
  && chown -R python:python /app

USER python
WORKDIR /app

COPY --chown=python:python requirements.txt /app/requirements.txt

RUN pip install --no-cache-dir --upgrade -r requirements.txt

COPY --chown=python:python . /app/

ENTRYPOINT ["tini", "--", "python", "inspire.py"]