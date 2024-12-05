### Projet afin de tester les networks policy

### Option 1 : autoriser seulement clover - utilisation du label 
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



### Option 2 : Alex ne peut pas communiquer avec Sam (par vraiment pratique si on l’expose ou si on redémarre notre argocd)
policyTypes:
  - Egress
  egress:
  - to:
    - ipBlock:
        cidr: <adresseIP pod de sam>/32


### Option 3 : refuser tout traffic
ingress: []


### Option 4


### Option 6 : Accéder que d'un certain port (celui de sam2 dans namespace-b)
  ingress:
  - ports:
    - port: 8000