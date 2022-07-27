# Usando-sql.
Comandos Sql
CREATE DATABASE escola;
USE escola;
CREATE TABLE tab_alunos(
    id_aluno INT NOT NULL PRIMARY KEY IDENTITY,
    nome  VARCHAR(50) NOT NULL,
    email VARCHAR(50) NOT NULL,
    fone  VARCHAR(15) NOT NULL,
    foto  VARCHAR(50) NOT NULL
);

CREATE TABLE tab_professores(
    id_professor INT NOT NULL PRIMARY KEY IDENTITY,
    nome VARCHAR(50) NOT NULL,
    email VARCHAR(50)NOT NULL,
	fone varchar(15)NOT NULL,
	foto varchar(50)NOT NULL,
	salario DECIMAL(10,2) NOT NULL
);
Create table tab_salas(
id_sala int not null primary key identity,
numero int not null, 
capacidade int not null,
equipamento varchar(3) not null
)
create table tab_turmas(
id_turma int not null primary key identity,
nome varchar(30) not null,
id_aluno int not null,
id_professor int not null,
id_sala int not null,
/* chave estrangeira*/
constraint fk_id_aluno foreign key(id_aluno)
references tab_alunos(id_aluno),

constraint fk_id_professor foreign key(id_professor)
references tab_professores(id_professor),

constraint fk_id_salas foreign key(id_sala)
references tab_salas(id_sala)
);

