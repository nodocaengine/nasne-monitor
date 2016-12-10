#!/bin/zsh

titles=$(curl -X GET 'http://192.168.210.25:64220/recorded/titleListGet?searchCriteria=0&filter=0&startingIndex=0&requestedCount=0&sortCriteria=0&withDescriptionLong=0&withUserData=0' | jq '.numberReturned')
usage=$(curl -X GET 'http://192.168.210.25:64210/status/HDDInfoGet?id=0' | jq '.HDD.usedVolumeSize * 100 / .HDD.totalVolumeSize')

obj=$(jq -n --arg titles $titles --arg usage $usage '{titles: $titles | tonumber, usage: $usage | tonumber, timestamp: now | todate}')

curl -X POST 'http://localhost:9200/nasne/usage' -d $obj

