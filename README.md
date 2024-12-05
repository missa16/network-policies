### Projet afin de tester les networks policy

### Option 1 : autoriser seulement clover - utilisation du label 
ingress:
  - from:
      - podSelector:
          matchLabels:
            app: clover


