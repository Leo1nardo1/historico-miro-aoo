REQUISITOS FUNCIONAIS
Módulo 1 — Autenticação e Segurança
RF-001 — AutenticaçãoO sistema deve permitir que usuários com conta de acesso realizem login utilizando e-mail e senha.
RF-002 — Alteração de senhaO sistema deve permitir que o usuário altere sua própria senha, respeitando a política de complexidade definida para as senhas.
RF-003 — Alteração obrigatória de senha no primeiro acessoO sistema deve exigir que o usuário altere a senha provisória em seu primeiro acesso.
RF-004 — Recuperação de senhaO sistema deve permitir que usuários não autenticados iniciem o processo de recuperação de senha utilizando o e-mail associado à conta, sem revelar se o endereço informado está ou não cadastrado.
RF-005 — Redefinição de senhaO sistema deve permitir a redefinição de senha por meio de um link temporário, válido por 30 minutos e de uso único após a redefinição bem-sucedida, conforme os RNF-040 e RNF-041.
RF-006 — Bloqueio temporário por tentativas inválidasO sistema deve bloquear temporariamente a autenticação de uma conta após cinco tentativas consecutivas de login inválido, mantendo o bloqueio temporário por 15 minutos, conforme a regra de negócio.
RF-007 — Controle de status do usuárioO sistema deve permitir que usuários autorizados gerenciem o status de acesso dos usuários, contemplando os estados Ativo, Inativo e Bloqueado.
RF-008 — Restrição de autenticaçãoO sistema deve impedir a autenticação de usuários cujo status não seja Ativo.
RF-009 — Notificação de bloqueio temporárioO sistema deve notificar o usuário por e-mail quando sua conta for temporariamente bloqueada em decorrência de tentativas consecutivas de autenticação inválida.
RF-010 — Autenticação de dois fatores em operações críticasO sistema deve exigir autenticação de dois fatores (2FA) para o acesso administrativo e para as operações críticas definidas na RN-015, incluindo a redefinição de senha e o login em dispositivo não reconhecido.
RF-011 — Controle de sessões simultâneasO sistema deve invalidar a sessão anterior quando detectar um novo login com as mesmas credenciais em outro dispositivo e notificar o usuário.

Módulo 2 — Administração, Contas, Perfis e Auditoria
RF-012 — Criação de contas de acesso para usuários da clínicaO sistema deve permitir que apenas o Administrador crie contas de acesso para Administradores, Psicólogos e Atendentes, definindo uma senha provisória que deverá ser alterada no primeiro acesso. A criação deve respeitar as regras de exclusividade de cadastro e de senha provisória (RN-002, RN-004 e RN-008). As contas de pacientes e responsáveis legais são tratadas em requisitos específicos.
RF-013 — Gerenciamento de usuáriosO sistema deve permitir que o Administrador consulte e gerencie os dados cadastrais dos usuários registrados, respeitando as permissões aplicáveis.
RF-014 — Gerenciamento de perfis de acessoO sistema deve permitir que o Administrador crie, consulte e gerencie perfis de acesso.
RF-015 — Gerenciamento de permissõesO sistema deve permitir que o Administrador associe permissões aos perfis de acesso.
RF-016 — Ativação, inativação e bloqueio administrativoO sistema deve permitir que o Administrador altere o status de acesso dos usuários conforme as permissões definidas.
RF-017 — Controle de autorizaçãoO sistema deve verificar as permissões do usuário autenticado antes de permitir a execução de operações protegidas.
RF-018 — Registro de auditoriaO sistema deve registrar em log as operações sensíveis realizadas, incluindo, quando aplicável, o usuário responsável, a data e hora, a operação realizada e os dados alterados. Os registros devem respeitar as regras de imutabilidade da RN-018.
RF-019 — Consulta de auditoriaO sistema deve permitir que o Administrador consulte os logs de auditoria, desde que possua a permissão necessária.
RF-020 — Gerenciamento de atendentesO sistema deve permitir que o Administrador cadastre, consulte, altere e gerencie os dados cadastrais e funcionais dos atendentes. A criação e o gerenciamento de suas contas de acesso devem respeitar os requisitos gerais de usuários.

