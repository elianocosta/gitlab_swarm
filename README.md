
# Documentação gitlab swarm docker

# Aumentando o numero de arquivos abertos pelo sistema
sysctl -w fs.file-max=806154

echo "fs.file-max = 806154
" >> /etc/sysctl.conf

ulimit -n 806154

echo "#### TUNNING DE LIMITS DE KERNEL #####
root soft nofile 806154
root hard nofile 806154
* soft nofile 806154
* hard nofile 806154
" >> /etc/security/limits.conf

cd /var/data
mkdir gitlab
cd gitlab
mkdir -p {postgresql,redis,gitlab}

## Para criação de usuário
docker exec -it container gitlab-rails console

user = User.new
user.name = 'usuario'
user.username = 'usuario'
user.email = 'usuario@example.net'
user.password = '442b7dbcc79751a6077a1a63f0749815'
user.admin = true
user.save!