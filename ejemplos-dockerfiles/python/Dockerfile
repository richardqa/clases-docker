FROM python:2.7
MAINTAINER Richard Quinto (richardqa@gmail.com)
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
RUN echo "Hello World" >> /opt/test.env
HEALTHCHECK CMD curl --fail http://localhost:5000/ || exit 1
ENTRYPOINT ["python"]
CMD ["app.py"]
