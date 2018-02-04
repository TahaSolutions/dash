#docker build -t dash3 .

FROM ubuntu:xenial

RUN apt-get update && \
    apt-get install -y software-properties-common build-essential python3-pip  nano && \
    apt-get clean

COPY . .

RUN pip3 install --upgrade pip
RUN pip3 install -r requirements.txt
EXPOSE 8050

#CMD ["bash"]
CMD gunicorn -w 10 -b 0.0.0.0:8050 -t 100000 --max-requests 20 app:server

CMD ["python3", "app.py"]

#docker run -it --name dash3 -p 8050:8050 dash3
