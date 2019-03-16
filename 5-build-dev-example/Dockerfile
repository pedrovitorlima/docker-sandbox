FROM python:3.6
LABEL mantainer 'Pedro Rodrigues'

RUN useradd www && \
    mkdir /app && \
    mkdir /log && \
    chown www /log

USER www
VOLUME /lg
WORKDIR /app
EXPOSE 8000

ENTRYPOINT ["/usr/local/bin/python"]
CMD ["run.py"]

#ps:. run this command inside 5-build-dev-example directory
#>>docker image build -t 5-build-dev-example .
#>>docker container run -it -v $(pwd):/app -p 80:8000 --name python-server 5-build-dev-example