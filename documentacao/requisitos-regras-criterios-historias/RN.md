REGRAS DE NEGÓCIO
Módulo 1 — Gestão de Contas, Autenticação e Segurança
RN-001 — Conta individual
Todo usuário do sistema — Administrador, Psicólogo, Atendente ou Paciente — deve possuir uma conta individual e credenciais próprias, sendo vedado o compartilhamento de contas entre pessoas.
RN-002 — Exclusividade do cadastro de contas
A criação de contas de acesso ao sistema é de responsabilidade exclusiva do Administrador.
RN-003 — Proibição de auto-cadastro
Não é permitido o auto-cadastro de usuários. Nenhum usuário pode criar sua própria conta de acesso sem a intervenção do Administrador.
RN-004 — Senha provisória definida pelo Administrador
Ao criar uma conta de acesso, o Administrador deve definir uma senha provisória, que deverá ser obrigatoriamente alterada pelo usuário no primeiro acesso, conforme a RN-008.
RN-005 — Separação entre conta de acesso e cadastro de paciente
O cadastro de pacientes (dados administrativos) não cria conta de acesso ao sistema, e a criação de conta de acesso é regida pela RN-002.
RN-006 — Criação de conta de acesso do paciente
O paciente é, por padrão, cadastrado apenas como registro administrativo, sem conta de acesso ao sistema.
A conta de acesso do paciente pode ser criada pelo Administrador quando:
(a) o paciente manifestar interesse em utilizar funcionalidades que exijam autenticação;
(b) o paciente atingir a maioridade e desejar assumir a gestão de seus próprios dados (RN-032);
(c) a clínica entender necessário para a prestação do serviço.
A criação da conta segue a RN-002 e a RN-004.
RN-007 — Política de complexidade de senha
Toda senha deve conter, no mínimo, uma letra maiúscula, uma letra minúscula, um número e um caractere especial.
RN-008 — Alteração de senha no primeiro acesso
Quando uma senha provisória for definida para um usuário, ela deverá ser obrigatoriamente alterada pelo usuário em seu primeiro acesso.
RN-009 — Status do usuário
Todo usuário deve possuir um status de acesso, podendo estar Ativo, Inativo ou Bloqueado.
RN-010 — Autenticação de usuários ativos
Somente usuários com status Ativo podem realizar autenticação no sistema.
RN-011 — Bloqueio temporário por tentativas inválidas
Após cinco tentativas consecutivas de autenticação inválida, a conta deverá permanecer temporariamente bloqueada por 15 minutos.
Observação: esse bloqueio temporário não deve ser confundido com o status administrativo Bloqueado do usuário.
RN-012 — Natureza distinta do bloqueio temporário e do status Bloqueado
O bloqueio temporário por tentativas inválidas de autenticação (RN-011) e o status administrativo Bloqueado (RN-009) são institutos distintos:
(a) o bloqueio temporário é medida de segurança de curta duração, não altera o status do usuário e cessa automaticamente após o prazo definido;
(b) o status Bloqueado é decisão administrativa, de duração indeterminada, que impede a autenticação enquanto perdurar;
(c) o bloqueio temporário não produz efeitos quando o usuário já se encontra com status Inativo ou Bloqueado, pois nesses casos a autenticação já é impedida pela RN-010.
RN-013 — Não exposição de credenciais
Nenhum usuário, inclusive o Administrador, pode visualizar a senha de outro usuário em texto legível.
RN-014 — Não exposição da existência de conta
O processo de recuperação de senha não deve revelar se o endereço de e-mail informado está ou não cadastrado no sistema.
RN-015 — Proteção adicional para operações críticas
Operações consideradas críticas no domínio — acesso administrativo, redefinição de senha e acesso a partir de dispositivo não reconhecido — exigem confirmação adicional de identidade do usuário, além da senha, como medida de proteção do sigilo das informações sob responsabilidade da clínica.
A confirmação adicional não se aplica a usuários impedidos de autenticar (RN-010), pois nestes casos o acesso já é negado.

