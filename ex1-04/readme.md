# Exercise 1.4: Missing dependencies

```docker run -it --rm ubuntu sh -c 'apt-get update; apt-get install curl -y; read -r -p "Input website: " website; echo "Searching... " $website; sleep 1; curl http://$website;'```