Módulo 3 — Gestão de Profissionais, Pacientes e Responsáveis Legais
RF-021 — Validação de campos cadastrais críticosO sistema deve validar os campos críticos durante o cadastro ou a alteração dos dados, incluindo CPF (formato e dígito verificador), CRP (formato e validação conforme a RN-021), e-mail (formato e unicidade), telefone (formato conforme o padrão brasileiro) e data de nascimento (formato e consistência com a idade informada, quando aplicável).
RF-022 — Gerenciamento de profissionaisO sistema deve permitir que o Administrador cadastre, consulte, altere e gerencie os profissionais da clínica. A ativação do cadastro de um psicólogo deve respeitar a validação de CRP prevista na RN-021.
RF-023 — Perfil profissionalO sistema deve permitir que o psicólogo consulte e atualize seu próprio perfil profissional, conforme as permissões definidas.
RF-024 — Área de atuação profissionalO sistema deve permitir que o psicólogo informe e gerencie sua área de atuação.
RF-025 — Cadastro e gerenciamento administrativo de pacientesO sistema deve permitir que Administradores, Atendentes e Psicólogos realizem o cadastro administrativo de pacientes conforme suas permissões. O Administrador deve poder consultar e gerenciar os registros de pacientes de acordo com as permissões estabelecidas.
RF-026 — Cadastro de responsável legalO sistema deve permitir o cadastro dos dados de identificação e contato do responsável legal associado a um paciente menor de 18 anos, conforme as permissões do usuário autenticado.
RF-027 — Criação de vínculo entre paciente e psicólogoO sistema deve permitir a criação de vínculo entre paciente e psicólogo, registrando a data de início, o motivo e o responsável pela criação, conforme a RN-028.
RF-028 — Encerramento de vínculo entre paciente e psicólogoO sistema deve permitir o encerramento de vínculo entre paciente e psicólogo, registrando a data de encerramento, o motivo e o responsável pela ação, conforme a RN-029.
RF-029 — Múltiplos vínculos de um pacienteO sistema deve permitir que um paciente possua vínculos simultâneos com múltiplos psicólogos, desde que cada vínculo seja registrado e autorizado individualmente.
RF-030 — Restrição de acesso do psicólogo aos pacientesO sistema deve restringir o acesso do psicólogo às informações confidenciais dos pacientes vinculados a ele, respeitando as permissões definidas.
RF-031 — Restrição de acesso do paciente aos próprios dadosO sistema deve restringir o acesso do paciente aos seus próprios dados e às funcionalidades autorizadas, impedindo o acesso a informações pertencentes a outros pacientes.
RF-032 — Atualização dos dados do responsável legalO sistema deve permitir que usuários autorizados consultem e atualizem os dados cadastrais do responsável legal associado ao paciente, preservando a integridade do vínculo entre ambos.
RF-033 — Encerramento de vínculos por inativação ou bloqueio administrativo do psicólogoO sistema deve encerrar os vínculos ativos de um psicólogo que seja inativado ou bloqueado administrativamente, registrar o motivo, preservar o histórico, comunicar os pacientes afetados e permitir que a clínica avalie a continuidade do cuidado, conforme a RN-031. Esse comportamento não deve ser acionado apenas por um bloqueio temporário de autenticação.
RF-034 — Transição do paciente para a maioridadeO sistema deve identificar quando o paciente completar 18 anos e aplicar as ações previstas nas RN-032 e RN-033, incluindo o encerramento do vínculo de representação legal, a revogação do acesso do responsável legal ao prontuário — salvo autorização expressa do paciente — e a preservação dos dados do responsável pelos prazos aplicáveis. O sistema deve permitir registrar eventual autorização expressa para a continuidade do acesso do responsável, manter eventual conta de acesso do paciente e sinalizar à clínica a necessidade de avaliar a criação de uma conta quando ela ainda não existir.
RF-035 — Criação de conta de acesso do pacienteO sistema deve permitir que o Administrador crie uma conta de acesso para o paciente nas situações previstas na RN-006. A conta deve ser independente dos registros de outros usuários, e a senha provisória deve seguir as regras aplicáveis de criação e alteração no primeiro acesso.
RF-036 — Criação de conta de acesso para responsável legalO sistema deve permitir que o Administrador crie uma conta de acesso para o responsável legal, com perfil específico e identidade independente da conta do paciente, respeitando as RN-002, RN-024 e RN-025.

