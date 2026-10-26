# Briefing de Desenvolvimento de Software

> **Projeto:** Raiz  
> **Versão:** 1.0  
> **Status:** Proposta inicial  
> **Data:** 24/10/2026

## 1. Informações gerais

- **Nome do projeto:** Raiz
- **Cliente:** Instituto Raiz Urbana
- **Responsável pelo contato:** Helena Martins, coordenadora de projetos
- **Equipe de desenvolvimento:** Equipe de desenvolvimento web contratada
- **Tipo de sistema:** Aplicação web de gestão de iniciativas ambientais comunitárias.

## 2. Visão geral do projeto

### 2.1. Apresentação

O Instituto Raiz Urbana é uma organização fictícia que promove a recuperação de espaços urbanos por meio de hortas comunitárias, jardins de chuva, arborização e educação ambiental.

A organização atua em parceria com moradores, voluntários, escolas e pequenos coletivos locais.

### 2.2. Descrição da ideia

Desenvolver uma plataforma web que permita cadastrar e divulgar projetos ambientais, organizar suas atividades e facilitar a participação da comunidade.

A plataforma terá duas áreas principais:

- **Área pública e do cliente:** permite explorar os projetos, consultar informações e manifestar interesse em participar das iniciativas.
- **Painel administrativo:** permite gerenciar projetos, atividades, categorias, imagens e inscrições de participantes.

### 2.3. Problema ou necessidade

Atualmente, o instituto utiliza planilhas, mensagens e publicações em redes sociais para organizar suas iniciativas.

Essa abordagem dificulta a centralização das informações, o acompanhamento das atividades e a divulgação de projetos ativos.

O software deverá reunir essas informações em um único ambiente, tornando a gestão mais organizada e o acesso da comunidade mais simples.

### 2.4. Objetivos

**Objetivo principal:** centralizar a divulgação e a organização das iniciativas ambientais do instituto.

**Objetivos secundários:**

- Facilitar a descoberta de projetos pela comunidade.
- Organizar tarefas e atividades vinculadas a cada projeto.
- Permitir que moradores manifestem interesse em participar.
- Melhorar o acompanhamento do andamento das iniciativas.
- Criar um catálogo visual de projetos ambientais.
- Facilitar a atualização das informações pela equipe administrativa.

### 2.5. Indicadores de sucesso

- Todos os projetos cadastrados podem ser consultados pela área pública.
- A equipe consegue gerenciar projetos e atividades sem editar diretamente o banco de dados.
- Os usuários conseguem se cadastrar, entrar e sair da plataforma.
- As manifestações de interesse ficam registradas e podem ser consultadas pelos administradores.
- As informações permanecem consistentes após operações de cadastro, edição e exclusão.

## 3. Público-alvo e usuários

### 3.1. Público-alvo

- Moradores interessados em iniciativas ambientais.
- Voluntários e estudantes.
- Coletivos e organizações comunitárias.
- Equipe responsável pela gestão do instituto.

### 3.2. Perfis de usuários

| Perfil | Descrição | Responsabilidades |
|---|---|---|
| Visitante | Pessoa sem sessão autenticada | Explorar o catálogo e consultar projetos |
| Cliente cadastrado | Morador com conta na plataforma | Gerenciar perfil e manifestar interesse em projetos |
| Administrador | Integrante autorizado do instituto | Gerenciar projetos, atividades, categorias e inscrições |

### 3.3. Permissões e acessos

- Visitantes podem visualizar projetos publicados, mas não podem realizar inscrições.
- Clientes podem visualizar e editar o próprio perfil e registrar interesse em projetos.
- Clientes não podem alterar projetos, atividades ou informações de outros usuários.
- Administradores podem criar, consultar, editar e excluir projetos e atividades.
- Administradores podem consultar as manifestações de interesse e alterar seus estados.
- Apenas administradores podem gerenciar categorias.
- A autenticação será baseada em sessão por cookies.
- Rotas administrativas deverão verificar as permissões no servidor, não apenas ocultar botões na interface.

## 4. Funcionalidades do sistema

### 4.1. Funcionalidades principais

