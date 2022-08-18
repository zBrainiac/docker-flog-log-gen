docker buildx build --platform linux/amd64,linux/arm64 -f dockerfile-multiarch-log-gen --tag brainiac/multiarch-log-gen:0.1.1 --push .




docker-compose down &&
docker rm -f $(docker ps -a -q) &&
docker volume rm $(docker volume ls -q)



docker run --add-host kafka:127.0.0.1 -it brainiac/multiarch-log-gen:0.1.1 flog -f rfc5424 -l -t log -o /var/log/generated.log
tail -f /var/log/generated.log | kcat -b kafka:9092 -t syslog



local test:
tail -f  /private/var/log/com.apple.xpc.launchd/launchd.log | kcat -b kafka:9092 -t syslog

****

#    command:
#      - flog -f rfc5424 -l -t log -o /var/log/generated.log



docker run brainiac/multiarch-log-gen:0.1.0
docker run -it flog -f rfc3164 -l brainiac/multiarch-log-gen:0.1.0
docker run -it brainiac/multiarch-log-gen:0.1.0 flog -f rfc3164 -l



rfc5424:
<135>2 2022-08-06T11:50:42.047Z districtmindshare.org et 9091 ID39 - You can't input the alarm without parsing the redundant ADP system!

rfc3164
--debug --logdir /var/log/apache2/access_log --server localhost:9092 --topic apache --client "client_id"