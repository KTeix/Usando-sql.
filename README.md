Criando tabela SQL


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

Insert into tab_alunos(nome, email, fone, foto)
values
('João da silva', 'Joao@gmail.com', '(11) 91111-1111', 'joao.png'),
('Maria Machadão', 'mmachado@outlook.com', '(11) 92222-2222', 'maria.png'),
('Charles', 'charles@uoo.com.br', '(11 93333-3333', 'charles.png'),
('Manoel', 'manoel@gmail.com', '(11) 94444-4444', 'manoel.jpeg'),
('Danilo', 'danilo@bol.com.br', '(11) 9555-5555', 'danilo.jpeg'),
('Fatima', 'fatima@gmail.com.br', '(11) 96666-6666', 'fatima.jpeg'),
('Simone', 'Simone@gmail.com.br', '(11) 97777-7777', 'Simone.jpeg'),
('Tomas', 'tomas@gmail.com.br', '(11) 98888-8888', 'tomas.jpeg'),
('tereza', 'tereza@uol.com.br', '(11) 9999-9999', 'tereza.jpeg'),
('beto', 'beto@gmail.com.br', '(11)91010-1010', 'beto.jpeg');

insert into tab_professores(nome, email, fone, foto, salario)
Values
('Fabio', 'fabioc@sp.senac.br', '(11) 91234-5678', 'fabio.jpeg', 1500.00),
('Rafael', 'rafael@sp.senac.br','(11) 99876-5432', 'Rafael.jpeg', 2500.00),
('Alexandre', 'Alexandre@sp.senac.br', '(11) 99632-5874', 'alex.png', 2500.00),
('Anésio', 'anesio@sp.senac.br', '(11) 97412-3658', 'anesio.jpeg', 2380.00);

insert into tab_salas (numero, capacidade, equipamento) values
(2,12, 'win'),
(24,27, 'win'),
(30,20, 'win'),
(32,20, 'mac');

insert into tab_turmas(nome, id_aluno, id_professor, id_sala)
values
('sql', 1, 1, 1),
('sql', 2, 1, 1),
('sql', 3, 1, 1),

('c#', 4, 2,2),
('c#', 5, 2,2),
('c#', 6, 2,2),

('redes', 7, 3, 3),
('redes', 8, 3, 3),

('excel', 9,4 ,4),
('excel', 10,4 ,4);


select * from tab_alunos
select * from tab_professores
select * from tab_salas
select * from tab_turmas

select nome, email from tab_alunos
Where email like '@gmail.com';


select nome, salario from tab_professores;

-- mostrar nome dos professores e salarios maiores que 2400

select nome, salario from tab_professores
where salario > 2400

select numero, capacidade, equipamento from tab_salas
where equipamento='win';

select numero, capacidade, equipamento from tab_salas
where equipamento like 'win';

SELECT tab_alunos.id_aluno, tab_alunos.nome, tab_turmas.nome
FROM tab_alunos
INNER JOIN tab_turmas
ON tab_alunos.id_aluno = tab_turmas.id_aluno
where tab_turmas.nome like 'sql';

SELECT tab_professores.nome as 'nome professor', tab_alunos.nome as 'nome aluno', tab_turmas.nome as 'Curso'
FROM tab_alunos
INNER JOIN tab_turmas
ON tab_alunos.id_aluno = tab_turmas.id_aluno
INNER JOIN tab_professores
ON tab_turmas.id_professor = tab_professores.id_professor
where tab_turmas.nome like 'redes'

SELECT tab_professores.nome as 'nome professor', tab_alunos.nome as 'nome aluno', tab_turmas.nome as 'Curso'
FROM tab_alunos
INNER JOIN tab_turmas
ON tab_alunos.id_aluno = tab_turmas.id_aluno
INNER JOIN tab_professores
ON tab_turmas.id_professor = tab_professores.id_professor
where tab_alunos.nome = 'nome' or tab_professores.nome = 'fabio'
