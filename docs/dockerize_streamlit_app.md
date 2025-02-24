## Example DOCKERFILE
```dockerfile
# app/Dockerfile

FROM python:3.9-slim

WORKDIR /report_v2

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    software-properties-common \
    git \
    && rm -rf /var/lib/apt/lists/*

COPY . .

RUN pip3 install -r requirements.txt
RUN pip3 install -U kaleido

EXPOSE 8080

HEALTHCHECK CMD curl --fail http://localhost:8080/_stcore/health

ENTRYPOINT ["streamlit", "run", "single_v1p5.py", "--server.port=8080", "--server.address=0.0.0.0"]
```


## ON TERMINAL
```bash
sudo docker build -t [IMAGE_NAME] .

sudo docker run -p 8080:8080 [IMAGE_NAME]
```

## to delete (if need be): 
```bash
sudo docker rmi -f [IMAGE_NAME]:latest
```


## Access the docker image to do Linux stuff inside

`docker exec -it flask_app4 /bin/bash`

## Save docker image as .tar

`docker save busybox > busybox.tar`