| Código | Funcionalidade | Prioridade |
|---|---|---|
| RF01 | Cadastro, login e logout | Alta |
| RF02 | Visualização do catálogo de projetos | Alta |
| RF03 | Consulta detalhada de um projeto | Alta |
| RF04 | Cadastro, edição e exclusão de projetos | Alta |
| RF05 | Cadastro e exibição de imagens dos projetos | Alta |
| RF06 | Gerenciamento das atividades dos projetos | Alta |
| RF07 | Manifestação de interesse em projetos | Alta |
| RF08 | Gerenciamento das manifestações de interesse | Alta |
| RF09 | Edição do perfil do usuário | Média |
| RF10 | Gerenciamento de categorias | Média |
| RF11 | Filtros por categoria e estado do projeto | Média |
| RF12 | Painel com indicadores administrativos | Baixa |

### 4.2. Detalhamento das funcionalidades

#### A. Catálogo de projetos

- **Objetivo:** permitir que os visitantes descubram iniciativas ambientais.
- **Usuários:** visitantes e clientes cadastrados.
- **Funcionamento:** exibir cartões com imagem, título, categoria, localização e estado do projeto.
- **Dados necessários:** título, descrição, imagem, categoria, localização e estado.
- **Resultado:** o usuário consegue explorar as iniciativas e acessar seus detalhes.
- **Regras:** somente projetos publicados serão exibidos no catálogo público.

#### B. Detalhes do projeto

- **Objetivo:** apresentar as informações completas de uma iniciativa.
- **Usuários:** visitantes e clientes cadastrados.
- **Funcionamento:** exibir descrição, galeria de imagens, localização, atividades e informações de participação.
- **Resultado:** o usuário compreende a proposta e pode decidir se deseja participar.
- **Regras:** projetos não publicados não poderão ser acessados por usuários comuns.

#### C. Gerenciamento de projetos

- **Objetivo:** permitir que os administradores mantenham o catálogo atualizado.
- **Usuários:** administradores.
- **Funcionamento:** formulário de cadastro e edição com título, descrição, categoria, localização, imagem de capa e estado de publicação.
- **Resultado:** os projetos ficam armazenados no PostgreSQL e podem ser exibidos na interface.
- **Regras:** o sistema deverá validar os campos obrigatórios e impedir referências a categorias inexistentes.

#### D. Gerenciamento de atividades

- **Objetivo:** organizar as tarefas associadas a cada iniciativa.
- **Usuários:** administradores.
- **Funcionamento:** cadastrar atividades com título, descrição, responsável, prazo e estado.
- **Resultado:** cada projeto apresenta uma lista organizada de atividades.
- **Regras:** uma atividade deverá estar associada a um projeto existente.

#### E. Participação em projetos

- **Objetivo:** permitir que moradores demonstrem interesse em colaborar.
- **Usuários:** clientes cadastrados.
- **Funcionamento:** o usuário seleciona a opção de participar e registra uma manifestação de interesse.
- **Resultado:** a solicitação fica disponível para análise administrativa.
- **Regras:** cada usuário poderá manter apenas uma manifestação por projeto. Solicitações poderão ser aceitas, recusadas ou marcadas como concluídas.

### 4.3. Requisitos funcionais

- **RF01:** o sistema deverá permitir o cadastro de usuários.
- **RF02:** o sistema deverá autenticar usuários e encerrar suas sessões.
- **RF03:** o sistema deverá permitir a consulta de projetos publicados.
- **RF04:** o sistema deverá permitir operações CRUD sobre projetos.
- **RF05:** o sistema deverá armazenar e exibir imagens dos projetos.
- **RF06:** o sistema deverá permitir operações CRUD sobre atividades.
- **RF07:** o sistema deverá registrar manifestações de interesse.
- **RF08:** o sistema deverá permitir a análise administrativa dessas manifestações.
- **RF09:** o sistema deverá permitir a edição do perfil do próprio usuário.
- **RF10:** o sistema deverá permitir o gerenciamento de categorias.
- **RF11:** o sistema deverá aplicar filtros ao catálogo.
- **RF12:** o sistema deverá restringir operações administrativas a usuários autorizados.

### 4.4. Funcionalidades futuras

- Mapa interativo com a localização dos projetos.
- Calendário comunitário de mutirões e eventos.
- Sistema de comentários e atualizações dos projetos.
- Registro de doações de materiais e ferramentas.
- Indicadores de impacto ambiental, como mudas plantadas e áreas recuperadas.
- Notificações por e-mail.
- Inscrição em atividades específicas, com limite de participantes.

Essas funcionalidades não fazem parte da primeira versão.

