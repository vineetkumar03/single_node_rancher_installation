# single_node_rancher_installation
single_node_rancher_installation

docker run -d --restart=unless-stopped --privileged --name rancher -p 80:80 -p 443:443 --network host -v /opt/rancher:/var/lib/rancher -v /home/secrets:/etc/rancher/k3s -v -v /home/secrets/registries.yaml:/etc/rancher/k3s/registries.yaml docker.registry.server/rancher/rancher:v2.5.9

NOTE: In /home/secrets all secrets as well as registries.yaml should present

registries.yaml is as below

mirrors:
  docker.io:
    endpoint:
      - "https://docker.registry.server"
    rewrite:
      "^rancher/(.*)": "/rancher/$1"   ## Replace from any rancher.io nameserver to chub.cloud.gov.in/rancher  
      "^docker/(.*)": "/rancher/$1"    
      "^git/(.*)": "/rancher/$1"    
      "^k8s/(.*)": "/rancher/$1"    
configs:
  "Registry":
    auth:
      username: admin # this is the registry username
      password: *********
    tls:
      cert_file: /etc/rancher/k3s/fullchain.pem # path to the cert file used in the registry
      key_file: /etc/rancher/k3s/privkey.key  # path to the key file used in the regis
