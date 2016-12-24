# Dockerfile for creating a deployable container for bet-scraper

# Install base stuff
FROM python:2
ENV REFRESHED_AT 2016-12-23
MAINTAINER Jonathan Poltak Samosir <jonathan.samosir@gmail.com>

# Set work directory for all build commands
WORKDIR /bet_scraper

# Copy over deps for pip
COPY requirements.txt /bet_scraper

# Install all pip deps on image
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN pip install -U cffi

RUN (>&2 echo "Make sure to schedule jobs with cron; this container does nothing")