## 5. Regras de negócio

**RN01. Publicação:** projetos em rascunho não aparecem no catálogo público.

**RN02. Integridade:** um projeto deverá possuir uma categoria válida.

**RN03. Atividades:** cada atividade deverá pertencer a um único projeto.

**RN04. Participação:** apenas usuários autenticados poderão manifestar interesse.

**RN05. Duplicidade:** um usuário não poderá registrar duas manifestações para o mesmo projeto.

**RN06. Privacidade:** um usuário poderá consultar e modificar somente o próprio perfil.

**RN07. Administração:** apenas administradores poderão alterar projetos, atividades, categorias e estados das manifestações.

**RN08. Exclusão:** a remoção de projetos deverá considerar as atividades e as manifestações associadas, evitando registros órfãos. A estratégia de exclusão deverá ser definida na modelagem do banco.

**RN09. Imagens:** cada projeto deverá possuir uma imagem de capa. A aplicação deverá validar os arquivos enviados e impedir o armazenamento de tipos não permitidos.

**RN10. Estados de projeto:** os projetos poderão estar em planejamento, ativos, pausados ou concluídos. A publicação será controlada separadamente do estado operacional.

## 6. Requisitos não funcionais

### 6.1. Desempenho

- O catálogo deverá apresentar os projetos sem exigir o carregamento de todas as informações detalhadas.
- Consultas e alterações deverão ser realizadas por meio de operações no backend.
- O sistema deverá suportar o uso simultâneo por uma pequena comunidade.
- As imagens deverão ter dimensões e tamanhos adequados para uso na web.

### 6.2. Segurança e privacidade

- Senhas deverão ser armazenadas usando hash seguro.
- Cookies de sessão deverão possuir configurações de segurança apropriadas ao ambiente.
- Rotas privadas deverão validar a sessão e as permissões.
- As consultas ao PostgreSQL deverão utilizar parâmetros para evitar SQL injection.
- Os dados de conexão deverão ser definidos em variáveis de ambiente.
- Arquivos enviados deverão passar por validação de tipo e tamanho.
- Dados pessoais deverão ser limitados ao necessário para o funcionamento do sistema.
- O projeto deverá considerar os princípios aplicáveis da LGPD.

### 6.3. Disponibilidade e confiabilidade

- O sistema deverá apresentar mensagens compreensíveis quando ocorrerem erros.
- Falhas de banco de dados não deverão resultar em respostas técnicas expostas ao usuário.
- As operações de escrita deverão preservar a integridade dos dados.
- A documentação deverá explicar como configurar e executar a aplicação localmente.

### 6.4. Compatibilidade e acessibilidade

- Interface responsiva para computadores e smartphones.
- Compatibilidade com navegadores modernos.
- Uso de HTML semântico.
- Contraste adequado, navegação por teclado e textos alternativos para imagens.
- Formulários com rótulos e mensagens de validação.

## 7. Design e experiência do usuário

### 7.1. Identidade visual

O Raiz deverá apresentar uma identidade visual inspirada em ecossistemas, agricultura urbana e tecnologias sustentáveis.

**Direção visual:**
- Verde-musgo e verde-folha.
- Tons de creme e areia como fundo.
- Detalhes em amarelo solar ou terracota.
- Tipografia legível, com títulos expressivos.
- Fotografias de hortas, jardins, sementes e espaços comunitários.
- Elementos gráficos inspirados em folhas, raízes, mapas e topografia.

A estética deverá ser contemporânea e acolhedora, evitando parecer um painel corporativo genérico.

### 7.2. Interface e navegação

A interface pública deverá priorizar a descoberta dos projetos. O painel administrativo deverá priorizar a organização e a rapidez das operações.

### 7.3. Páginas da primeira versão

A aplicação deverá possuir, no mínimo, quatro páginas HTML interligadas:

1. **Início (`index.html`):** apresentação do instituto, projetos em destaque e chamada para participação.
2. **Projetos (`projetos.html`):** catálogo de projetos, filtros e pesquisa.
3. **Detalhes do projeto (`projeto.html`):** informações completas de um projeto selecionado.
4. **Entrar (`login.html`):** formulário de autenticação.

As áreas de cadastro de conta, perfil e administração poderão ser implementadas em páginas adicionais.

O cabeçalho deverá conter a identidade visual e o menu de navegação. O rodapé deverá apresentar o nome completo do desenvolvedor, a turma e o ano, conforme solicitado no projeto acadêmico.

