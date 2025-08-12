FROM node:18.12.1-bullseye-slim
FROM python:3.12.0-slim-bookworm
RUN npm install -g npm@9.1.3
ENV PYTHONBUFFERED 1
ENV PYTHONWRITEBYTECODE 1

ENV APP=/app
ADD package.json .
ADD app.js .
ADD review.js .
ADD dealership.js .
ADD data/dealerships.json .
ADD data/reviews.json .
WORKDIR $APP
COPY requirements.txt $APP
COPY . $APP
RUN npm install
RUN pip3 install -r requirements.txt
EXPOSE 3030
ENTRYPOINT ["/bin/bash","/app/entrypoint.sh"]

CMD [ "node", "app.js","gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi" ]