Módulo 2 — Administração, Perfis, Permissões e Auditoria
RN-016 — Permissões por perfil
Cada perfil de acesso deve possuir um conjunto explícito de permissões, e nenhum usuário poderá executar uma operação que não esteja autorizada para seu perfil.
RN-017 — Auditoria de operações sensíveis
Operações sensíveis da clínica, como criação, exclusão ou alteração de usuários, perfis e permissões, bem como outras operações classificadas como críticas devem ser rastreáveis, de modo a permitir a identificação posterior do usuário responsável, da data e hora, da operação realizada e dos dados alterados.
RN-018 — Imutabilidade dos logs
Os registros de auditoria não podem ser editados ou excluídos por nenhum perfil, inclusive pelo Administrador.
RN-019 — Atuação do atendente no domínio da clínica
O atendente atua no apoio administrativo da clínica, sendo responsável por atividades de recepção, cadastro administrativo, agendamento e comunicação com pacientes.
RN-020 — Rastreabilidade das tentativas de autenticação em dois fatores
As tentativas de autenticação em dois fatores — bem-sucedidas ou malsucedidas — devem ser rastreáveis, de modo a permitir a identificação posterior do usuário, da data, da hora e do resultado da tentativa.

Módulo 3 — Profissionais, Pacientes, Responsáveis Legais e Vínculos
RN-021 — Validação de CRP
O CRP informado no cadastro de um psicólogo deve ser validado antes da ativação da conta, por meio de validação de formato, consulta à base externa do CFP quando disponível, e validação manual pelo Administrador quando a consulta automática não for possível. Cadastros com CRP inválido não devem ser ativados.
RN-022 — Restrição de acesso do psicólogo
Um psicólogo somente pode acessar informações confidenciais de pacientes que estejam vinculados a ele.
RN-023 — Isolamento entre pacientes
Um paciente não pode acessar informações pessoais, status ou quaisquer outros dados pertencentes a outro paciente.
RN-024 — Responsável legal de menor
Todo paciente menor de 18 anos deve possuir responsável legal cadastrado e atualizado, com dados de identificação e contato suficientes para o exercício da representação legal.
RN-025 — Independência de identidade do responsável legal e do paciente
A conta de acesso do responsável legal e a conta de acesso do paciente são identidades independentes, não podendo ser mescladas nem compartilhadas.
RN-026 — Acesso do responsável legal ao prontuário psicológico e informações do paciente
O responsável legal de paciente menor de 18 anos possui direito de acesso às informações do prontuário psicológico do paciente, incluindo o direito de obter cópia do prontuário, conforme disposto no Artigo 5º, Inciso II da Resolução CFP nº 001/2009.
O exercício concreto desse direito de acesso deve seguir as seguintes regras:
Informações administrativas (como agendamentos, status do paciente, dados cadastrais, etc.): o responsável legal possui acesso livre.
Informações do prontuário psicológico (registros de evolução, resumos de atendimento, etc.): o responsável legal pode solicitar o acesso através do sistema, e o psicólogo responsável realiza a entrega de forma mediada (por exemplo, gerando arquivo PDF ou liberando visualização), e registra no prontuário a data de entrega e a assinatura do destinatário.
Limitação do âmbito de acesso: documentos de avaliação psicológica, testes, desenhos, registros de análise detalhada de sessões e outros materiais que constituem o "registro documental privativo" do psicólogo não fazem parte do prontuário e não estão incluídos no âmbito de acesso obrigatório.
Exceções: apenas em situações em que exista suspeita de abuso contra o menor por parte do responsável, conflito grave de guarda com determinação judicial ou risco iminente à segurança do menor, é que o acesso pode ser restringido, devendo o psicólogo registrar o fundamento da restrição.
RN-027 — Solicitações de informações por terceiros
As solicitações de informações sobre pacientes realizadas por responsáveis legais ou terceiros devem ser encaminhadas aos canais de atendimento da clínica e avaliadas por pessoal autorizado antes de qualquer divulgação, observando as regras aplicáveis de confidencialidade, proteção de dados e autorização.
RN-028 — Vínculo paciente–psicólogo
Todo vínculo entre paciente e psicólogo deve ser explicitamente registrado e autorizado, contendo:
data de início;
motivo;
responsável pela criação.
RN-029 — Encerramento do vínculo
O encerramento do vínculo entre paciente e psicólogo deve ser registrado contendo:
data de encerramento;
motivo;
responsável pela ação.
O encerramento do vínculo não deve eliminar o histórico de atendimentos realizados durante o período do vínculo.
RN-030 — Múltiplos vínculos
Um paciente pode possuir vínculo simultâneo com mais de um psicólogo, desde que cada vínculo seja individualmente registrado e autorizado.
RN-031 — Efeitos da inativação ou do bloqueio administrativo do psicólogo sobre os vínculos
A inativação ou o bloqueio administrativo do psicólogo produz efeitos sobre os vínculos ativos com pacientes:
(a) os vínculos ativos são encerrados, com registro conforme a RN-029;
(b) o motivo do encerramento deve identificar a situação ocorrida, indicando a inativação ou o bloqueio administrativo do psicólogo, conforme o caso;
(c) o histórico de atendimentos é preservado (RN-029);
(d) os pacientes afetados são comunicados;
(e) a clínica é responsável por avaliar a continuidade do cuidado, observado o princípio da continuidade do atendimento psicológico.
RN-032 — Cessação da representação legal pela maioridade
A maioridade do paciente produz os seguintes efeitos:
(a) cessa, em regra, a representação legal exercida pelo responsável em razão da menoridade;
(b) o acesso do responsável legal ao prontuário é revogado, salvo autorização expressa do paciente ou hipótese legal aplicável;
(c) o paciente passa a exercer diretamente os direitos relativos aos seus próprios dados pessoais e clínicos, ressalvadas as hipóteses legais aplicáveis;
(d) eventual conta de acesso do paciente permanece válida;
(e) a clínica deve avaliar a necessidade de criação de conta de acesso, caso o paciente ainda não a possua, conforme a RN-006.
RN-033 — Destino dos dados do responsável legal após a maioridade do paciente
Com a maioridade do paciente e a cessação da representação legal (RN-032):
(a) o vínculo responsável–paciente é encerrado;
(b) o responsável legal perde o acesso ao prontuário psicológico do paciente;
(c) os dados cadastrais do responsável legal permanecem armazenados pelo prazo legal de guarda, para fins de cumprimento de obrigação legal ou exercício regular de direitos, conforme a LGPD;
(d) após o prazo legal, os dados do responsável legal podem ser anonimizados ou eliminados, observada a RN-036;
(e) o paciente pode autorizar expressamente a manutenção do acesso do responsável, se assim desejar.

