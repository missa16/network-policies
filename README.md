### Projet afin de tester les networks policy

### Option 1 : autoriser seulement clover - utilisation du label 
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

### Option 3 : Accéder que d'un certain port
  ingress:
  - ports:
    - port: 82

### Option 4 :  que d'un certain namespace
policyTypes:
  - Ingress
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          project: my-namespace

### Option 5 : refuser tout traffic
ingress: []