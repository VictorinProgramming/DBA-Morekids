CREATE DATABASE db_morekids;

USE db_morekids;

CREATE TABLE IF NOT EXISTS tb_usuario(
    id BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    nome VARCHAR (50) NOT NULL,
    email VARCHAR (50) NOT NULL UNIQUE,
    login VARCHAR(25) NOT NULL UNIQUE,
    senha VARCHAR (60) NOT NULL,
    perfil VARCHAR (25) NOT NULL DEFAULT 'PADRAO',
    data_hora_criacao DATETIME DEFAULT CURRENT_TIMESTAMP,
    ultimo_login DATETIME DEFAULT '0001-01-01 00:00:00'
);

CREATE TABLE IF NOT EXISTS tb_tipo_produto(
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL UNIQUE,
    descricao VARCHAR(255)
);

CREATE TABLE IF NOT EXISTS tb_produto(
    id BIGINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL UNIQUE,
    descricao VARCHAR(200) NOT NULL,
    preco DECIMAL (10, 2) NOT NULL,
    quantidade INT NOT NULL,
    tipo_produto_id INT NOT NULL,
    usuario_id BIGINT NOT NULL,
    data_hora_criacao DATETIME DEFAULT '0001-01-01 00:00:00',
    CONSTRAINT fk_produto_tipo_produto FOREIGN KEY(tipo_produto_id) REFERENCES tb_tipo_produto (id),
    CONSTRAINT fk_produto_usuario FOREIGN KEY (usuario_id) REFERENCES tb_usuario (id)
);

CREATE TABLE IF NOT EXISTS tb_clientes(
    id BIGINT PRIMARY KEY AUTO_INCREMENT NOT NULL,
    nome VARCHAR(50) NOT NULL UNIQUE,
    telefone VARCHAR(12) NOT NULL,
    genero VARCHAR(9) NOT NULL
);

CREATE TABLE IF NOT EXISTS tb_vendas(
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    total_venda DECIMAL (10,2) NOT NULL,
    valor_pago DECIMAL (10,2) NOT NULL,
    troco DECIMAL (10,2) NOT NULL,
    desconto DECIMAL (10,2) NOT NULL,
    cliente_id BIGINT,
    usuario_id BIGINT NOT NULL,
    data_hora_criacao DATETIME DEFAULT CURRENT_TIMESTAMP,
    ultima_atualizacao DATETIME DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT fk_venda_cliente FOREIGN KEY (cliente_id) REFERENCES tb_clientes (id),
    CONSTRAINT fk_venda_usuario FOREIGN KEY (usuario_id) REFERENCES tb_usuario (id)
);

CREATE TABLE IF NOT EXISTS tb_venda_item (
    vendas_id BIGINT NOT NULL,
    produto_id BIGINT NOT NULL,
    quantidade INT NOT NULL,
    total DECIMAL (10,2) NOT NULL,
    desconto DECIMAL (10,2) NOT NULL,
    CONSTRAINT fk_venda_item_vendas FOREIGN KEY (vendas_id) REFERENCES tb_vendas (id),
    CONSTRAINT fk_venda_item_produto FOREIGN KEY (produto_id) REFERENCES tb_produto(id)
);


DROP TABLE tb_usuario;
DROP TABLE tb_tipo_produto;
DROP TABLE tb_produto;
DROP TABLE tb_clientes;
DROP TABLE tb_vendas; 
DROP TABLE tb_venda_item;

select* from tb_usuario;
select* from tb_tipo_produto;
select* from tb_produto;
select* from tb_clientes;
select*from tb_vendas;
select*from tb_venda_item;

describe tb_usuario;
describe tb_tipo_produto;
describe tb_produto;
describe tb_clientes;
describe tb_vendas;
describe tb_venda_item;

update db_morekids.tb_usuario set nome = ''  where id_usuario = 1;
update  set nome = ''  where  = ;
update  set nome = ''  where  = ;
update  set nome = ''  where  = ;
update  set nome = ''  where  = ;
update  set nome = ''  where  = ;

alter table tb_usuario add perfil varchar(20) not null after genero;
alter table  add  varchar() not null after ;
alter table  add  varchar() not null after ;
alter table  add  varchar() not null after ;
alter table  add  varchar() not null after ;
alter table  add  varchar() not null after ;

insert into tb_tipo_produto (nome, descricao) values ('Camiseta Gola O' , 'Verde');
insert into () values ();
insert into () values ();
insert into () values ();
insert into () values ();
insert into () values ();
