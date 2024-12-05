### Projet afin de tester les networks policy

### Option 1 : autoriser seulement clover - utilisation du label 
ingress:
  - from:
      - podSelector:
          matchLabels:
            app: clover

### Option 2 : Limiter le traffic par adresse IP (par vraiment pratique si on l’expose ou si on redémarre notre argocd)



### Option 3 : Accéder que d'un certain port
  ingress:
  - ports:
    - port: 82

### Option 4 :  que d'un certain namespace


### Option 5 : refuser tout traffic
ingress: []