Módulo 4 — Prontuário, Confidencialidade e Governança de Dados
RN-034 — Sigilo profissional
As informações clínicas dos pacientes devem permanecer sob sigilo profissional, não podendo ser divulgadas fora das hipóteses permitidas pelas regras aplicáveis ao domínio.
RN-035 — Rastreabilidade do acesso ao prontuário psicológico
Toda solicitação, entrega, restrição ou visualização de prontuário psicológico deve ser rastreável, de modo a permitir a identificação posterior do solicitante, do paciente, do psicólogo responsável, da data e hora, do tipo de operação e do fundamento, quando houver restrição.
A rastreabilidade é condição do exercício do sigilo profissional (RN-034) e do direito de acesso do responsável legal (RN-026).
RN-036 — Temporalidade dos dados pessoais e clínicos
Os dados pessoais e clínicos tratados pela clínica devem observar os prazos de guarda e as hipóteses legais de conservação aplicáveis:
(a) os registros documentais psicológicos devem ser preservados por, no mínimo, 5 anos após o último registro, podendo esse prazo ser ampliado nos casos previstos em lei, por determinação judicial ou quando houver necessidade específica de manutenção por período maior;
(b) nos estabelecimentos que prestam serviços de saúde, os prontuários de pacientes abrangidos pela Lei nº 13.787/2018 podem ser eliminados após o prazo mínimo de 20 anos a partir do último registro, observadas as condições legais aplicáveis;
(c) nos atendimentos a crianças e adolescentes, o prazo de 5 anos não deve ser aplicado automaticamente, devendo a guarda considerar a proteção integral e os demais prazos legais aplicáveis;
(d) dados administrativos podem ser anonimizados ou eliminados após o término da relação com o paciente, desde que respeitados os prazos legais e as hipóteses que exijam sua conservação;
(e) dados de pesquisa efetivamente anonimizados, sem possibilidade razoável de reidentificação, podem ser conservados para fins de pesquisa, observados o protocolo da pesquisa e as regras éticas e legais aplicáveis;
(f) o exercício do direito de eliminação não pode comprometer a imutabilidade dos logs de auditoria (RN-018) nem o sigilo profissional (RN-034).

