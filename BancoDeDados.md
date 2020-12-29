# ProjetoPTI-Faculdade
Esse Projeto foi estipulado pela faculdade pra entrega de final de semestre , nele tem banco de dados, modelagem em UML e Python


create database fazendaBd
default character set utf8
default collate utf8_general_ci;


create table fazenda (
nome varchar(20),
localizacao varchar(30),
metrosQuadrados decimal (5,3)
) default charset = utf8;

insert into fazenda
(nome,localizacao,metrosquadrados)
values
('Fazentech','mato grosso','14.520');
select * from fazenda;

create table funcionarios (
id int not null auto_increment,
nome varchar(30) not null,
cpf decimal (11,2),
datanasc date,
funcao varchar(20),
primary key (id)
) default charset = utf8;

desc funcionarios;

insert into funcionarios
(id,nome,cpf,datanasc,funcao)
values
('João','43989567804','1992-11-02','Agricultor'),
('Cleberson','43989790809','1987-06-06','Pecuarista');

use fazendaBd;

select * from funcionarios;

create table agricultor (
pesquisaoferta varchar(500),
rela_compra_equipamentos varchar(500),
rela_controle_solo varchar(500),
rela_qualidade_plantio varchar(500),
rela_qualidade_colheita varchar(500)
) default charset utf8;

insert into agricultor
(pesquisaoferta,rela_compra_equipamentos,rela_controle_solo,rela_qualidade_plantio,rela_qualidade_colheita)
values
('Realizando a pesquisa,podemos ver que é melhor plantar soja este ano','compramos 2 tratores','O solo está pronto pra receber as sementes',
'a qualidade do plantio foi excelente','A colheita foi muito boa');

select * from agricultor;

create table pecuarista (
obter_custos_producao decimal(6,3),
gerar_relatorio_saude varchar(500),
controle_qualidade_agua varchar(500),
graficos_producao varchar(500),
controle_de_custo varchar(500)
) default charset utf8;

desc pecuarista;

insert into pecuarista
(obter_custos_producao, gerar_relatorio_saude, controle_qualidade_agua, graficos_producao, controle_de_custo)
values
(150.000,'os animais estão bem nutridos e todos vacinados','A agua está com otima qualidade de purificação',
'os graficos segue no anexo','na safra no inicio do ano gastamos 100 mil, no meio gastamos 150 mil,fora alguns equipamentos que tivemos que comprar que ficou mais 300 mil');
select * from pecuarista;
desc pecuarista;

create table animal (
ID_A int not null auto_increment,
especie varchar(20),
peso decimal(4,1),
primary key (ID_A)
) default charset utf8;

insert into animal
(especie,peso)
values
('Boi','1100'),
('Vaca','900');


select * from animal;

describe animal;

create table ordenha (
ID_O int not null auto_increment,
data_ordenha date,
temperatura_leite varchar(5),
litros_obtidos decimal (3,2),
especie_animal varchar(20),
primary key (ID_O)
) default charset utf8;



insert into ordenha 
(data_ordenha,temperatura_leite,litros_obtidos,especie_animal)
values
('2020-10-23','4ºC','10,0','Vaca'),
('2020-10-18','4ºC','09,0','Vaca');
select * from ordenha;





create table plantio (
especie varchar (10),
data_plantio date,
obter_relatorio_plantio varchar (500)
) default charset utf8;

desc plantio;

insert into plantio 
(especie,data_plantio,obter_relatorio_plantio)
values
('Soja','2020-06-02','Relando que o plantio se saiu muito bem, as sementes estavam otimas');
select * from plantio;

create table colheita (
especie varchar(20),
data_ultima_colheita date,
infor_colheita varchar (300)
) default charset utf8;

insert into colheita
(especie,data_ultima_colheita,infor_colheita)
values
('Soja','2020-01-01','Foi feita a colheita com otimos resultados etc');

select * from colheita;


alter table animal
add column IDordenha int;

desc animal;

desc ordenha;


alter table animal
add foreign key (IDordenha)
references ordenha(ID_O);

select * from animal;
select * from ordenha;
update animal set ordenha = '2' where ID_A = '1';
update animal set ordenha = '1'where ID_A = '2';
