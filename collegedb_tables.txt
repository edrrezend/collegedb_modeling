CREATE TABLE departamentos (
    id_departamento INTEGER NOT NULL PRIMARY KEY,
    nome_departamento VARCHAR NOT NULL
);

CREATE TABLE professores (
    id_professor INTEGER NOT NULL PRIMARY KEY,
    id_departamento INTEGER NOT NULL,
    nome_professor VARCHAR NOT NULL,
    sobrenome_professor VARCHAR NOT NULL,
    status_professor TINYINT NOT NULL,
    FOREIGN KEY (id_departamento) REFERENCES departamentos(id_departamento)
);
CREATE TABLE disciplinas (
    id_disciplina INTEGER NOT NULL PRIMARY KEY,
    id_departamento INTEGER NOT NULL,
    nome_disciplina VARCHAR NOT NULL,
    carga_horaria INTEGER NOT NULL,
    descricao VARCHAR NULL,
    num_alunos INTEGER NOT NULL,
    FOREIGN KEY (id_departamento) REFERENCES departamentos(id_departamento)
);
CREATE TABLE professor_disciplina (
    id_professor INTEGER NOT NULL,
    id_disciplina INTEGER NOT NULL,
    PRIMARY KEY (id_professor, id_disciplina),
    FOREIGN KEY (id_professor) REFERENCES professores(id_professor),
    FOREIGN KEY (id_disciplina) REFERENCES disciplinas(id_disciplina)
);

CREATE TABLE cursos (
    id_curso INTEGER NOT NULL PRIMARY KEY,
    id_departamento INTEGER NOT NULL,
    nome_curso VARCHAR NOT NULL,
    FOREIGN KEY (id_departamento) REFERENCES departamentos(id_departamento)
);

CREATE TABLE depende (
    id_disciplina INTEGER NOT NULL,
    possui_id_disciplina INTEGER NOT NULL,
    FOREIGN KEY (id_disciplina) REFERENCES disciplinas(id_disciplina),
    FOREIGN KEY (possui_id_disciplina) REFERENCES disciplinas(id_disciplina)
);

CREATE TABLE curso_disciplina (
    id_curso INTEGER NOT NULL,
    id_disciplina INTEGER NOT NULL,
    PRIMARY KEY (id_curso, id_disciplina),
    FOREIGN KEY (id_curso) REFERENCES cursos(id_curso),
    FOREIGN KEY (id_disciplina) REFERENCES disciplinas(id_disciplina)
);

CREATE TABLE turmas (
    id_turma INTEGER NOT NULL PRIMARY KEY,
    id_curso INTEGER NOT NULL,
    periodo VARCHAR NOT NULL,
    num_alunos INTEGER NOT NULL,
    data_inicio DATE NOT NULL,
    data_fim DATE NOT NULL,
    FOREIGN KEY (id_curso) REFERENCES cursos(id_curso)
);

CREATE TABLE alunos (
    id_aluno INTEGER NOT NULL PRIMARY KEY,
    id_turma INTEGER NOT NULL,
    id_curso INTEGER NOT NULL,
    nome_aluno VARCHAR NOT NULL,
    sobrenome_aluno VARCHAR NOT NULL,
    cpf_aluno VARCHAR NOT NULL,
    status_aluno TINYINT NOT NULL,
    sexo_aluno VARCHAR NOT NULL,
    nome_pai VARCHAR NOT NULL,
    nome_mae VARCHAR NOT NULL,
    email_aluno VARCHAR NOT NULL,
    zap_aluno VARCHAR NOT NULL,
    FOREIGN KEY (id_turma) REFERENCES turmas(id_turma),
    FOREIGN KEY (id_curso) REFERENCES cursos(id_curso)
);

CREATE TABLE historico (
    id_historico INTEGER NOT NULL PRIMARY KEY,
    id_aluno INTEGER NOT NULL,
    data_inicio DATE NOT NULL,
    data_final DATE NOT NULL,
    FOREIGN KEY (id_aluno) REFERENCES alunos(id_aluno)
);
CREATE TABLE disciplina_historico (
    id_disciplina INTEGER NOT NULL,
    id_historico INTEGER NOT NULL,
    nota INTEGER NOT NULL,
    frequencia INTEGER NOT NULL,
    PRIMARY KEY (id_disciplina, id_historico),
    FOREIGN KEY (id_disciplina)
    REFERENCES disciplinas (id_disciplina),
    FOREIGN KEY (id_historico)
    REFERENCES historico (id_historico)
);
