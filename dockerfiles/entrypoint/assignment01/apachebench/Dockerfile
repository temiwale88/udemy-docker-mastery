FROM ubuntu:latest

# Avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install apache2-utils which provides the `ab` (ApacheBench) tool.
# Update the apt cache, install, then clean apt lists to keep the image small.
RUN apt-get update \
	&& apt-get install -y --no-install-recommends apache2-utils \
	&& rm -rf /var/lib/apt/lists/*

# Make `ab` the container entrypoint; users add the target URL as arguments.
ENTRYPOINT ["ab"]

# Provide sensible defaults: 10 requests, concurrency 2, and an example URL.
# Users can override any of these by supplying different args to `docker run`.
CMD ["-n","10","-c","2","https://www.bretfisher.com/"]


