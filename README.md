ssh root@165.22.45.215
sudo ufw allow port

###used ports
3102 sql closed
80/8080 open
547 email

mysql -u root -p // loga my no server
service mysqld stop/start
sudo service mysql restart
sudo update-rc.d /etc/init.d/nameofscript.sh defaults
cd /root/app/checkStart.sh

OneShot. For example, create /etc/systemd/system/foo.service containing:

[Unit]
Description=Job that runs your user script

[Service]
ExecStart=sh /root/app/checkStart.sh
Type=oneshot
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target

Then run:

sudo systemctl daemon-reload
sudo systemctl enable stall.service

//////////////////////////////////////////////////////////////////////
CREATE USER 'app'@'%' IDENTIFIED BY 'AppPassWd789612';
GRANT SELECT,DELETE,EXECUTE,INSERT,UPDATE ON *.* TO 'app'@'%';


flush privileges;


/////////////////////////////////////////////////////////////////
CREATE DATABASE PaSolucoes;
USE PaSolucoes;
SELECT MD5('w3resource'); 

create table funcionarios(
id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(50) NOT NULL,
login VARCHAR(20) NOT NULL,
senha VARCHAR(200) NOT NULL,
admin_user bool default 0 ,
data_criacao DATETIME NOT NULL DEFAULT NOW(),
data_modificacao DATETIME NOT NULL DEFAULT NOW()
);

create table clientes(
id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(50) NOT NULL,
CNPJ INT NOT NULL,
Endereco VARCHAR(200) NOT NULL,
email VARCHAR(100) NOT NULL,
data_criacao DATETIME NOT NULL DEFAULT NOW(),
data_modificacao DATETIME NOT NULL DEFAULT NOW()
);

create table atendimentos(
id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
duracao INT NOT NULL DEFAULT 0,
data_atendimento DATETIME NOT NULL DEFAULT NOW(),
cliente_id INT NOT NULL,
funcionario_id INT NOT NULL,
FOREIGN KEY (funcionario_id) REFERENCES funcionarios(id),
FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);