## 8. Dados e integrações

### 8.1. Gerenciamento de dados

O sistema utilizará PostgreSQL para armazenar os dados relacionais.

A modelagem inicial será composta pelas seguintes tabelas:

| Tabela | Finalidade | Relacionamento |
|---|---|---|
| `categories` | Categorias ambientais | Tabela de referência |
| `users` | Dados de autenticação e identificação | Relaciona-se a perfis e manifestações |
| `user_profiles` | Informações complementares dos usuários | 1:1 com `users` |
| `projects` | Cadastro das iniciativas | Relaciona-se a categorias e atividades |
| `activities` | Tarefas de cada iniciativa | N:1 com `projects` |
| `project_interests` | Manifestações de interesse | Relaciona usuários e projetos |

**Relacionamentos principais:**

- `users` ↔ `user_profiles`: um para um, com chave estrangeira única em `user_profiles.user_id`.
- `projects` → `activities`: um para muitos, pois um projeto poderá conter várias atividades.
- `categories` → `projects`: um para muitos, pois uma categoria poderá classificar vários projetos.
- `users` → `project_interests`: um para muitos.
- `projects` → `project_interests`: um para muitos.

A tabela `categories` será independente de outras tabelas por não possuir chaves estrangeiras próprias.

O banco deverá possuir um arquivo SQL de criação e carga inicial, com pelo menos dez registros por tabela, conforme o requisito acadêmico.

### 8.2. Imagens

As imagens dos projetos poderão ser armazenadas localmente durante a execução da aplicação, enquanto seus caminhos relativos serão registrados no banco de dados.

O CRUD de projetos deverá permitir cadastrar, visualizar, substituir e remover imagens. A exclusão de um arquivo deverá considerar se ele ainda está sendo utilizado por algum registro.

### 8.3. Integrações externas

Nenhuma integração externa será obrigatória na primeira versão.

- Pagamentos: não aplicável.
- Mapas: recurso futuro.
- E-mail: recurso futuro.
- APIs ambientais: recurso futuro.

## 9. Infraestrutura e tecnologia

- **Frontend:** HTML5, CSS3 e JavaScript.
- **Backend:** Node.js.
- **Arquitetura:** Cliente/Servidor, com padrão MVC.
- **Roteamento:** módulos Router separados dos Controllers.
- **Banco de dados:** PostgreSQL.
- **Conexão:** variáveis de ambiente em arquivo `.env`.
- **Autenticação:** sessão com cookies.
- **Versionamento:** Git e GitHub.
- **Hospedagem:** ambiente local durante o desenvolvimento e publicação a definir.

O projeto deverá seguir a organização arquitetural do projeto `candyshop`, usado como referência na disciplina.

O arquivo `.env` não deverá ser versionado. O repositório deverá conter `.gitignore` e `README.md` com instruções de execução, documentação e diagrama do banco de dados.

## 10. Escopo do projeto

### 10.1. Incluído no escopo

- Cadastro, login e logout.
- Controle de acesso por perfil.
- Catálogo público de projetos.
- Página de detalhes de cada projeto.
- CRUD de projetos com imagens.
- CRUD de atividades.
- Gerenciamento de categorias.
- Cadastro e edição do perfil.
- Registro e análise de manifestações de interesse.
- Integração com PostgreSQL.
- Interface responsiva.
- Documentação técnica e carga inicial de dados.

### 10.2. Fora do escopo

- Aplicativo nativo para smartphones.
- Pagamentos e transferências financeiras.
- Conversas em tempo real.
- Notificações push.
- Integração com serviços externos.
- Sistema avançado de relatórios.
- Mapa interativo.
- Implantação em infraestrutura de produção definitiva.

### 10.3. Entregáveis

- [x] Aplicação web com frontend e backend.
- [x] Integração com PostgreSQL.
- [x] Arquitetura MVC com rotas e controllers.
- [x] Sistema de autenticação.
- [x] CRUD com gerenciamento de imagens.
- [x] Arquivo SQL de criação e carga inicial.
- [x] Arquivo `.gitignore`.
- [x] Arquivo `.env.example`, sem credenciais reais.
- [x] `README.md` com guia de execução e diagrama do banco.
- [x] Repositório GitHub.
- [x] Demonstração das áreas administrativa e pública.

