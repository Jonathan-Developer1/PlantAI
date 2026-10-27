# 3 Modelagem e diagramas arquiteturais: (Modelo C4)

A modelagem arquitetural do PlantAÍ foi definida utilizando o modelo C4, que permite representar o sistema em diferentes níveis de abstração. A solução é organizada em camadas, contemplando a interação com os usuários, a aplicação responsável pelo processamento das solicitações, os serviços de inteligência artificial e o banco de dados PostgreSQL.

Essa organização permite separar as responsabilidades do sistema, facilitando a manutenção, a integração entre os componentes e a evolução das funcionalidades de identificação de plantas e análise de possíveis doenças.

<p align="center">
  <img src="imagem/figura1.jfif" alt="Diagrama geral da arquitetura do PlantAÍ"><br>
  Figura 1: Visão Geral da Solução (camadas).[cite: 19]
</p>

## 3.1 Nível 1: Diagrama de Contexto

O diagrama de contexto apresenta uma visão geral do PlantAÍ, destacando os usuários e os sistemas externos que podem interagir com a solução. Os principais usuários são agricultores e técnicos agrícolas, que poderão utilizar o aplicativo para enviar imagens de plantas, consultar possíveis doenças e obter informações sobre prevenção e tratamento.

O PlantAÍ atua como o sistema central, recebendo as solicitações dos usuários e disponibilizando os resultados das análises. Para auxiliar na identificação de espécies vegetais e na análise de possíveis doenças, a solução poderá integrar serviços externos de inteligência artificial, conforme a arquitetura definida para o projeto.

<p align="center">
  <img src="imagem/figura2.jfif" alt="Diagrama de Contexto do PlantAÍ"><br>
  Figura 2: Diagrama de Contexto.[cite: 18]
</p>

## 3.2 Nível 2: Diagrama de Contêiner

O diagrama de contêiner apresenta a arquitetura de alto nível do PlantAÍ e a distribuição das responsabilidades entre seus principais elementos. A solução prevê um aplicativo mobile para interação com o usuário, um backend para processamento das solicitações e aplicação das regras de negócio, além de um banco de dados PostgreSQL para armazenamento das informações.

O aplicativo mobile será responsável pelo envio das imagens e pela apresentação dos resultados. O backend coordenará o processamento das solicitações, a integração com os serviços de inteligência artificial e a comunicação com o banco de dados. O PostgreSQL armazenará informações dos usuários, consultas realizadas e referências às imagens enviadas.

A arquitetura também prevê a integração com ferramentas de processamento de imagens e modelos de inteligência artificial para auxiliar na identificação das espécies vegetais e na detecção de possíveis doenças. Os componentes externos serão integrados conforme a implementação do projeto.

<p align="center">
  <img src="imagem/figura3.jfif" alt="Diagrama de Contêiner do PlantAÍ"><br>
  Figura 3: Diagrama de Contêiner.[cite: 17]
</p>

## 3.3 Nível 3: Diagrama de Componentes

O diagrama de componentes detalha a organização interna da aplicação e as responsabilidades de seus principais módulos. A arquitetura proposta utiliza a separação em camadas, distinguindo a interface do usuário, a lógica de negócio, a integração com serviços externos e a persistência dos dados.

Os componentes previstos incluem o módulo de gerenciamento de usuários, responsável pelos dados de cadastro e autenticação; o módulo de consultas, responsável por registrar e processar as solicitações de análise; o módulo de processamento de imagens, destinado à preparação das fotografias; e os módulos de integração com os modelos de inteligência artificial, responsáveis por auxiliar na identificação de plantas e na análise de possíveis doenças.

O componente de persistência será responsável pela comunicação com o banco de dados PostgreSQL, enquanto o módulo de armazenamento e recuperação de imagens utilizará as referências das fotografias associadas às consultas.

O projeto prevê o desenvolvimento dos componentes específicos da aplicação e o reaproveitamento de tecnologias e bibliotecas existentes, como PostgreSQL e ferramentas de processamento de imagens. Serviços externos e modelos de inteligência artificial serão utilizados conforme sua disponibilidade, compatibilidade e condições de uso.

<p align="center">
  <img src="imagem/figura4.jfif" alt="Diagrama de Componentes do PlantAÍ"><br>
  Figura 4: Diagrama de Componentes.[cite: 16]
</p>

## 3.4 Nível 4: Código

No nível de código, a estrutura do banco de dados é representada por meio do diagrama entidade-relacionamento (ER), complementado pela definição das tabelas e de seus atributos. A modelagem contempla as entidades Usuário, Consulta e Foto_Consulta, responsáveis pelo gerenciamento dos usuários, pelo registro das análises e pelo armazenamento das referências às imagens utilizadas.

A entidade Usuário contém os atributos identificador, nome, e-mail e senha. O identificador é a chave primária, enquanto o e-mail possui restrição de unicidade, evitando cadastros duplicados com o mesmo endereço.

A entidade Consulta registra as análises realizadas, contendo identificador, nome da planta, descrição da análise, grau, possível doença, probabilidade, data e identificador do usuário responsável. O campo id_usuario é uma chave estrangeira que relaciona cada consulta ao usuário que a realizou.

A entidade Foto_Consulta armazena o identificador da fotografia, a referência URI da imagem, a data de registro e o identificador da consulta associada. A chave estrangeira id_consulta estabelece o relacionamento entre as fotografias e as consultas, permitindo associar as imagens ao processo de análise correspondente.

Dessa forma, um usuário pode realizar várias consultas, e cada consulta pode possuir uma ou mais fotografias associadas. A exclusão de uma consulta também remove as fotografias vinculadas a ela, conforme a regra ON DELETE CASCADE definida no banco de dados.

<p align="center">
  <img src="imagem/DER_3.jpg" alt="Diagrama Entidade-Relacionamento do PlantAÍ" width="600"><br>
  Figura 5: Diagrama Entidade-Relacionamento (ER) do PlantAÍ.[cite: 15]
</p>