Módulo 4 — Agenda e Atendimento
RF-037 — Disponibilidade profissionalO sistema deve permitir que o psicólogo informe e gerencie sua disponibilidade para atendimento.
RF-038 — Agendamento de consultaO sistema deve permitir que o paciente solicite ou realize o agendamento de uma consulta conforme a disponibilidade do profissional e as regras de agendamento da clínica.
RF-039 — Confirmação de agendamentoO sistema deve permitir que o psicólogo ou o Atendente confirme um agendamento, conforme as permissões definidas.
RF-040 — Validação de conflito de horárioO sistema deve verificar conflitos de horário ao criar ou confirmar um agendamento e impedir a sobreposição de agendamentos do psicólogo, considerando os estados abrangidos pela RN-037.
RF-041 — Cancelamento de agendamentoO sistema deve permitir que o paciente, o psicólogo ou o Atendente cancele um agendamento, conforme as permissões definidas.
RF-042 — Registro de cancelamentoO sistema deve registrar as informações relacionadas ao cancelamento, incluindo o responsável, a data e hora, o motivo quando informado e a classificação aplicável, conforme a RN-039.
RF-043 — Classificação de cancelamentos e ausênciasO sistema deve classificar os cancelamentos como antecipados ou tardios e permitir a classificação de uma ausência como não comparecimento, conforme a política da clínica e a RN-040.
RF-044 — Registro de não comparecimentoO sistema deve permitir que usuários autorizados registrem o não comparecimento do paciente a um agendamento, preservando as informações necessárias para aplicação das políticas da clínica.
RF-045 — Remarcação de consultaO sistema deve permitir a remarcação de um agendamento confirmado, criando um novo registro e preservando o registro anterior no histórico. O novo agendamento deve passar por nova confirmação.
RF-046 — Registro de atendimento realizadoO sistema deve permitir que o psicólogo registre um atendimento realizado.
RF-047 — Vinculação do atendimentoO sistema deve vincular cada atendimento registrado ao respectivo agendamento confirmado, paciente e psicólogo responsável, conforme a RN-044.
RF-048 — Validação da data do atendimentoO sistema deve impedir o registro de atendimento com data posterior à data corrente, conforme a RN-045.
RF-049 — Consulta de agendaO sistema deve permitir a consulta da agenda por profissional, período e situação do agendamento, conforme as permissões do usuário e a RN-046.
RF-050 — Configuração das políticas de cancelamento e ausênciaO sistema deve permitir que o Administrador configure as políticas de cancelamento e ausência da clínica, incluindo, quando adotados, o prazo mínimo para cancelamento antecipado, os percentuais de cobrança por cancelamento tardio ou não comparecimento e os critérios para bloqueio de pacientes.
RF-051 — Configuração do limite de remarcaçõesO sistema deve permitir que o Administrador configure o número máximo de remarcações permitidas por agendamento, conforme a RN-043.
RF-052 — Configuração do horário comercialO sistema deve permitir que o Administrador configure o horário comercial da clínica, incluindo dias da semana e faixas de horário, para o cálculo da disponibilidade e a realização de agendamentos.