## 11. Cronograma

Considerando o prazo acadêmico de 25/11/2026:

| Etapa | Período previsto |
|---|---|
| Levantamento e validação dos requisitos | 24 a 25/10 |
| Modelagem do banco e arquitetura | 26 a 28/10 |
| Estruturação do frontend | 29/10 a 02/11 |
| Desenvolvimento do backend e autenticação | 03 a 08/11 |
| Implementação das regras de negócio | 09 a 14/11 |
| Integração, imagens e ajustes de interface | 15 a 18/11 |
| Testes e correções | 19 a 22/11 |
| Documentação e preparação da demonstração | 23 a 24/11 |
| Revisão final e entrega | 25/11 |

O cronograma é uma estimativa inicial e deverá ser ajustado conforme o andamento do desenvolvimento.

## 12. Orçamento e condições

Como se trata de um cliente simulado para um projeto acadêmico, não haverá cobrança real.

- **Orçamento:** não aplicável.
- **Contratação:** não aplicável.
- **Hospedagem:** ambiente local para desenvolvimento e apresentação.
- **Custos recorrentes:** nenhum previsto para a versão acadêmica.
- **Manutenção:** correções durante o desenvolvimento e a validação.

## 13. Critérios de aceitação

| Critério | Como será verificado? |
|---|---|
| Navegação | Pelo menos quatro páginas HTML interligadas |
| Arquitetura | Separação entre rotas, controllers e camada de dados |
| Banco de dados | Conexão funcional com PostgreSQL |
| Modelagem | Relacionamentos 1:1 e 1:N implementados |
| Carga inicial | Pelo menos dez registros em cada tabela |
| Autenticação | Login e logout por cookies funcionando |
| Autorização | Usuários comuns não conseguem executar operações administrativas |
| CRUD | Cadastro, consulta, edição e exclusão de projetos |
| Imagens | Cadastro e exibição de imagens funcionando |
| Atividades | Criação e gerenciamento de atividades vinculadas aos projetos |
| Participação | Registro e análise de manifestações de interesse |
| Documentação | README, diagrama do banco e guia de execução disponíveis |
| Repositório | Código versionado no GitHub com os arquivos exigidos |

## 14. Riscos, dependências e pendências

### 14.1. Riscos conhecidos

- O escopo poderá ficar grande demais para o prazo acadêmico.
- A autenticação e o controle de permissões exigirão atenção especial.
- A exclusão de projetos poderá afetar registros relacionados.
- O armazenamento de imagens precisará ser configurado corretamente.
- A carga inicial de dados poderá consumir tempo se for feita manualmente.

### 14.2. Dependências

- PostgreSQL instalado e acessível.
- Node.js configurado.
- Credenciais locais definidas no `.env`.
- Definição das imagens utilizadas nos projetos.
- Disponibilidade de dados fictícios para testes.
- Repositório GitHub configurado conforme as exigências acadêmicas.

### 14.3. Pendências

- [ ] Definir a lista final de categorias ambientais.
- [ ] Definir os estados possíveis para as manifestações de interesse.
- [ ] Escolher a biblioteca de gerenciamento de sessões por cookies.
- [ ] Definir os limites de tamanho e os formatos aceitos para imagens.
- [ ] Elaborar o diagrama entidade-relacionamento.
- [ ] Preparar a carga inicial com dados fictícios.
- [ ] Confirmar a aprovação do escopo.

## 15. Validação do briefing

- [x] Problema e objetivos definidos.
- [x] Perfis de usuários identificados.
- [x] Funcionalidades prioritárias definidas.
- [x] Regras de negócio documentadas.
- [x] Escopo inicial estabelecido.
- [x] Tecnologias principais definidas.
- [x] Prazo acadêmico considerado.
- [ ] Pendências técnicas resolvidas.
- [ ] Aprovação final do cliente simulado.

**Responsável pela aprovação:** Helena Martins, coordenadora fictícia do Instituto Raiz Urbana.

**Data:** a definir após revisão do documento.

**Observação final:** este briefing representa a proposta inicial do projeto Raiz. As decisões técnicas detalhadas, os diagramas, os contratos das rotas HTTP e os protótipos deverão ser desenvolvidos antes ou durante a implementação, conforme a necessidade.

---

*Raiz: conectar pessoas, organizar iniciativas e transformar espaços esquecidos em lugares vivos.*