Módulo 5 — Agenda e Atendimento
RN-037 — Não sobreposição de horários
Um psicólogo não pode possuir dois agendamentos com sobreposição de horário, considerando todos os agendamentos com situação confirmado ou pendente. Agendamentos cancelados ou remarcados não contam para a sobreposição.
RN-038 — Cancelamento de agendamento
Um agendamento pode ser cancelado pelo paciente, psicólogo ou atendente.
RN-039 — Registro do cancelamento
Todo cancelamento deve registrar:
responsável pelo cancelamento;
data e hora;
motivo, quando informado;
classificação do cancelamento.
RN-040 — Classificação de cancelamento e ausência
Os cancelamentos e as ausências devem ser classificados conforme critérios objetivos previamente definidos pela clínica:
(a) cancelamento antecipado: cancelamento comunicado com antecedência igual ou superior ao prazo mínimo definido pela clínica;
(b) cancelamento tardio: cancelamento comunicado após o prazo limite para cancelamento antecipado, mas antes de ser caracterizado o não comparecimento;
(c) não comparecimento: ausência do paciente até o limite de tolerância definido pela clínica, sem cancelamento comunicado antes desse limite.
A clínica deve definir e documentar os prazos de antecedência e a tolerância utilizados para essa classificação.

RN-041 — Políticas de cancelamento e ausência
As informações de cancelamento, cancelamento tardio e não comparecimento devem permitir que a clínica aplique suas políticas internas de cobrança ou bloqueio.
RN-042 — Remarcação
A remarcação de um agendamento confirmado gera novo registro de agendamento, mantendo o registro anterior no histórico. O novo agendamento deve passar por nova confirmação pelo psicólogo ou atendente, não herdando automaticamente a confirmação anterior.
RN-043 — Limite de remarcações
O limite de remarcações de um agendamento deve ser definido pela clínica.
RN-044 — Vinculação do atendimento
Todo atendimento realizado deve estar vinculado a um agendamento confirmado, a um paciente e ao psicólogo responsável pelo atendimento.
RN-045 — Data do atendimento
Um atendimento não pode ser registrado com data futura.
RN-046 — Acesso à agenda
A agenda de um psicólogo é informação de acesso restrito, limitada ao próprio profissional e aos perfis autorizados pela clínica.

Módulo 6 — Pesquisa e Ética
RN-047 — Aprovação ética
Uma pesquisa não pode entrar em execução ou coleta sem aprovação prévia do Comitê de Ética.
RN-048 — Anonimização para pesquisa
Os dados utilizados em pesquisas devem ser anonimizados antes de serem disponibilizados para processamento ou análise da pesquisa.
RN-049 — Não exposição de identificadores
Resultados de pesquisas não podem apresentar nome, CPF, RG ou outros dados que permitam identificar diretamente o paciente.
RN-050 — Consentimento para pesquisa
A participação do paciente em uma pesquisa deve possuir o respectivo Termo de Consentimento Livre e Esclarecido (TCLE) registrado no sistema.
RN-051 — Direito de não participação
O paciente pode optar por não participar de pesquisas.
RN-052 — Ciclo de vida da pesquisa
A pesquisa percorre estados que refletem sua situação ética e operacional, seguindo as seguintes transições:
- Rascunho → Submetida ou Cancelada.
- Submetida → Em Avaliação ou Cancelada.
- Em Avaliação → Aprovada, Rejeitada ou Cancelada.
- Rejeitada → Rascunho ou Cancelada.
- Aprovada → Em Coleta ou Cancelada.
- Em Coleta → Concluída, Suspensa ou Cancelada.
- Suspensa → Em Coleta ou Cancelada.
A pesquisa somente ingressa em coleta após aprovação ética (RN-047).
A rejeição ética impede a coleta e admite retorno ao estado de Rascunho para ajustes ou cancelamento da pesquisa.
A suspensão interrompe temporariamente a coleta, por decisão do Comitê de Ética, admitindo retomada ou cancelamento.
O cancelamento encerra a pesquisa antes de sua conclusão, por decisão do pesquisador responsável ou do Comitê de Ética.
Os estados Concluída e Cancelada são estados finais, não permitindo novas transições no ciclo de vida da pesquisa.
Todas as transições devem ser auditáveis (RNF-024).
RN-053 — Efeitos da inativação do psicólogo sobre as pesquisas sob sua responsabilidade
A inativação ou o bloqueio administrativo do psicólogo produz efeitos sobre as pesquisas sob sua responsabilidade:
(a) pesquisas em Rascunho ou Submetida podem ser canceladas ou transferidas para outro pesquisador habilitado;
(b) pesquisas Aprovadas ou Em Coleta devem ser suspensas, admitindo transferência ou cancelamento, conforme decisão do Comitê de Ética;
(c) pesquisas Concluídas permanecem arquivadas, preservando-se o histórico;
(d) a transferência de responsabilidade deve ser registrada e auditável;
(e) a clínica deve comunicar o Comitê de Ética sobre a inativação do pesquisador responsável.