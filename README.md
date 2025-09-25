# edge-dns-anycast

Service d’annuaire Internet (DNS) **opéré comme un service réseau** : une **même IP** servie depuis **plusieurs lieux** (anycast), **chiffrée** (DoH/DoT), **résiliente** aux pannes/attaques, **observable** et **déployée** de façon reproductible.

## But du projet
- **Disponibilité** : éviter le point unique de panne d’un “serveur DNS unique”. La même IP est annoncée depuis plusieurs PoP ; si l’un tombe, les autres répondent.
- **Proximité/latence** : diriger automatiquement chaque client vers le **PoP le plus proche**.
- **Confidentialité/Intégrité** : transporter les requêtes/réponses **chiffrées** (DoH/DoT) et **validées** (DNSSEC côté données).
- **Résilience basique aux DDoS** : filtrage/limitations en bordure pour préserver les ressources légitimes.
- **Maîtrise opérationnelle** : métriques, logs, tableaux de bord et **configurations versionnées** (GitOps) pour des changements tracés et réversibles.

## Ce que le projet **démontre**
- Un **résolveur** (cherche pour l’utilisateur) et un **autoritatif** (répond pour tes zones) servis derrière une **façade chiffrée**.
- Un **routage** qui fait qu’**une seule IP** existe en **plusieurs lieux** et reste joignable malgré une panne locale.
- Une **exploitation** mesurable (latence, erreurs, QPS, état des sessions) et **industrialisée** (CI/CD de configs).

## Hors périmètre
- Matériel anti-DDoS opérateur (scrubbing center).
- Anycast public BGP “Internet” complet (démonstration en lab/overlay suffisante).
- Portail applicatif non-DNS.

## Pourquoi ce nom : `edge-dns-anycast`
- **edge** : le service vit **au bord du réseau** (PoP/edge), au plus près des clients.
- **dns** : c’est un **annuaire nom → adresse** (résolveur + autoritatif).
- **anycast** : **une IP unique, plusieurs sites** qui la servent, avec bascule automatique.
