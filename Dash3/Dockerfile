#docker build -t dash3 .

FROM ubuntu:xenial

RUN apt-get update && \
    apt-get -y install software-properties-common wget curl && \
    apt-add-repository 'deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main' && \
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
    apt-get update && \
    apt-get update  && \
    apt-get install -y build-essential python3-pip  && \
    apt-get install -y postgresql-9.4 && \
    curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
    apt-get install -y nodejs git nano && \
    apt-get clean

COPY . .

RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt
EXPOSE 8050

#CMD ["bash"]
CMD gunicorn -w 10 -b 0.0.0.0:8050 -t 100000 --max-requests 20 app:server

CMD ["python3", "app.py"]

#docker run -it --name dash3 -p 8050:8050 dash3