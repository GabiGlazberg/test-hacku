# test-hacku
1. jenkins master on ssh -i "candidate-test.pem" ec2-user@ec2-54-235-217-196.compute-1.amazonaws.com 
    1. run on port 11011
2. jenkis slave ssh -i "candidate-test.pem" ec2-user@ec2-54-235-181-217.compute-1.amazonaws.com
    1. open on port 22
    2. jenkins slave, if not connected, go to: Manage Jenkins -> Manage Nodes and Clouds -> test-slave -> run the secund commend to reconnect the server
3. jenkins file 
    1. repo https://github.com/GabiGlazberg/test-hacku
    2. agent as above
4. docker
    1. build nginx 
    2. change owner to file so nginx have access
5. nginx
    1. open connection localhost:80
    2. all / request go to /usr/share/nginx/html/
    3. autoindex to show the folders