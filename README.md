# desafio-de-projetos
Desafio de projetos git/github

#!/bin/bash

# Excluindo diretórios, arquivos, grupos e usuários criados anteriormente (se existirem)
echo "Excluindo diretórios, arquivos, grupos e usuários criados anteriormente (se existirem)..."
sudo rm -rf /publico /adm /ven /sec
sudo groupdel grp_adm grp_ven grp_sec
sudo userdel carlos maria joao debora sebastiana roberto josefina amanda rogerio

# Criando diretórios
echo "Criando diretórios..."
sudo mkdir /publico
sudo mkdir /adm
sudo mkdir /ven
sudo mkdir /sec

# Criando grupos
echo "Criando grupos..."
sudo groupadd grp_adm
sudo groupadd grp_ven
sudo groupadd grp_sec

# Definindo proprietário e permissões dos diretórios
echo "Definindo proprietário e permissões dos diretórios..."
sudo chown root:root /publico /adm /ven /sec
sudo chmod 755 /publico /adm /ven /sec

# Atribuindo permissões aos grupos
echo "Atribuindo permissões aos grupos..."
sudo chgrp grp_adm /adm
sudo chgrp grp_ven /ven
sudo chgrp grp_sec /sec
sudo chmod 770 /adm /ven /sec

# Criando usuários e adicionando aos grupos correspondentes
echo "Criando usuários e adicionando aos grupos correspondentes..."
sudo useradd -m -G grp_adm carlos
sudo useradd -m -G grp_adm maria
sudo useradd -m -G grp_adm joao
sudo useradd -m -G grp_ven debora
sudo useradd -m -G grp_ven sebastiana
sudo useradd -m -G grp_ven roberto
sudo useradd -m -G grp_sec josefina
sudo useradd -m -G grp_sec amanda
sudo useradd -m -G grp_sec rogerio

# Definindo permissões específicas
echo "Definindo permissões específicas..."
sudo chown root:grp_adm /adm
sudo chown root:grp_ven /ven
sudo chown root:grp_sec /sec
sudo chmod 770 /adm /ven /sec

# Atribuindo permissões totais dentro do diretório /publico para todos os usuários
echo "Atribuindo permissões totais dentro do diretório /publico para todos os usuários..."
sudo chmod 777 /publico

echo "Script concluído com sucesso!"

