# Modelo Criação Tabelas

## Script de criação de Tabelas para o Banco de Dados EstrelaDaMorte - Projeto DIO

###  CREATE TABLE Planetas(
           IdPlaneta int NOT NULL,
           Nome varchar (50) NOT NULL,
           Rotacao float NOT NULL,   
           Orbita float NOT NULL,
           Diametro float NOT NULL,
           Clima varchar (50) NOT NULL,
           População int NOT NULL,
)
GO 
ALTER TABLE Planetas ADD CONSTRAINT PK_Planetas PRIMARY KEY (IdPlaneta); 



###  CREATE TABLE NAVES(
    IdNave int NOT NULL,
    Nome varchar(100) NOT NULL,
    Modelo varchar(100) NOT NULL,
    Passageiros int NOT NULL,
    Carga float NOT NULL,
    Classe varchar (100),
)
GO
ALTER TABLE Naves ADD CONSTRAINT PK_Naves PRIMARY KEY (IdNave); 



### CREATE TABLE Pilotos (
         IdPiloto int NOT NULL,
         NOME varchar (200) NOT NULL,
         AnoNascimento varchar(10) NOT NULL,
         IdPlaneta int NOT NULL,
)
GO
ALTER TABLE Pilotos ADD CONSTRAINT PK_Pilotos PRIMARY KEY (IdPiloto)
GO
ALTER TABLE Pilotos ADD CONSTRAINT PK_Pilotos_Planetas FOREIGN KEY (IdPlaneta)
REFERENCES Planetas (IdPlaneta)



###  CREATE TABLE PilotosNaves(
           IdPiloto int NOT NULL,
           IdNave int NOT NULL,
           FlagAutorizado bit NOT NULL,
) 
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT PK_PilotosNaves PRIMARY KEY (IdPiloto, IdNAve)
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT FK_PilotosNaves_Pilotos FOREIGN KEY (IdPiloto)
REFERENCES Pilotos (IdPiloto)
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT FK_PilotosNaves_Naves FOREIGN KEY (IdNave)
REFERENCES Naves (IdNave)
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT DF_PilotosNaves_FlagAutorizado DEFAULT (1) FOR FlagAutorizado
 


###  CREATE TABLE HistoricoViagens (
           IdNave int NOTT NULL,
           IdPiloto int NOT NULL,
           DtSaida datetime NOT NULL,
           DtChegada datetime NULL
)
GO 

ALTER TABLE HistoricoViagens ADD CONSTRAINT FK_HistoricoViagens_PilotosNaves FOREIGN KEY (IdPiloto, IdNave)
REFERENCES PilotosNaves (IdPiloto, IdNave)
GO

ALTER TABLE HistoricoViagens CHECK CONSTRAINT FK_HistoricoViagens_PilotosNaves
           
