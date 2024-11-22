# logstash-config-tester

## Description
Quickly bootstrap a docker container to test your logstash filters

## Configuration
The configuration file is located at `/pipeline/configuration.conf`.

The pipeline flow is:
> input > filters > output 

In this project, the input comes from `stdin` and goes to `stdout`. The only part to touch is the `filters` section. 

## Usage
Simply start this project using `docker-compose run logstash`. 
Then, you only need to paste your log line to see how it is parsed by your filters.

In one terminal run:
docker compose -f docker-compose.yml -p logstash-config-tester up

In a second terminal to test logstash is working:
echo "Hello world" | socat EXEC:"docker attach logstash-config-tester-logstash-1",pty STDIN
