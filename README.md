# single_node_rancher_installation
single_node_rancher_installation

docker run -d --restart=unless-stopped --privileged --name rancher -p 80:80 -p 443:443 --network host -v /opt/rancher:/var/lib/rancher -v /home/secrets:/etc/rancher/k3s -v -v /home/secrets/registries.yaml:/etc/rancher/k3s/registries.yaml docker.registry.server/rancher/rancher:v2.5.9

NOTE: In /home/secrets all secrets as well as registries.yaml should present

registries.yaml 


