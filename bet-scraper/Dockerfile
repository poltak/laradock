# Dockerfile for creating a deployable container for bet-scraper

# Install base stuff
FROM python:2
ENV REFRESHED_AT 2016-07-01
MAINTAINER Jonathan Poltak Samosir <jonathan.samosir@gmail.com>

# Set work directory for all build commands
WORKDIR /bet_scraper

# Install cron
RUN apt-get update
RUN apt-get -qqy install cron

# Copy over cron and anacron configs
COPY crontab /etc/cron.d/bet-scraper
RUN chmod 0644 /etc/cron.d/bet-scraper

# Copy over deps for pip
COPY requirements.txt /bet_scraper

# Install all pip deps on image
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN pip install -U cffi

# Add log file
RUN touch /var/log/cron.log

# Forever watch the log file, making it the container's log
CMD ["cron", "&&", "tail", "-f", "/var/log/cron.log"]

