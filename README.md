### Projet afin de tester les networks policy


### Option 1 : Autoriser seulement une adresse Ip (celle de clover) + Alex ne peut pas communiquer avec Sam (par vraiment pratique si on l’expose ou si on redémarre notre argocd)

kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: network-policy-alex
spec:
  podSelector:
    matchLabels:
      project: namespace-c
  policyTypes:
    - Egress
  ingress:
  - from:
      - ipBlock:
          cidr: <adresse IP clover>/32       
  egress:
  - to:
    - ipBlock:
        cidr: <adresse IP de sam>/32


### Option 2 : refuser tout traffic
ingress: []


### Option 3 : autoriser seulement clover - utilisation du label 
kind: NetworkPolicy
apiVersion: networking.k8s.io/v1
metadata:
  name: network-policy-alex
spec:
  podSelector:
    matchLabels:
      app: alex
  ingress:
  - from:
      - podSelector:
          matchLabels:
            app: clover



### Option 6 : Accéder que d'un certain port (celui de sam2 dans namespace-b)
  ingress:
  - ports:
    - port: 8000