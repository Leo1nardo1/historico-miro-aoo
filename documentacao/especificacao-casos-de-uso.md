ESPECIFICAÇÃO DOS PRINCIPAIS CASOS DE USOUC01 — Autenticar-se
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
