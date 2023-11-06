FROM registry.access.redhat.com/ubi9/python-39:1-117.1684741281

WORKDIR /projects

COPY . .

RUN pip install -r requirements.txt; 

CMD [ "python", "./app.py" ]
