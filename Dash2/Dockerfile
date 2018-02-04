#docker build -t dash2 .

FROM ubuntu:xenial

RUN apt-get update && \
    apt-get -y install  && \
    apt-get install -y software-properties-common build-essential python-pip  nano && \
    apt-get clean

COPY . .

RUN pip install --upgrade pip
RUN pip install -r requirements.txt
EXPOSE 8050

#CMD ["bash"]
CMD gunicorn -w 10 -b 0.0.0.0:8050 -t 100000 --max-requests 20 app:server

CMD ["python", "app.py"]

#docker run -it --name dash2 -p 8050:8050 dash2