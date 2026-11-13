ESPECIFICAÇÃO DE TODOS OS CASOS DE USOUC01 — Autenticar-se
Identificador: UC01Nome: Autenticar-se
Objetivo: Permitir que o usuário acesse a plataforma de forma segura utilizando e-mail e senha, respeitando as regras de bloqueio, controle de sessão e autenticação de dois fatores.
Atores: Administrador, Psicólogo, Atendente, Paciente, Responsável Legal.
Pré-condições:
O usuário deve possuir uma conta de acesso cadastrada.
O status do usuário deve ser "Ativo".
Pós-condições:
O usuário está autenticado e com uma sessão ativa.
A sessão anterior (se houver em outro dispositivo) é encerrada.
As tentativas de login (sucesso ou falha) e o acesso são registrados em log de auditoria, quando aplicável.
Fluxo Principal:
O usuário acessa a tela de login e informa e-mail e senha.
O sistema valida o formato dos dados e verifica as credenciais.
O sistema verifica se o status do usuário é "Ativo".
O sistema verifica se já existe uma sessão ativa para esta conta em outro dispositivo e a invalida.
O sistema verifica se a operação exige autenticação de dois fatores (2FA).
O sistema solicita e valida o segundo fator de autenticação.
O sistema cria a sessão e concede acesso à plataforma.
O sistema verifica se a senha é provisória.
O sistema redireciona o usuário para a tela de alteração de senha (UC02).
Fluxos Alternativos:
5a. A operação não exige 2FA (usuário comum em dispositivo reconhecido):5a.1. O sistema pula para o passo 7.
8a. A senha não é provisória:8a.1. O sistema concede acesso direto ao painel principal do usuário e encerra o caso de uso.
Fluxos de Exceção:
2a. Credenciais inválidas (e-mail ou senha incorretos):2a.1. O sistema incrementa o contador de tentativas falhas.2a.2. Se o contador atingir 5 tentativas consecutivas, o sistema bloqueia temporariamente a conta por 15 minutos.2a.3. O sistema envia e-mail de notificação de bloqueio (RF-009).2a.4. O sistema exibe mensagem genérica de erro e encerra o caso de uso.
3a. Usuário com status "Inativo" ou "Bloqueado":3a.1. O sistema nega a autenticação.3a.2. O sistema exibe mensagem genérica (sem revelar o status real) e encerra o caso de uso.
6a. Falha na validação do segundo fator:6a.1. O sistema exibe mensagem de erro e permite nova tentativa.6a.2. Se exceder o limite de tentativas de 2FA, o sistema cancela a autenticação e encerra o caso de uso.
Regras de Negócio: RN-001, RN-009, RN-010, RN-011, RN-012, RN-013, RN-014, RN-015.Requisitos Funcionais: RF-001, RF-003, RF-006, RF-008, RF-009, RF-010, RF-011.Requisitos Não Funcionais: RNF-001 a RNF-008, RNF-039.Rastreabilidade: UC02, UC03, UC05.
UC02 — Alterar Senha
Identificador: UC02
Nome: Alterar Senha
Objetivo: Permitir que o usuário autenticado altere a sua senha de acesso, exigindo a validação da senha atual e o cumprimento de políticas de complexidade.
Atores: Administrador, Psicólogo, Atendente, Paciente, Responsável Legal.
Pré-condições:
O usuário deve estar autenticado na plataforma.
O usuário deve possuir permissão para gerenciar suas credenciais.
A senha do usuário é atualizada de forma segura (armazenada com hash e salt).
Pós-condições:
O status de "senha provisória" (se houver) é desativado.
A alteração é registrada no log de auditoria.
Sessões ativas em outros dispositivos podem ser invalidadas por segurança.
Fluxo Principal:
O usuário acessa as configurações de perfil ou é redirecionado pelo sistema (após o primeiro login com senha provisória).
O usuário solicita a alteração de senha, informando a senha atual e a nova senha (junto com a confirmação).
O sistema valida se a senha atual informada está correta.
O sistema valida se a nova senha atende aos critérios de complexidade da política de segurança (mínimo de caracteres, letras maiúsculas, minúsculas, números e caracteres especiais).
O sistema valida se a nova senha é diferente da senha atual.
O sistema atualiza o registro da senha criptografada na base de dados.
O sistema registra a operação no log de auditoria.
O sistema exibe uma mensagem de sucesso e atualiza o estado da credencial.
O caso de uso é encerrado.
Fluxos Alternativos:
2a. O usuário está alterando a senha por solicitação de redefinição anterior (token válido):
2a.1. O sistema pula a exigência da senha atual, validando apenas o token de recuperação enviado por e-mail e a nova senha.
2a.2. O sistema prossegue para o passo 4.
Fluxos de Exceção:
3a. Senha atual incorreta:
3a.1. O sistema exibe mensagem de erro informando que a senha atual é inválida.
3a.2. O sistema incrementa a contagem de falhas e encerra ou permite nova tentativa conforme o limite.
4a. Nova senha fora dos critérios de complexidade:
4a.1. O sistema destaca os requisitos de segurança não atendidos.
4a.2. O sistema solicita que o usuário insira uma nova senha válida e retorna ao passo 2.
5a. A nova senha é idêntica à senha atual:
5a.1. O sistema exibe mensagem informando que a nova senha deve ser diferente da anterior e retorna ao passo 2.
Regras de Negócio: RN-001, RN-009, RN-010, RN-012, RN-013.
Requisitos Funcionais: RF-002, RF-012.
Requisitos Não Funcionais: RNF-001, RNF-002, RNF-005, RNF-006.
Rastreabilidade: UC01, UC06.
UC03 — Recuperar Senha
Identificador: UC03Nome: Recuperar Senha
Objetivo: Permitir que um usuário não autenticado solicite a recuperação de sua senha por e-mail, sem que o sistema revele a existência da conta.
Atores: Administrador, Psicólogo, Atendente, Paciente, Responsável Legal, Serviço de E-mail.
Pré-condições: Nenhuma (o usuário não precisa estar autenticado).
Pós-condições:
O usuário recebe (ou não) o e-mail com instruções de redefinição.
A solicitação é registrada em log de auditoria.
Fluxo Principal:
O usuário acessa a tela de recuperação de senha e informa seu e-mail.
O sistema verifica se o e-mail existe na base de dados.
O sistema gera um token único e temporário.
O sistema aciona o Serviço de E-mail para enviar a mensagem com o link de redefinição.
O sistema exibe uma mensagem genérica de sucesso (ex.: "Se o e-mail estiver cadastrado, enviaremos as instruções").
O caso de uso é encerrado.
Fluxos Alternativos:
2a. E-mail não cadastrado:2a.1. O sistema ignora a geração do token.2a.2. O sistema exibe a mesma mensagem genérica de sucesso.2a.3. O caso de uso é encerrado (proteção contra enumeração de usuários).
Fluxos de Exceção:
4a. Serviço de E-mail indisponível:4a.1. O sistema retém a notificação em uma fila de reenvio.4a.2. O sistema exibe a mensagem genérica de sucesso para o usuário.4a.3. O sistema registra a falha de envio em log.
Regras de Negócio: RN-014 (Não exposição de existência de conta).Requisitos Funcionais: RF-004.Requisitos Não Funcionais: RNF-008, RNF-030, RNF-031.Rastreabilidade: UC01, UC04.
UC04 — Redefinir Senha
Identificador: UC04
Nome: Redefinir Senha
Objetivo: Permitir que o usuário redefina sua senha utilizando um token de recuperação válido enviado por e-mail, estabelecendo uma nova credencial segura sem necessidade de informar a senha anterior.
Atores: Administrador, Psicólogo, Atendente, Paciente, Responsável Legal.
Pré-condições:
O usuário deve ter solicitado a recuperação de senha previamente (UC03).
O token gerado deve ser válido e estar dentro do prazo de expiração.
Pós-condições:
A nova senha é criptografada e atualizada na base de dados.
O token utilizado é invalidado permanentemente.
O evento é registrado no log de auditoria.
Fluxo Principal:
O usuário acede ao link de redefinição enviado por e-mail contendo o token.
O sistema valida a autenticidade e a validade temporal do token.
O sistema solicita a inserção da nova senha e a respetiva confirmação.
O usuário insere a nova senha.
O sistema valida se a nova senha atende aos critérios de complexidade de segurança.
O sistema atualiza o registo da senha encriptada e invalida o token.
O sistema regista a operação no log de auditoria.
O sistema exibe mensagem de sucesso e redireciona para a tela de autenticação (UC01).
O caso de uso é encerrado.
Fluxos de Exceção:
2a. Token inválido ou expirado:
2a.1. O sistema deteta que o token expirou ou é inválido.
2a.2. O sistema exibe mensagem de erro e solicita um novo pedido de recuperação (retorna a UC03).
2a.3. O caso de uso é encerrado.
5a. Senha fora dos critérios de complexidade:
5a.1. O sistema destaca os requisitos não atendidos e solicita nova entrada (retorna ao passo 3).
Regras de Negócio: RN-009, RN-010, RN-012, RN-014.
Requisitos Funcionais: RF-002, RF-004, RF-005.
Requisitos Não Funcionais: RNF-001, RNF-002, RNF-005.
Rastreabilidade: UC01, UC03.
UC05 — Gerir Sessões de Utilizador
Identificador: UC05
Nome: Gerir Sessões de Utilizador
Objetivo: Permitir o controlo ativo e o encerramento de sessões simultâneas ou inativas na plataforma, garantindo a segurança contra acessos não autorizados.
Atores: Administrador, Utilizador Autenticado.
Pré-condições: 
O utilizador deve estar autenticado com uma sessão válida.
Pós-condições: 
Sessões selecionadas são encerradas e tokens de acesso revogados.
Fluxo Principal:
O utilizador acede às definições de segurança e visualiza as sessões ativas (dispositivos e IPs).
O utilizador seleciona uma sessão específica e opta por "Encerrar Sessão".
O sistema revoga o token JWT correspondente e remove o registo de sessão ativa.
O sistema regista a ação no log de auditoria.
O sistema atualiza a lista de sessões ativas e exibe confirmação.
O caso de uso é encerrado.
Fluxos de Exceção:
3a. Falha de comunicação com o servidor de autenticação:
3a.1. O sistema exibe mensagem de indisponibilidade momentânea e sugere nova tentativa.
Regras de Negócio: RN-011, RN-012.
Requisitos Funcionais: RF-006, RF-010.
Requisitos Não Funcionais: RNF-003, RNF-004.
Rastreabilidade: UC01.
UC06 — Gerenciar Contas de Acesso
Identificador: UC06Nome: Gerenciar Contas de Acesso
Objetivo: Permitir que o Administrador crie, consulte e gerencie as contas de acesso ao sistema (exceto pacientes e responsáveis legais, que têm casos específicos), definindo senhas provisórias e perfis.
Atores: Administrador.
Pré-condições: O usuário deve estar autenticado como Administrador.
Pós-condições:
A conta do usuário é criada/atualizada.
O usuário está associado a um perfil e permissões.
O log de auditoria registra a operação.
Fluxo Principal:
O Administrador seleciona a opção "Gerenciar Contas".
O sistema exibe a lista de usuários cadastrados.
O Administrador opta por criar uma nova conta e insere os dados (nome, e-mail, CRP quando aplicável, perfil).
O sistema valida os campos críticos (CPF/CRP/e-mail/telefone).
O sistema cria a conta com status "Ativo".
O sistema gera uma senha provisória para o usuário.
O sistema define que a senha deve ser alterada no primeiro acesso.
O sistema envia a senha provisória por e-mail.
O sistema registra a ação no log de auditoria.
O caso de uso é encerrado.
Fluxos Alternativos:
3a. O Administrador edita uma conta existente:3a.1. O sistema permite alterar dados cadastrais e perfis.3a.2. O sistema executa a validação e registra a alteração no log.
Fluxos de Exceção:
4a. Dados inválidos (CPF inválido, e-mail já em uso, etc.):4a.1. O sistema exibe mensagem de erro específica.4a.2. O Administrador corrige e reenvia.
5a. CRP inválido (no cadastro de psicólogo):5a.1. O sistema consulta a Base Externa do CFP.5a.2. Se o CFP indicar inválido, a conta é criada com status "Inativo" até correção.5a.3. Se a API do CFP estiver indisponível, o sistema permite a validação manual posterior pelo Administrador.
Regras de Negócio: RN-002, RN-003, RN-004, RN-008, RN-017, RN-021.Requisitos Funcionais: RF-012, RF-013, RF-021.Requisitos Não Funcionais: RNF-009, RNF-010, RNF-040.Rastreabilidade: UC08, UC10, UC17, UC18.
UC07 — Gerir Perfis de Acesso
Identificador: UC07
Nome: Gerir Perfis de Acesso
Objetivo: Permitir que o Administrador crie, edite ou associe conjuntos de permissões a perfis específicos do sistema (Administrador, Psicólogo, Atendente, Paciente, Responsável, Pesquisador).
Atores: Administrador.
Pré-condições: 
O Administrador deve estar autenticado.
Pós-condições: 
Perfis e matrizes de permissão atualizados na base de dados.
Fluxo Principal:
O Administrador acede ao módulo de controlo de acessos e seleciona "Perfis".
O sistema exibe a lista de perfis disponíveis.
O Administrador seleciona um perfil para editar ou clica em "Novo Perfil".
O Administrador define o nome e assinala as permissões associadas.
O sistema valida e grava as alterações.
O sistema regista a operação no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-005, RN-006, RN-007.
Requisitos Funcionais: RF-014, RF-015.
Requisitos Não Funcionais: RNF-009, RNF-010.
Rastreabilidade: UC06, UC09.
UC08 — Gerenciar Status de Usuários
Identificador: UC08
Nome: Gerenciar Status de Usuários
Objetivo: Permitir que o Administrador altere o status de acesso de um utilizador cadastrado (entre Ativo, Inativo e Bloqueado), aplicando as regras de negócio de encerramento de vínculos, suspensão de pesquisas e notificação de auditoria.
Atores: Administrador.
Pré-condições:
O Administrador deve estar autenticado na plataforma com sessão ativa.
O utilizador alvo deve estar previamente cadastrado no sistema.
O status de acesso do utilizador é atualizado na base de dados (tb_usuario).
Pós-condições:
Caso o utilizador seja um Psicólogo inativado/bloqueado: os seus vínculos ativos com pacientes são encerrados e o histórico de atendimento é preservado.
Caso o utilizador seja responsável por pesquisas científicas: as pesquisas são tratadas conforme as regras do Comitê de Ética (suspensão/cancelamento/transferência).
A operação é gravada de forma imutável no log de auditoria.
Fluxo Principal:
O Administrador acede ao módulo de gestão de utilizadores e pesquisa a conta desejada.
O sistema exibe os detalhes do utilizador e o seu status atual (Ativo, Inativo ou Bloqueado).
O Administrador escolhe a opção de alterar status e seleciona o novo estado pretendido.
O Administrador introduz a justificativa da alteração de status.
O sistema valida se o Administrador possui permissão explícita para a operação.
O sistema atualiza o status do utilizador na base de dados.
O sistema verifica o perfil do utilizador (se é Psicólogo/Pesquisador) e despoleta as regras automáticas de inativação/bloqueio (encerramento de vínculos e suspensão de pesquisas).
O sistema encerra de imediato quaisquer sessões ativas existentes para a conta inativada ou bloqueada.
O sistema regista a ação, a justificativa, a data/hora e o responsável no log de auditoria.
O sistema exibe mensagem de confirmação da alteração de status.
O caso de uso é encerrado.
Fluxos Alternativos:
7a. O utilizador alterado é um Psicólogo com vínculos ativos (RN-031):
7a.1. O sistema encerra automaticamente os vínculos ativos com pacientes, registando a data, motivo (inativação/bloqueio) e responsável.
7a.2. O sistema preserva integralmente o histórico de atendimentos realizados.
7a.3. O sistema despoleta notificações aos pacientes afetados e à administração da clínica para avaliação da continuidade do cuidado.
7a.4. O fluxo retorna ao passo 8.
7b. O utilizador alterado é um Psicólogo/Pesquisador responsável por pesquisas (RN-053):
7b.1. O sistema cancela ou permite transferir pesquisas nos estados Rascunho ou Submetida.
7b.2. O sistema altera o estado de pesquisas Aprovadas ou Em Coleta para Suspensa.
7b.3. O sistema notifica o Comitê de Ética sobre a alteração de responsabilidade.
7b.4. O fluxo retorna ao passo 8.
Fluxos de Exceção:
3a. Tentativa de alterar o status da própria conta de Administrador:
3a.1. O sistema impede a auto-inativação/bloqueio da conta administrativa principal.
3a.2. O sistema exibe mensagem de erro: "Não é permitido alterar o status do próprio utilizador autenticado."
3a.3. O caso de uso é encerrado.
4a. Justificativa não informada:
4a.1. O sistema assinala o campo como obrigatório e impede o salvamento.
4a.2. O Administrador fornece a justificativa e o fluxo retorna ao passo 5.
Regras de Negócio: RN-009, RN-010, RN-012, RN-016, RN-017, RN-018, RN-031, RN-053.
Requisitos Funcionais: RF-007, RF-016, RF-018, RF-033, RF-070.
Requisitos Não Funcionais: RNF-004, RNF-009, RNF-010, RNF-012.
Rastreabilidade: HU08, UC01, UC06, UC15.
UC09 — Gerir Permissões do Sistema
Identificador: UC09
Nome: Gerir Permissões do Sistema
Objetivo: Permitir o mapeamento granular de permissões associadas a funcionalidades específicas do sistema para cada perfil de utilizador.
Atores: Administrador.
Pré-condições: O Administrador deve estar autenticado.
Pós-condições: Matriz de controlo de acessos atualizada.
Fluxo Principal:
O Administrador acede ao painel de permissões granulares.
O sistema exibe a matriz de casos de uso/funcionalidades versus perfis.
O Administrador altera o acesso (concede ou revoga) de uma funcionalidade para um perfil.
O sistema valida a integridade estrutural das permissões e grava.
O sistema regista a alteração no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-005, RN-006, RN-007.
Requisitos Funcionais: RF-014, RF-015.
Requisitos Não Funcionais: RNF-009, RNF-010.
Rastreabilidade: UC07, UC10.
UC10 — Consultar Logs de Auditoria
Identificador: UC10
Nome: Consultar Logs de Auditoria
Objetivo: Permitir que o Administrador consulte, filtre e exporte os registos imutáveis de eventos de segurança e operações sensíveis do sistema.
Atores: Administrador.
Pré-condições: O Administrador deve estar autenticado.
Pós-condições: Logs consultados com salvaguarda da imutabilidade dos registos.
Fluxo Principal:
O Administrador acede ao painel de auditoria.
O Administrador define filtros de busca (período, tipo de evento, ID de utilizador ou severidade).
O sistema consulta a base de dados de auditoria e exibe os resultados paginados.
O Administrador seleciona a opção de exportar relatório (PDF/CSV), se necessário.
O sistema regista a própria consulta de auditoria no log.
O caso de uso é encerrado.
Regras de Negócio: RN-013, RN-015, RN-034.
Requisitos Funcionais: RF-017, RF-019.
Requisitos Não Funcionais: RNF-004, RNF-010, RNF-011.
Rastreabilidade: UC06, UC08.
UC11 — Gerir Credenciais e Dispositivos
Identificador: UC11
Nome: Gerir Credenciais e Dispositivos
Objetivo: Permitir que o utilizador gerencie os seus fatores de autenticação adicionais (como aplicativos de autenticação 2FA) e dispositivos confiáveis.
Atores: Administrador, Psicólogo, Atendente, Paciente, Responsável Legal.
Pré-condições: O utilizador deve estar autenticado.
Pós-condições: Configurações de 2FA ou dispositivos confiáveis atualizados.
Fluxo Principal:
O utilizador acede às definições de segurança da conta.
O sistema exibe o status do 2FA e os dispositivos associados.
O utilizador opta por configurar ou redefinir o segundo fator (geração de QR Code).
O utilizador insere o código de confirmação gerado pelo aplicativo autenticador.
O sistema valida o código, ativa o 2FA e regista a alteração no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-010, RN-011.
Requisitos Funcionais: RF-003, RF-008.
Requisitos Não Funcionais: RNF-001, RNF-002.
Rastreabilidade: UC01.
UC12 — Cadastrar Atendente
Identificador: UC12
Nome: Cadastrar Atendente
Objetivo: Permitir que o Administrador registe um novo operador com o perfil de Atendente no sistema.
Atores: Administrador.
Pré-condições: O Administrador deve estar autenticado.
Pós-condições: Nova conta de atendente criada com status ativo e senha provisória enviada.
Fluxo Principal:
O Administrador seleciona a opção de cadastrar atendente.
O sistema solicita os dados pessoais, e-mail e contacto telefónico.
O Administrador preenche e submete os dados.
O sistema valida a unicidade do e-mail e CPF.
O sistema cria a conta com perfil "Atendente", gera senha provisória e envia por e-mail.
O sistema regista a ação no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-002, RN-004, RN-008.
Requisitos Funcionais: RF-020, RF-021.
Requisitos Não Funcionais: RNF-009, RNF-010.
Rastreabilidade: UC06, UC13.
UC13 — Consultar Dados Administrativos Globais
Identificador: UC13
Nome: Consultar Dados Administrativos Globais
Objetivo: Permitir a visualização de métricas consolidadas, relatórios operacionais e indicadores globais do sistema.
Atores: Administrador, Atendente (com restrições).
Pré-condições: O ator deve estar autenticado com perfil administrativo ou de atendimento.
Pós-condições: Painel de indicadores globais exibido com segurança.
Fluxo Principal:
O ator acede ao dashboard administrativo principal.
O sistema recolhe métricas consolidadas de utilizadores ativos, agendamentos e status da clínica.
O sistema exibe o painel gráfico com os dados agregados.
O caso de uso é encerrado.
Regras de Negócio: RN-015, RN-034.
Requisitos Funcionais: RF-022, RF-023.
Requisitos Não Funcionais: RNF-019, RNF-023.
Rastreabilidade: UC12, UC06.
UC14 — Criar Vínculo
Identificador: UC14Nome: Criar Vínculo (Paciente–Psicólogo)
Objetivo: Registrar o vínculo terapêutico entre um paciente e um psicólogo, garantindo o controle de acesso às informações clínicas.
Atores: Administrador, Psicólogo (autorizado), Atendente (conforme permissão).
Pré-condições:
O paciente e o psicólogo devem estar previamente cadastrados.
O psicólogo deve estar com CRP válido e conta Ativa.
Pós-condições:
O vínculo é criado e ativo.
O psicólogo passa a ter acesso autorizado aos dados do paciente.
O histórico é registrado no log de auditoria.
Fluxo Principal:
O ator acessa o cadastro do paciente.
O ator seleciona a opção "Criar Vínculo".
O sistema exibe os psicólogos disponíveis.
O ator seleciona o psicólogo.
O ator insere o motivo do vínculo e a data de início.
O sistema registra a data de início, o motivo e o responsável pela criação.
O sistema vincula o paciente ao psicólogo, aplicando as regras de restrição de acesso.
O caso de uso é encerrado.
Fluxos Alternativos:
4a. O paciente já possui vínculo com este psicólogo:4a.1. O sistema informa que o vínculo já existe e encerra o caso.
Fluxos de Exceção:
3a. Nenhum psicólogo ativo disponível:3a.1. O sistema exibe mensagem informando a ausência de profissionais.3a.2. O caso de uso é encerrado.
Regras de Negócio: RN-022, RN-028, RN-030.Requisitos Funcionais: RF-027, RF-030.Requisitos Não Funcionais: RNF-013, RNF-014.Rastreabilidade: UC15, UC16.
UC15 — Encerrar Vínculo (Paciente–Psicólogo)
Identificador: UC15
Nome: Encerrar Vínculo (Paciente–Psicólogo)
Objetivo: Permitir o registo formal do encerramento do vínculo terapêutico entre um paciente e um psicólogo, garantindo a preservação integral do histórico de atendimentos e a rastreabilidade da operação.
Atores: Administrador, Psicólogo, Atendente (conforme permissão).
Pré-condições:
O ator deve estar autenticado e com permissão para gerir vínculos.
Deve existir um vínculo ativo entre o paciente e o psicólogo selecionados.
O status do vínculo é alterado para "Encerrado", registando data de fim, motivo e responsável.
Pós-condições:
O psicólogo perde o acesso ativo a novas consultas e atendimentos para o paciente.
O histórico de atendimentos e prontuários passados permanece preservado e imutável para fins legais e de auditoria.
A operação é gravada no log de auditoria.
Fluxo Principal:
O ator acede ao perfil do paciente ou à lista de vínculos do psicólogo.
O sistema exibe os vínculos ativos associados.
O ator seleciona o vínculo pretendido e escolhe a opção "Encerrar Vínculo".
O sistema solicita a confirmação, a data de encerramento e o motivo do encerramento.
O ator introduz as informações solicitadas e confirma a operação.
O sistema valida se os dados obrigatórios foram preenchidos.
O sistema atualiza o estado do vínculo na base de dados, guardando o responsável pela ação.
O sistema revoga as permissões de acesso ativo do psicólogo aos novos agendamentos do paciente.
O sistema preserva o histórico completo de atendimentos já realizados durante a vigência do vínculo.
O sistema regista a alteração no log de auditoria.
O sistema exibe mensagem de confirmação do encerramento.
O caso de uso é encerrado.
Fluxos Alternativos:
3a. Encerramento automático provocado por Inativação/Bloqueio do Psicólogo (em ligação com o UC08):
3a.1. O sistema deteta a alteração de status do psicólogo para Inativo ou Bloqueado.
3a.2. O sistema encerra automaticamente todos os vínculos ativos do profissional.
3a.3. O sistema regista o motivo como "Inativação/Bloqueio Administrativo do Profissional".
3a.4. O sistema despoleta a notificação aos pacientes e assinala a necessidade de avaliação da continuidade do cuidado pela clínica.
3a.5. O fluxo salta para o passo 8.
Fluxos de Exceção:
5a. Motivo de encerramento não informado:
5a.1. O sistema destaca o campo do motivo como obrigatório.
5a.2. O sistema impede a conclusão do encerramento até ao preenchimento do campo.
6a. Vínculo já se encontra encerrado ou inexistente:
6a.1. O sistema exibe mensagem informando que o vínculo selecionado já não se encontra ativo.
6a.2. O caso de uso é encerrado.
Regras de Negócio: RN-017, RN-018, RN-028, RN-029, RN-031.
Requisitos Funcionais: RF-028, RF-033, RF-055.
Requisitos Não Funcionais: RNF-012, RNF-013, RNF-015.
Rastreabilidade: HU15, UC06, UC08, UC14.
UC16 — Consultar Perfil e Dados Cadastrais
Identificador: UC16
Nome: Consultar Perfil e Dados Cadastrais
Objetivo: Permitir que o utilizador visualize e edite as suas informações cadastrais básicas, respeitando as restrições do seu perfil.
Atores: Administrador, Psicólogo, Atendente, Paciente, Responsável Legal.
Pré-condições: O utilizador deve estar autenticado.
Pós-condições: Dados cadastrais exibidos ou atualizados com registo em auditoria.
Fluxo Principal:
O utilizador acede à opção "Meu Perfil".
O sistema recupera e exibe as informações cadastrais associadas à conta.
O utilizador edita os campos permitidos (ex: telefone, morada) e clica em "Salvar".
O sistema valida os dados e atualiza a base de dados.
O sistema regista a alteração no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-002, RN-004, RN-020.
Requisitos Funcionais: RF-024, RF-025.
Requisitos Não Funcionais: RNF-009, RNF-010.
Rastreabilidade: UC01, UC14.
UC17 — Cadastrar Psicólogo (com validação de CRP)
Identificador: UC17
Nome: Cadastrar Psicólogo (com validação de CRP)
Objetivo: Permitir que o Administrador cadastre um psicólogo na plataforma, integrando a validação obrigatória do número de inscrição no CRP junto à base externa do Conselho Federal de Psicologia.
Atores: Administrador.
Pré-condições: O Administrador deve estar autenticado.
Pós-condições: Conta de psicólogo criada e validada (ou marcada para revisão se a API externa falhar).
Fluxo Principal:
O Administrador acede à gestão de profissionais e seleciona "Novo Psicólogo".
O Administrador introduz os dados pessoais, e-mail e o número de registo no CRP.
O sistema envia a requisição de validação para a API externa do CFP.
A API do CFP retorna o status regular do profissional.
O sistema cria a conta com status "Ativo" e perfil "Psicólogo", gerando senha provisória.
O sistema regista a operação no log de auditoria e encerra o caso de uso.
Fluxos de Exceção:
4a. CRP irregular ou inexistente na base externa:
4a.1. O sistema impede a ativação imediata e define o status como "Inativo/Pendente de Validação".
4a.2. O Administrador é notificado da divergência.
Regras de Negócio: RN-002, RN-003, RN-021.
Requisitos Funcionais: RF-026, RF-028.
Requisitos Não Funcionais: RNF-010, RNF-028.
Rastreabilidade: UC06, UC18, UC19.
UC18 — Atualizar Perfil Profissional e Área de Atuação
Identificador: UC18
Nome: Atualizar Perfil Profissional e Área de Atuação
Objetivo: Permitir que o psicólogo atualize as suas especialidades, abordagem teórica, biografia e informações de atendimento exibidas aos pacientes.
Atores: Psicólogo, Administrador.
Pré-condições: O psicólogo deve estar autenticado e com conta ativa.
Pós-condições: Perfil profissional atualizado na plataforma.
Fluxo Principal:
O psicólogo acede às configurações do seu perfil profissional.
O sistema exibe os dados atuais de especialidade, mini biografia e áreas de atuação.
O psicólogo altera as informações desejadas e confirma a gravação.
O sistema valida os campos e atualiza o registo.
O sistema regista a ação no log de auditoria e encerra o caso de uso.
Regras de Negócio: RN-002, RN-021.
Requisitos Funcionais: RF-028, RF-029.
Requisitos Não Funcionais: RNF-010.
Rastreabilidade: UC17, UC19.
UC19 — Gerir Disponibilidade Profissional
Identificador: UC19
Nome: Gerir Disponibilidade Profissional
Objetivo: Permitir que o psicólogo defina os seus dias e horários de atendimento recorrentes e exceções de agenda.
Atores: Psicólogo.
Pré-condições: O psicólogo deve estar autenticado e com conta ativa.
Pós-condições: Grade de horários e disponibilidades atualizada para agendamentos.
Fluxo Principal:
O psicólogo acede ao módulo de gestão de agenda/disponibilidade.
O sistema exibe o calendário semanal de horários configurados.
O psicólogo define ou ajusta os blocos de horário disponíveis para marcação.
O sistema valida se há conflito com consultas já agendadas e salva a nova grade.
O sistema regista a alteração e encerra o caso de uso.
Regras de Negócio: RN-037, RN-038.
Requisitos Funcionais: RF-036, RF-037.
Requisitos Não Funcionais: RNF-019.
Rastreabilidade: UC20, UC22.
UC20 — Agendar Consulta
Identificador: UC20Nome: Agendar Consulta
Objetivo: Permitir que o paciente (ou atendente em seu nome) agende uma consulta, respeitando a disponibilidade do psicólogo e evitando conflitos de horário.
Atores: Paciente, Atendente.
Pré-condições:
O psicólogo deve ter disponibilidade cadastrada.
O paciente deve estar cadastrado.
Pós-condições:
O agendamento é criado com status "Pendente" (ou "Confirmado", se aplicável).
A agenda do psicólogo é reservada naquele horário.
Fluxo Principal:
O ator seleciona o psicólogo e a data desejada.
O sistema exibe os horários disponíveis com base na agenda e disponibilidade do profissional.
O ator seleciona o horário.
O sistema verifica se há sobreposição de agendamentos (conflito) para o psicólogo naquele horário.
O sistema registra o agendamento com status "Pendente".
O sistema notifica o psicólogo sobre a nova solicitação.
O caso de uso é encerrado.
Fluxos Alternativos:
3a. O ator precisa remarcar uma consulta existente:3a.1. O ator seleciona a consulta anterior e escolhe "Remarcar" (aciona UC24).
Fluxos de Exceção:
2a. Nenhum horário disponível:2a.1. O sistema exibe mensagem e sugere novas datas.2a.2. O caso de uso é encerrado.
4a. Conflito de horário detectado (condição de corrida):4a.1. O sistema bloqueia o agendamento e informa que o horário foi ocupado.4a.2. O sistema retorna ao passo 2.
Regras de Negócio: RN-037.Requisitos Funcionais: RF-038, RF-040.Requisitos Não Funcionais: RNF-019.Rastreabilidade: UC21, UC22, UC24, UC26.
UC21 — Confirmar Agendamento
Identificador: UC21
Nome: Confirmar Agendamento
Objetivo: Permitir que o Psicólogo ou o Atendente confirme uma consulta agendada que esteja com status "Pendente", validando a ausência de conflitos de horário e atualizando a situação na agenda.
Atores: Psicólogo, Atendente.
Pré-condições:
O ator deve estar autenticado e com permissão para gerir a agenda.
Deve existir um agendamento no estado "Pendente" registado no sistema.
O status do agendamento é alterado para "Confirmado".
Pré-condições:
O usuário deve estar autenticado na plataforma.
O usuário deve possuir permissão para gerenciar suas credenciais.
A senha do usuário é atualizada de forma segura (armazenada com hash e salt).
Pós-condições:
O status de "senha provisória" (se houver) é desativado.
A alteração é registrada no log de auditoria.
Sessões ativas em outros dispositivos podem ser invalidadas por segurança.
O horário fica reservado de forma definitiva no calendário do Psicólogo.
O paciente é notificado sobre a confirmação da consulta.
A alteração é registrada no log de auditoria.
Fluxo Principal:
O ator acede ao módulo de agenda e visualiza a lista de agendamentos pendentes.
O ator seleciona o agendamento desejado e escolhe a opção "Confirmar Agendamento".
O sistema executa a verificação automática de conflito de horário para o Psicólogo no período da consulta.
O sistema confirma que o horário está livre de sobreposições com outros agendamentos "Confirmados" ou "Pendentes".
O sistema atualiza o status do agendamento para "Confirmado".
O sistema aciona o serviço de notificação para enviar a confirmação ao paciente.
O sistema regista a confirmação e o responsável pela ação no log de auditoria.
O sistema exibe mensagem de sucesso e atualiza a exibição da agenda.
O caso de uso é encerrado.
Fluxos Alternativos:
2a. Confirmação decorrente de remarcação de consulta (em ligação com o UC24):
2a.1. O agendamento pendente é oriundo de um processo de remarcação (RN-042).
2a.2. O sistema valida que o agendamento original anterior permanece preservado no histórico.
2a.3. O fluxo prossegue a partir do passo 3.
Fluxos de Exceção:
3a. Conflito de horário detetado:
3a.1. O sistema identifica que o Psicólogo possui outro agendamento já confirmado ou pendente sobreposto no mesmo intervalo de tempo (RN-037).
3a.2. O sistema bloqueia a confirmação e exibe uma mensagem de alerta de conflito.
3a.3. O sistema sugere ao ator a remarcação da consulta ou a rejeição do agendamento pendente.
3a.4. O caso de uso é encerrado sem alterar o status.
6a. Falha no envio da notificação ao paciente:
6a.1. O sistema deteta indisponibilidade no serviço de e-mail/notificação.
6a.2. O sistema armazena a notificação na fila de reenvio pendente (RNF-031).
6a.3. O sistema mantém o agendamento como "Confirmado" e exibe aviso de que a notificação será enviada assim que o serviço for restabelecido.
Regras de Negócio: RN-016, RN-017, RN-037, RN-042.
Requisitos Funcionais: RF-039, RF-040, RF-045, RF-049.
Requisitos Não Funcionais: RNF-019, RNF-030, RNF-031.
Rastreabilidade: HU21, UC20, UC24.
UC22 — Consultar Agenda e Disponibilidades
Identificador: UC22
Nome: Consultar Agenda e Disponibilidades
Objetivo: Permitir que pacientes, psicólogos e atendentes consultem a agenda de consultas e os horários livres disponíveis para marcação.
Atores: Paciente, Psicólogo, Atendente, Responsável Legal.
Pré-condições: O ator deve estar autenticado.
Pós-condições: Visualização da agenda filtrada por profissional ou paciente.
Fluxo Principal:
O ator acede ao módulo de agenda.
O ator seleciona o psicólogo e o período desejado (dia/semana/mês).
O sistema consulta os agendamentos e os blocos de disponibilidade cadastrados.
O sistema exibe a visualização calendarizada com os status correspondentes (livre, confirmado, pendente).
O caso de uso é encerrado.
Regras de Negócio: RN-037, RN-038.
Requisitos Funcionais: RF-039, RF-043.
Requisitos Não Funcionais: RNF-019.
Rastreabilidade: UC20, UC21.
UC23 — Cancelar Agendamento
Identificador: UC23
Nome: Cancelar Agendamento
Objetivo: Permitir que o paciente, psicólogo ou atendente cancele uma consulta previamente agendada ou confirmada, respeitando os prazos e as políticas de cancelamento da clínica e registando a operação para auditoria.
Atores: Paciente, Psicólogo, Atendente.
Pré-condições:
O ator deve estar autenticado e com permissão para gerir a agenda.
Deve existir um agendamento válido e ativo (Pendente ou Confirmado).
Pós-condições:
O status do agendamento é alterado para "Cancelado".
O horário anteriormente reservado é libertado na agenda do psicólogo.
O registo do cancelamento, motivo e responsável são salvos no log de auditoria.
O sistema envia uma notificação automática às partes envolvidas.
Fluxo Principal:
O ator acede ao módulo de agenda e seleciona a consulta pretendida.
O ator escolhe a opção "Cancelar Agendamento".
O sistema valida se o prazo de cancelamento respeita a política configurada pela clínica (RN-041 / RN-043).
O sistema solicita o motivo obrigatório do cancelamento.
O ator introduz o motivo e confirma a operação.
O sistema atualiza o status do agendamento na base de dados para "Cancelado".
O sistema liberta o bloco de horário correspondente na agenda do psicólogo.
O sistema aciona o serviço de notificação para informar a outra parte interessada.
O sistema regista a operação e o responsável no log de auditoria.
O sistema exibe a confirmação do cancelamento e o caso de uso é encerrado.
Fluxos Alternativos:
3a. Cancelamento fora do prazo estipulado pela política da clínica:
3a.1. O sistema deteta que o pedido de cancelamento viola o prazo mínimo de antecedência configurado (RN-041).
3a.2. O sistema emite um alerta informando sobre a incidência de penalização ou taxa de ausência tardia.
3a.3. O ator confirma o ciente da penalização e o fluxo prossegue a partir do passo 4.
Fluxos de Exceção:
4a. Motivo de cancelamento não informado:
4a.1. O sistema destaca o campo do motivo como obrigatório e impede a conclusão.
4a.2. O ator preenche o motivo e o fluxo retorna ao passo 5.
6a. Consulta já se encontra cancelada ou realizada:
6a.1. O sistema exibe mensagem informando que o agendamento já não pode ser modificado.
6a.2. O caso de uso é encerrado.
Regras de Negócio: RN-017, RN-041, RN-042
Requisitos Funcionais: RF-041, RF-042, RF-045
Requisitos Não Funcionais: RNF-019, RNF-030
Rastreabilidade: HU20, UC20, UC21, UC27
UC24 — Remarcar Consulta
Identificador: UC24
Nome: Remarcar Consulta
Objetivo: Permitir a remarcação de uma consulta previamente confirmada, gerando um novo registo de agendamento, preservando o histórico anterior e impondo os limites configurados pela clínica.
Atores: Paciente, Psicólogo, Atendente.
Pré-condições:
O ator deve estar autenticado e com permissão para gerir a agenda.
Deve existir um agendamento válido e confirmado elegível para remarcação.
Pós-condições:
Um novo registo de agendamento é criado com status "Pendente" para a nova data/horário.
O agendamento original é mantido e registado no histórico de agendamentos.
A agenda do psicólogo é verificada quanto à ausência de conflitos.
Fluxo Principal:
O ator acede aos detalhes de uma consulta agendada e seleciona a opção "Remarcar".
O sistema verifica se o número de remarcações efetuadas para este atendimento já atingiu o limite máximo permitido pela clínica (RN-043).
O sistema apresenta os horários disponíveis na agenda do psicólogo.
O ator seleciona a nova data e o novo horário pretendidos.
O sistema executa a validação de sobreposição de horários (conflito) para o novo período.
O sistema cria um novo registo de agendamento com status "Pendente", associando-o ao histórico do agendamento anterior.
O sistema notifica o psicólogo ou o paciente sobre a nova solicitação pendente de confirmação.
O sistema regista a operação no log de auditoria.
O caso de uso é encerrado.
Fluxos Alternativos:
2a. Limite máximo de remarcações atingido:
2a.1. O sistema bloqueia a remarcação direta e informa que o limite máximo configurado foi alcançado.
2a.2. O sistema orienta o ator a contactar o atendimento administrativo da clínica para excepções.
2a.3. O caso de uso é encerrado.
Fluxos de Exceção:
5a. Conflito de horário detetado no novo período:
5a.1. O sistema deteta sobreposição de agenda e impede o registo.
5a.2. O sistema exibe um alerta e solicita a escolha de outro horário (retorna ao passo 3).
Regras de Negócio: RN-037, RN-042, RN-043.
Requisitos Funcionais: RF-038, RF-040, RF-045, RF-051.
Requisitos Não Funcionais: RNF-019, RNF-021.
Rastreabilidade: HU20, UC20, UC21.
UC25 — Registar Atendimento
Identificador: UC25
Nome: Registar Atendimento
Objetivo: Permitir que o psicólogo responsável elabore e salve o registo conceitual e o histórico de um atendimento realizado, garantindo a vinculação estrita com um agendamento confirmado e o respeito ao sigilo profissional.
Atores: Psicólogo.
Pré-condições:
O psicólogo deve estar autenticado e com conta ativa.
Deve existir um agendamento prévio com status "Confirmado" entre o psicólogo e o paciente.
Pós-condições:
O registo conceitual do atendimento é gravado e associado ao paciente e ao psicólogo.
O histórico clínico fica atualizado, mantendo a imutabilidade e a proteção de acesso.
Fluxo Principal:
O psicólogo acede à sua agenda ou ao perfil do paciente vinculado e seleciona a opção "Registar Atendimento" correspondente à consulta realizada.
O sistema valida se o agendamento associado está confirmado e se o psicólogo possui vínculo ativo com o paciente.
O psicólogo preenche os dados do atendimento (resumo conceitual, evolução e data da sessão).
O sistema valida se a data do atendimento respeita a regra de não permitir datas futuras (RN-045).
O sistema grava o registo do atendimento, associando-o ao respetivo agendamento, paciente e psicólogo.
O sistema regista a ação no log de auditoria, garantindo a rastreabilidade.
O sistema exibe mensagem de sucesso e conclui o registo.
O caso de uso é encerrado.
Fluxos de Exceção:
2a. Ausência de vínculo válido ou permissão negada:
2a.1. O sistema bloqueia o acesso e exibe uma mensagem de restrição por falta de vínculo ativo.
2a.2. O caso de uso é encerrado.
4a. Tentativa de registar com data futura:
4a.1. O sistema impede o salvamento e indica que a data do atendimento não pode ser posterior à data atual (RN-045).
4a.2. O psicólogo corrige a data e o fluxo retorna ao passo 3.
Regras de Negócio: RN-022, RN-034, RN-044, RN-045.
Requisitos Funcionais: RF-046, RF-047, RF-048, RF-054.
Requisitos Não Funcionais: RNF-012, RNF-013, RNF-015, RNF-038.
Rastreabilidade: HU28, UC14, UC20.
UC26 — Registar Ausência / Não Comparecimento
Identificador: UC26
Nome: Registar Ausência / Não Comparecimento
Objetivo: Permitir que o psicólogo ou o atendente registe oficialmente o não comparecimento de um paciente a uma consulta confirmada, atualizando o status do agendamento e acionando as políticas administrativas e financeiras aplicáveis.
Atores: Psicólogo, Atendente.
Pré-condições:
O ator deve estar autenticado com permissão de gestão de agenda.
Deve existir um agendamento com status "Confirmado" cuja data e horário já tenham ocorrido.
Pós-condições:
O status do agendamento é alterado para "Não Compareceu" (No-Show).
O registo de ausência fica associado ao histórico do paciente.
A operação é registada de forma imutável no log de auditoria.
Fluxo Principal:
O ator acede à agenda e localiza o agendamento confirmado correspondente ao horário já transcorrido.
O ator seleciona a opção "Registar Ausência".
O sistema valida se o horário da consulta já expirou (RN-045).
O sistema altera o status do agendamento para "Não Compareceu".
O sistema regista o evento no histórico do paciente e contabiliza para efeitos das políticas da clínica.
O sistema aciona o envio de uma mensagem de acompanhamento ao paciente.
O sistema grava a ação e o responsável no log de auditoria.
O sistema exibe mensagem de confirmação e o caso de uso é encerrado.
Fluxos Alternativos:
2a. Registo automático de ausência por tolerância de tempo excedida:
2a.1. O sistema atinge o limite de tolerância pós-horário agendado sem confirmação de presença.
2a.2. O sistema altera automaticamente o status para "Não Compareceu" e prossegue para o passo 5.
Fluxos de Exceção:
3a. Tentativa de registar ausência em consulta futura:
3a.1. O sistema impede a alteração e exibe mensagem de erro informando que não é possível registar ausência antes da ocorrência do horário agendado (RN-045).
3a.2. O caso de uso é encerrado.
Regras de Negócio: RN-017, RN-040, RN-044, RN-045
Requisitos Funcionais: RF-044, RF-045, RF-050
Requisitos Não Funcionais: RNF-012, RNF-015
Rastreabilidade: HU20, UC21, UC25, UC27
UC27 — Configurar Políticas de Cancelamento e Horários
Identificador: UC27
Nome: Configurar Políticas de Cancelamento e Horários
Objetivo: Permitir que o Administrador configure as regras globais da clínica relativas a prazos mínimos de cancelamento, tolerâncias de atraso e limites de remarcação.
Atores: Administrador.
Pré-condições:O Administrador deve estar autenticado na plataforma.
Pós-condições:
Parâmetros de política de atendimento atualizados no sistema.
A alteração é registada no log de auditoria.
Fluxo Principal:
O Administrador acede ao painel de configurações globais da clínica.
O sistema exibe os parâmetros vigentes (antecedência mínima de cancelamento em horas, tolerância de atraso e limite de remarcações).
O Administrador altera os valores desejados e clica em "Salvar Configurações".
O sistema valida se os valores inseridos são numéricos e positivos.
O sistema grava os novos parâmetros na base de dados.
O sistema regista a alteração e o responsável no log de auditoria.
O sistema exibe mensagem de confirmação e o caso de uso é encerrado.
Fluxos de Exceção:
4a. Valores inválidos ou negativos inseridos:
4a.1. O sistema bloqueia a gravação e destaca os campos com valores fora do intervalo permitido.
4a.2. O Administrador corrige os valores e o fluxo retorna ao passo 3.
Regras de Negócio: RN-041, RN-043
Requisitos Funcionais: RF-051, RF-052
Requisitos Não Funcionais: RNF-010
Rastreabilidade: UC23, UC24, UC26
UC28 — Consultar Histórico de Atendimentos
Identificador: UC28
Nome: Consultar Histórico de Atendimentos
Objetivo: Permitir a consulta ao histórico cronológico de atendimentos realizados e registos clínicos associados, respeitando rigorosamente os limites de acesso baseados em vínculos ativos e sigilo profissional.
Atores: Psicólogo, Paciente, Responsável Legal (mediado).
Pré-condições:
O ator deve estar autenticado na plataforma.
Deve existir um vínculo ativo (para Psicólogo) ou titularidade/representação legal válida (para Paciente/Responsável).
Pós-condições:
O histórico de atendimentos é apresentado conforme o nível de acesso permitido ao perfil.
O acesso aos dados sensíveis é registado no log de auditoria.
Fluxo Principal:
O ator acede ao perfil do paciente e seleciona "Histórico de Atendimentos".
O sistema valida se o ator possui permissão e vínculo ativo válido com o paciente (RN-022).
O sistema recupera a lista cronológica de sessões realizadas.
O sistema filtra o nível de detalhe exibido conforme o perfil (exibindo resumos conceituais ao psicólogo vinculado e apenas datas/status ao paciente).
O sistema exibe o histórico na tela.
O sistema regista a visualização no log de auditoria de operações sensíveis.
O caso de uso é encerrado.
Fluxos Alternativos:
2a. Psicólogo com vínculo encerrado tentando consultar histórico:
2a.1. O sistema bloqueia a visualização de novos detalhes clínicos e permite apenas a consulta de auditoria caso autorizado administrativamente.
2a.2. O caso de uso é encerrado.
Fluxos de Exceção:
2b. Utilizador sem vínculo ou permissão de acesso:
2b.1. O sistema nega o acesso, exibe alerta de segurança e regista a tentativa no log.
2b.2. O caso de uso é encerrado.
Regras de Negócio: RN-022, RN-025, RN-034
Requisitos Funcionais: RF-053, RF-054
Requisitos Não Funcionais: RNF-010, RNF-015, RNF-016
Rastreabilidade: UC14, UC15, UC25, UC30
UC29 — Solicitar Acesso ao Prontuário
Identificador: UC29Nome: Solicitar Acesso ao Prontuário
Objetivo: Permitir que o responsável legal de um paciente menor de 18 anos solicite ao psicólogo responsável a entrega mediada do prontuário psicológico.
Atores: Responsável Legal.
Pré-condições:
O responsável legal deve estar autenticado e vinculado ao paciente menor.
O paciente deve ter vínculo ativo (ou histórico) com o psicólogo.
Pós-condições:
A solicitação é registrada no sistema.
O psicólogo responsável é notificado.
A operação é registrada em log de auditoria.
Fluxo Principal:
O responsável legal acessa o painel do paciente.
O responsável seleciona "Solicitar Acesso ao Prontuário".
O sistema verifica se o solicitante possui representação legal válida.
O sistema registra a solicitação com data e hora.
O sistema encaminha a solicitação ao psicólogo responsável.
O sistema exibe mensagem de confirmação e o status "Aguardando avaliação do psicólogo".
O caso de uso é encerrado.
Fluxos Alternativos:
2a. O responsável já possui uma solicitação em andamento:2a.1. O sistema informa o status atual da solicitação e encerra o caso.
Fluxos de Exceção:
3a. Representação legal inválida ou vencida (ex.: paciente já completou 18 anos):3a.1. O sistema nega a solicitação com base na cessação da representação legal.3a.2. O caso de uso é encerrado.
Regras de Negócio: RN-024, RN-026, RN-032, RN-035.Requisitos Funcionais: RF-056, RF-059.Requisitos Não Funcionais: RNF-015.Rastreabilidade: UC30, UC31, UC32.
UC30 — Entregar Prontuário (Mediada)
Identificador: UC30
Nome: Entregar Prontuário (Mediada)
Objetivo: Permitir que o psicólogo responsável efetue a entrega mediada de cópias do prontuário psicológico ao responsável legal autorizado (ou paciente maior), gerando documentação adequada e registando a auditoria da operação.
Atores: Psicólogo.
Pré-condições:
O psicólogo deve estar autenticado e existir uma solicitação de acesso ao prontuário pendente (submetida via UC29).
O solicitante deve possuir representação legal válida ou ser o próprio titular maior de idade.
Pós-condições:
O prontuário é disponibilizado de forma mediada (via PDF ou visualização controlada).
A operação de entrega é registada detalhadamente no histórico de auditoria e no prontuário.
Fluxo Principal:
O psicólogo acede ao painel de solicitações de prontuários pendentes.
O sistema exibe os detalhes da solicitação feita pelo responsável legal ou paciente.
O psicólogo valida os fundamentos da solicitação e seleciona a opção "Efetuar Entrega Mediada".
O sistema gera ou compila o conteúdo permitido do prontuário (excluindo o registo documental privativo do psicólogo, conforme RN-026).
O sistema gera a versão digital segura (PDF) ou libera o acesso restrito online.
O sistema regista a data, a hora, a identificação do destinatário e o conteúdo disponibilizado.
O sistema atualiza o status da solicitação para "Entregue".
O sistema grava o evento no log de auditoria de operações sensíveis.
O sistema exibe confirmação da conclusão da entrega.
O caso de uso é encerrado.
Fluxos Alternativos:
3a. Decisão de restrição de acesso ao prontuário:
3a.1. O psicólogo identifica fundamentos para restringir o acesso (ex: suspeita de abuso ou conflito grave de guarda, conforme RN-026).
3a.2. O psicólogo seleciona "Restringir Acesso" e preenche a justificativa obrigatória.
3a.3. O sistema regista a restrição e notifica o solicitante de acordo com as regras da clínica.
3a.4. O fluxo prossegue para o passo 8 (registando a recusa fundamentada).
Regras de Negócio: RN-026, RN-034, RN-035.
Requisitos Funcionais: RF-057, RF-058, RF-059.
Requisitos Não Funcionais: RNF-010, RNF-015, RNF-016.
Rastreabilidade: HU28, UC29.
UC31 — Registar Restrição de Acesso ao Prontuário
Identificador: UC31
Nome: Registar Restrição de Acesso ao Prontuário
Objetivo: Permitir que o psicólogo responsável registe formalmente a fundamentação técnica para restringir a entrega de cópias do prontuário a terceiros ou responsáveis legais, salvaguardando o melhor interesse do paciente.
Atores: Psicólogo.
Pré-condições: Existir uma solicitação de acesso pendente (UC29) e fundamentos clínicos/éticos para a restrição.
Pós-condições: A restrição é registrada no prontuário e a recusa fundamentada é comunicada.
Fluxo Principal:
O psicólogo analisa a solicitação de acesso ao prontuário feita por um responsável legal.
O psicólogo identifica riscos ou motivos éticos para restrição (ex: suspeita de conflito grave ou abuso - RN-026).
O psicólogo seleciona a opção "Restringir Acesso" e preenche a fundamentação técnica obrigatória.
O sistema grava o registo de restrição vinculado ao prontuário e atualiza o status da solicitação para "Recusada Fundamentadamente".
O sistema regista a operação no log de auditoria e notifica o solicitante com a justificativa permitida.
O caso de uso é encerrado.
Regras de Negócio: RN-026, RN-034, RN-035.
Requisitos Funcionais: RF-058, RF-060.
Requisitos Não Funcionais: RNF-010, RNF-015.
Rastreabilidade: UC29, UC30.
UC32 — Gerir Transição para Maioridade (Paciente)
Identificador: UC32
Nome: Gerir Transição para Maioridade (Paciente)
Objetivo: Tratar automaticamente a alteração de estatuto de um paciente que atinge os 18 anos, cessando a representação legal prévia e garantindo que o titular passe a deter o controlo exclusivo sobre o seu prontuário e dados.
Atores: Sistema (Automático), Administrador.
Pré-condições: O paciente atinge a data correspondente à maioridade civil (18 anos).
Pós-condições: A representação legal anterior é encerrada e o acesso exclusivo é transferido ao titular.
Fluxo Principal:
O sistema identifica diariamente os pacientes cuja data de nascimento completa 18 anos na data atual.
O sistema revoga automaticamente os privilégios de acesso do Responsável Legal sobre o perfil e prontuário do paciente.
O sistema envia uma notificação ao novo titular informando sobre a autonomia plena da conta e a necessidade de redefinição de credenciais de acesso exclusivo.
O sistema regista o evento de transição no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-024, RN-025.
Requisitos Funcionais: RF-056, RF-060.
Requisitos Não Funcionais: RNF-010, RNF-015.
Rastreabilidade: UC02, UC29.
UC33 — Encaminhar Solicitações de Terceiros
Identificador: UC33
Nome: Encaminhar Solicitações de Terceiros
Objetivo: Permitir que o atendente receba e reencaminhe solicitações formais de instituições externas ou terceiros para a avaliação da administração e equipa técnica.
Atores: Atendente, Administrador.
Pré-condições: O atendente deve estar autenticado.
Pós-condições: Solicitação registada e encaminhada ao setor responsável.
Fluxo Principal:
O atendente acede ao módulo de registo de pedidos externos.
O atendente insere os dados da solicitação do terceiro (ofício, instituição, assunto).
O sistema gera um número de protocolo e encaminha o pedido para o Administrador ou Psicólogo responsável.
O sistema regista a operação no log de auditoria e encerra o caso de uso.
Regras de Negócio: RN-015, RN-034.
Requisitos Funcionais: RF-055, RF-059.
Requisitos Não Funcionais: RNF-010.
Rastreabilidade: UC12, UC13.
UC34 — Criar e Configurar Pesquisa
Identificador: UC34Nome: Criar e Configurar Pesquisa
Objetivo: Permitir que o psicólogo (atuando como pesquisador) crie uma pesquisa, defina seus critérios de recorte e a prepare para submissão ao Comitê de Ética.
Atores: Pesquisador (Psicólogo).
Pré-condições: O usuário deve estar autenticado com perfil de pesquisador autorizado.
Pós-condições:
A pesquisa é criada no estado "Rascunho".
Os critérios de recorte e o escopo estão definidos.
Fluxo Principal:
O pesquisador acessa o módulo de Pesquisas e seleciona "Nova Pesquisa".
O sistema solicita título, descrição e objetivo da pesquisa.
O pesquisador define os critérios de recorte (ex.: faixa etária, área de atuação, período).
O pesquisador salva a pesquisa.
O sistema registra a pesquisa no estado "Rascunho".
O sistema vincula o pesquisador como responsável.
O caso de uso é encerrado.
Fluxos Alternativos:
6a. O pesquisador decide submeter imediatamente:6a.1. O sistema aciona o caso de uso UC35 (Submeter Pesquisa à Avaliação Ética).
Fluxos de Exceção:
4a. Dados obrigatórios não preenchidos:4a.1. O sistema bloqueia o salvamento e destaca os campos pendentes.4a.2. O caso de uso retorna ao passo 2.
Regras de Negócio: RN-047, RN-048, RN-051, RN-052.Requisitos Funcionais: RF-061, RF-062, RF-063.Requisitos Não Funcionais: RNF-023, RNF-025, RNF-026.Rastreabilidade: UC35, UC37, UC38.
UC35 — Submeter Pesquisa à Avaliação Ética
Identificador: UC35
Nome: Submeter Pesquisa à Avaliação Ética
Objetivo: Permitir que o pesquisador submeta formalmente uma pesquisa criada (em rascunho) para análise e aprovação do Comitê de Ética da instituição.
Atores: Pesquisador (Psicólogo).
Pré-condições: Existir uma pesquisa criada no estado "Rascunho" com todos os documentos e critérios preenchidos (UC34).
Pós-condições: A pesquisa passa para o estado "Submetida" e é encaminhada ao Comitê de Ética.
Fluxo Principal:
O pesquisador acede aos detalhes da pesquisa em estado "Rascunho".
O pesquisador seleciona a opção "Submeter para Avaliação Ética".
O sistema valida a integridade e o preenchimento obrigatório dos campos da pesquisa.
O sistema altera o estado da pesquisa para "Submetida".
O sistema notifica o Comitê de Ética sobre a nova subvenção pendente.
O sistema regista a subvenção no log de auditoria e encerra o caso de uso.
Regras de Negócio: RN-047, RN-048, RN-052.
Requisitos Funcionais: RF-062, RF-064.
Requisitos Não Funcionais: RNF-010, RNF-023.
Rastreabilidade: UC34, UC36.
UC36 — Avaliar Pesquisa (Comitê de Ética)
Identificador: UC36
Nome: Avaliar Pesquisa (Comitê de Ética)
Objetivo: Permitir que o Comitê de Ética analise, aprove, rejeite ou solicite ajustes em uma pesquisa submetida.
Atores: Comitê de Ética (utilizador com perfil administrativo/ético).
Pré-condições: Existir uma pesquisa no estado "Submetida" (UC35).
Pós-condições: A pesquisa transita para o estado "Aprovada", "Rejeitada" ou "Em Ajustes".
Fluxo Principal:
O membro do Comitê acede à fila de pesquisas submetidas.
O sistema exibe os detalhes e documentos da pesquisa.
O avaliador emite o parecer ético e seleciona a decisão ("Aprovar", "Reprovar" ou "Solicitar Ajustes"), inserindo justificativa.
O sistema atualiza o estado da pesquisa de acordo com a decisão (RN-052).
O sistema notifica o pesquisador responsável sobre o parecer emitido.
O sistema regista o parecer e o responsável no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-047, RN-048, RN-052.
Requisitos Funcionais: RF-064, RF-066.
Requisitos Não Funcionais: RNF-010, RNF-016.
Rastreabilidade: UC35, UC34.
UC37 — Registar Termo de Consentimento (TCLE)
Identificador: UC37
Nome: Registar Termo de Consentimento (TCLE)
Objetivo: Permitir o registo formal da aceitação do Termo de Consentimento Livre e Esclarecido (TCLE) pelo paciente para participação em pesquisas científicas no âmbito do LAPI.
Atores: Paciente, Responsável Legal.
Pré-condições: O paciente/responsável deve estar autenticado e a pesquisa deve estar em fase ativa de recolha (Aprovada).
Pós-condições: O aceite do TCLE é gravado com registo de data, hora e hash de validação.
Fluxo Principal:
O paciente acede aos detalhes de uma pesquisa disponível para participação.
O sistema exibe o documento completo do TCLE associado à pesquisa.
O paciente lê os termos e seleciona a opção "Aceitar e Concordar com o TCLE".
O sistema captura a data, a hora, o endereço IP e gera um registo imutável do consentimento.
O sistema atualiza o status de participação do paciente para "Consentido".
O sistema regista a operação no log de auditoria e encerra o caso de uso.
Regras de Negócio: RN-049, RN-050.
Requisitos Funcionais: RF-067, RF-068.
Requisitos Não Funcionais: RNF-010, RNF-015, RNF-027.
Rastreabilidade: UC34, UC38.
UC38 — Registar Opção de Não Participação (Opt-out)
Identificador: UC38
Nome: Registar Opção de Não Participação (Opt-out)
Objetivo: Permitir que o paciente manifeste a recusa ou revogue a qualquer momento o seu consentimento de participação em pesquisas científicas (Opt-out), garantindo que os seus dados sejam excluídos de futuras extrações do LAPI.
Atores: Paciente, Responsável Legal.
Pré-condições: O paciente deve possuir uma conta ativa e eventual consentimento prévio registado.
Pós-condições: A opção de Opt-out é ativada, bloqueando o uso dos dados do paciente em novas pesquisas.
Fluxo Principal:
O paciente acede às preferências de privacidade e partilha para pesquisa (LAPI).
O sistema exibe o status atual de consentimento.
O paciente seleciona a opção "Recusar Participação em Pesquisas (Opt-out)" e confirma.
O sistema atualiza a preferência de privacidade na base de dados, bloqueando qualquer futura anonimização ou inclusão dos dados do paciente em novos recortes de pesquisa.
O sistema regista a revogação no log de auditoria e exibe confirmação.
O caso de uso é encerrado.
Regras de Negócio: RN-049, RN-050, RN-051.
Requisitos Funcionais: RF-068, RF-069.
Requisitos Não Funcionais: RNF-010, RNF-015, RNF-027.
Rastreabilidade: UC37.
UC39 — Tratar Inativação do Pesquisador
Identificador: UC39
Nome: Tratar Inativação do Pesquisador
Objetivo: Aplicar automaticamente ou por intervenção administrativa as regras de transição e salvaguarda sobre as pesquisas científicas geridas por um psicólogo que foi inativado ou bloqueado no sistema.
Atores: Administrador, Comitê de Ética (via sistema).
Pré-condições:Um psicólogo com pesquisas ativas ou em rascunho sofreu alteração de status para "Inativo" ou "Bloqueado" (via UC08).
Pós-condições:
As pesquisas do profissional sofrem as devidas transições de estado (cancelamento, suspensão ou arquivamento).
O Comitê de Ética é notificado e a rastreabilidade das ações é garantida.
Fluxo Principal:
O sistema deteta a inativação ou o bloqueio administrativo de um utilizador com o perfil de Pesquisador (em consonância com o UC08).
O sistema identifica todas as pesquisas associadas ao profissional e agrupa-as pelo estado atual no ciclo de vida (RN-052).
Para pesquisas em estado Rascunho ou Submetida: o sistema cancela-as automaticamente ou disponibiliza-as para transferência de responsabilidade a outro pesquisador habilitado.
Para pesquisas em estado Aprovada ou Em Coleta: o sistema altera automaticamente o estado para Suspensa, interrompendo a recolha de dados.
Para pesquisas em estado Concluída: o sistema mantém-nas arquivadas, preservando o histórico integral.
O sistema notifica o Comitê de Ética sobre as medidas aplicadas e gera a comunicação formal de transferência ou suspensão.
O sistema regista todas as movimentações e transferências no log de auditoria.
O caso de uso é encerrado.
Fluxos Alternativos:
3a. Atribuição de novo responsável a uma pesquisa suspensa:
3a.1. O Administrador indica um novo psicólogo habilitado para assumir a titularidade de uma pesquisa suspensa.
3a.2. O sistema valida as credenciais do novo responsável, atualiza a autoria e notifica o Comitê de Ética para reavaliação da retoma do estado Em Coleta.
3a.3. O fluxo prossegue para o passo 7.
Regras de Negócio: RN-018, RN-052, RN-053.
Requisitos Funcionais: RF-065, RF-070.
Requisitos Não Funcionais: RNF-010, RNF-024.
Rastreabilidade: HU47, UC08, UC34.
UC40 — Definir Recorte de Pesquisa
Identificador: UC40
Nome: Definir Recorte de Pesquisa
Objetivo: Permitir que o pesquisador configure os parâmetros analíticos e os filtros de anonimização (recorte) sobre a base de dados do LAPI para a extração de dados estatísticos ou epidemiológicos aprovados eticamente.
Atores: Pesquisador (Psicólogo).
Pré-condições: A pesquisa deve possuir aprovação ética válida (UC36) e o pesquisador deve estar autenticado.
Pós-condições: O motor do LAPI gera o conjunto de dados anonimizados conforme os critérios definidos.
Fluxo Principal:
O pesquisador acede à sua pesquisa aprovada e seleciona "Definir Recorte Analítico".
O sistema apresenta os filtros disponíveis (faixa etária, período temporal, categorias diagnósticas genéricas e região).
O pesquisador define os parâmetros e submete o pedido de extração.
O motor de anonimização do LAPI processa a consulta, aplicando técnicas de supressão de identificadores diretos.
O sistema gera o dataset anonimizado seguro e disponibiliza o download/visualização para o pesquisador.
O sistema regista a extração e os parâmetros no log de auditoria.
O caso de uso é encerrado.
Regras de Negócio: RN-046, RN-047, RN-051.
Requisitos Funcionais: RF-063, RF-070, RF-071.
Requisitos Não Funcionais: RNF-010, RNF-023, RNF-038.
Rastreabilidade: UC34, UC36, UC39.