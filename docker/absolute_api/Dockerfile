FROM python:2.7
MAINTAINER Jesse Chahal "jesse@jessechahal.com"
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT ["python"]
CMD ["app.py"]