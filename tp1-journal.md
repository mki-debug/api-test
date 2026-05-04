# TP1 - Journal de déploiement

## Informations
- Application : todo-api
- Serveur : Ubuntu 22.04 LTS
- URL GitHub : https://github.com/mki-debug/api-test

## Étapes réalisées
- Mise à jour du système
- Configuration UFW (22, 80, 443)
- Création utilisateur todoapp
- Installation Node.js 20 LTS
- Déploiement application depuis GitHub
- Création service systemd
- Configuration Nginx reverse proxy
- Tests fonctionnels validés

## Runbook

### Redémarrer le service
sudo systemctl restart todo-api

### Voir les 50 derniers logs
sudo journalctl -u todo-api -n 50

### Déployer une nouvelle version
cd /opt/todo-api && sudo -u todoapp git pull && sudo systemctl restart todo-api

### Rollback
cd /opt/todo-api && sudo -u todoapp git checkout <commit-id> && sudo systemctl restart todo-api

### Régénérer le JWT_SECRET
sudo nano /opt/todo-api/.env
sudo systemctl restart todo-api
# Attention : tous les utilisateurs connectés devront se reconnecter

### Nginx ne démarre plus
sudo nginx -t
sudo systemctl start nginx
