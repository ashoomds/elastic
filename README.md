# elastic
tutorial for standing up elastic stack 

https://medium.com/@d3rwan/an-elk-stack-from-scratch-with-docker-58551616a2da


# clone repo & build images
git clone https://github.com/d3rwan/docker_elk_stack
cd docker_elk_stack
docker-compose build
# run (daemon)
docker-compose up -d
# show logs
docker-compose logs

After startup, you should be able to access Kibana (port 5601).

Then, we will deploy a basic example web app (NGinx serving HTML + Filebeat agent to send log in our stack)

# build image
docker build ./webapp -t dockerelkstack_webapp
# run (daemon)
docker run --network docker_elk_stack_logging --link redis:redis -p 80:80 -d --name webapp dockerelkstack_webapp

# show logs
docker logs webapp

what does docker link do and it's explaination --> 
https://docs.docker.com/network/links/#communication-across-links


##LOADING DATA IN ELASTIC
https://www.elastic.co/guide/en/kibana/current/tutorial-load-dataset.html
https://www.elastic.co/guide/en/kibana/current/tutorial-discovering.html
https://www.elastic.co/guide/en/kibana/current/tutorial-visualizing.html
https://www.elastic.co/guide/en/kibana/current/_pie_chart.html
https://www.elastic.co/guide/en/kibana/current/_bar_chart.html
https://www.elastic.co/guide/en/kibana/current/_coordinate_map.html
https://www.elastic.co/guide/en/kibana/current/_markdown.html