Módulo 5 — Prontuário, Confidencialidade e Proteção de Dados
RF-053 — Encaminhamento de solicitações de informações por terceirosO sistema deve registrar e encaminhar aos canais de atendimento da clínica as solicitações de informações sobre pacientes realizadas por responsáveis legais ou terceiros, para avaliação por pessoal autorizado antes de qualquer divulgação, conforme a RN-027.
RF-054 — Consulta ao histórico de atendimentosO sistema deve permitir a consulta ao histórico de atendimentos conforme as permissões do usuário e as regras de confidencialidade e restrição de acesso aplicáveis.
RF-055 — Preservação do histórico após encerramento do vínculoO sistema deve preservar o histórico de atendimentos após o encerramento do vínculo entre paciente e psicólogo, conforme a RN-029.
RF-056 — Solicitação de acesso ao prontuário pelo responsável legalO sistema deve permitir que o responsável legal de um paciente menor de 18 anos, após autenticação de identidade, registre uma solicitação de acesso ao prontuário psicológico. A solicitação deve ser encaminhada ao psicólogo responsável para avaliação e processamento, conforme a RN-026.
RF-057 — Entrega mediada do prontuárioO sistema deve permitir que o psicólogo responsável realize a entrega mediada do prontuário após receber uma solicitação de acesso, por meio da geração de documento em PDF ou da liberação de visualização on-line. O sistema deve registrar a data e hora da entrega, o conteúdo disponibilizado e a identidade do destinatário. A entrega não deve incluir o registro documental privativo do psicólogo, conforme a RN-026.
RF-058 — Registro de restrição de acesso ao prontuárioO sistema deve permitir que o psicólogo responsável registre a decisão de restringir o acesso do responsável legal ao prontuário, apresentando a justificativa específica aplicável, como suspeita de abuso contra o menor por parte do responsável, conflito de guarda com determinação judicial ou risco iminente à segurança do menor, conforme a RN-026.
RF-059 — Auditoria das operações relacionadas ao prontuárioO sistema deve registrar em log de auditoria toda solicitação, entrega, restrição ou visualização de prontuário psicológico, permitindo identificar o solicitante, o paciente, o psicólogo responsável, a data e hora, o tipo de operação e o fundamento da restrição, quando houver, conforme a RN-035.
RF-060 — Solicitação de exclusão ou anonimização de dados pessoaisO sistema deve permitir que o paciente ou seu representante legal, quando autorizado, registre uma solicitação de exclusão ou anonimização de dados pessoais. A solicitação deve ser avaliada e tratada conforme a RN-036 e as obrigações legais aplicáveis, sem eliminar automaticamente registros que devam ser mantidos nem comprometer a imutabilidade dos logs ou o sigilo profissional.

Módulo 6 — Pesquisa e Ética
RF-061 — Criação de pesquisaO sistema deve permitir que psicólogos autorizados criem pesquisas.
RF-062 — Definição de recorte de pesquisaO sistema deve permitir que o responsável pela pesquisa defina os critérios e recortes dos dados a serem utilizados.
RF-063 — Anonimização de dados para pesquisaO sistema deve anonimizar os dados antes de disponibilizá-los para utilização, processamento ou análise na pesquisa, conforme a RN-048.
RF-064 — Submissão para avaliação éticaO sistema deve permitir que uma pesquisa seja submetida ao fluxo de avaliação ética do Comitê de Ética.
RF-065 — Controle do ciclo de vida da pesquisaO sistema deve controlar os estados e as transições válidas da pesquisa, conforme a RN-052:
Rascunho: pode ser submetida ou cancelada.
Submetida: pode passar para Em Avaliação ou ser cancelada.
Em Avaliação: pode ser aprovada, rejeitada ou cancelada.
Rejeitada: pode retornar a Rascunho para ajustes ou ser cancelada.
Aprovada: pode passar para Em Coleta ou ser cancelada antes do início da coleta.
Em Coleta: pode passar para Concluída, Suspensa ou Cancelada.
Suspensa: pode retornar a Em Coleta ou ser cancelada.
Concluída e Cancelada: são estados finais.
O sistema deve impedir transições inválidas e manter a rastreabilidade das alterações de estado.
RF-066 — Bloqueio da coleta sem aprovação éticaO sistema deve impedir o início da coleta de dados de uma pesquisa que não esteja aprovada pelo Comitê de Ética, conforme a RN-047.
RF-067 — Registro do Termo de Consentimento Livre e Esclarecido (TCLE)O sistema deve permitir o registro do TCLE associado à pesquisa e ao paciente participante, conforme a RN-050.
RF-068 — Registro da opção de não participaçãoO sistema deve permitir o registro da opção do paciente de não participar de pesquisas, conforme a RN-051.
RF-069 — Respeito à opção de não participação (opt-out)O sistema deve impedir que pacientes que tenham optado por não participar sejam incluídos em pesquisas futuras, conforme a RN-051.
RF-070 — Efeitos da inativação do psicólogo sobre pesquisas sob sua responsabilidadeO sistema deve aplicar o tratamento previsto na RN-053 quando um psicólogo responsável por pesquisas for inativado ou bloqueado administrativamente: pesquisas em Rascunho ou Submetida podem ser canceladas ou transferidas para outro pesquisador habilitado; pesquisas Aprovadas ou Em Coleta devem ser suspensas até decisão sobre transferência ou cancelamento, conforme o Comitê de Ética; pesquisas Concluídas devem permanecer arquivadas; transferências de responsabilidade devem ser auditáveis; e o Comitê de Ética deve ser comunicado.