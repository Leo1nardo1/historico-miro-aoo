ATORES E RESPONSABILIDADES
1. Objetivo
Este documento identifica os papéis que interagem com a
Plataforma de Psicologia e delimita suas responsabilidades conforme
os requisitos funcionais (RF), as regras de negócio (RN) e os
requisitos não funcionais (RNF) definidos para o projeto.
Observação de modelagem: ator representa um papel que
interage com o sistema, não necessariamente uma pessoa ou uma conta
exclusiva. Uma mesma pessoa pode desempenhar mais de um papel, desde
que possua as permissões necessárias.
2. Atores principais
2.1 Administrador
Tipo: ator interno, usuário autenticado.
Responsabilidades:
Criar contas de acesso para usuários da clínica, conforme
 os fluxos específicos de conta.
Consultar e gerenciar usuários, atendentes, profissionais e
 dados administrativos de pacientes, respeitando as permissões
 aplicáveis.
Criar e gerenciar perfis de acesso e associar permissões.
Ativar, inativar ou bloquear administrativamente contas de
 usuários.
Consultar logs de auditoria quando possuir permissão.
Configurar as políticas de cancelamento e ausência, o
 limite de remarcações e o horário comercial da clínica.
Cadastrar e atualizar os dados de responsáveis legais,
 conforme as permissões definidas.
Restrições:
Não pode visualizar senhas em texto legível.
Deve respeitar o controle de autorização e a imutabilidade
 dos logs de auditoria.
A gestão administrativa não concede automaticamente acesso
 irrestrito a informações clínicas confidenciais.
Rastreabilidade principal: RF-012 a RF-020, RF-022,
RF-025, RF-026, RF-032, RF-034, RF-036, RF-050 a RF-052; RN-002,
RN-013, RN-016 a RN-018, RN-024 a RN-027; RNF de segurança,
autorização, auditoria e proteção de dados.
2.2 Psicólogo
Tipo: ator interno, usuário autenticado.
Responsabilidades:
Consultar e atualizar o próprio perfil profissional e sua
 área de atuação.
Definir e gerenciar sua disponibilidade.
Consultar a própria agenda e gerenciar agendamentos conforme
 suas permissões.
Confirmar agendamentos e cancelar agendamentos permitidos.
Consultar apenas as informações confidenciais de pacientes
 que estejam vinculados a ele e que estejam abrangidas por suas
 permissões.
Criar, encerrar ou manter vínculos com pacientes quando
 autorizado.
Registrar atendimentos realizados vinculados a um agendamento
 confirmado, ao paciente e ao próprio profissional responsável.
Consultar o histórico de atendimentos conforme as regras de
 acesso.
Exercer o papel de pesquisador quando estiver autorizado a
 criar ou conduzir pesquisas.
Processar solicitações de acesso ao prontuário psicológico
 por responsáveis legais, incluindo entrega mediada ou registro
 fundamentado de restrição, conforme as regras aplicáveis.
Restrições:
Não pode acessar informações clínicas de pacientes sem
 vínculo válido, salvo hipótese expressamente prevista nas regras
 aplicáveis.
Não pode registrar atendimento com data futura.
O atendimento precisa estar associado ao agendamento
 confirmado correspondente.
A inativação ou o bloqueio administrativo encerra os
 vínculos ativos e aciona o tratamento das pesquisas sob sua
 responsabilidade; bloqueio temporário de autenticação não produz
 esses efeitos.
Rastreabilidade principal: RF-023 a RF-030, RF-033, RF-037
a RF-049, RF-054 a RF-070; RN-022, RN-028 a RN-031, RN-034 a
RN-036, RN-037, RN-042, RN-044 a RN-050, RN-052 e RN-053.
2.3 Atendente
Tipo: ator interno, usuário autenticado.
Responsabilidades:
Cadastrar e atualizar dados administrativos de pacientes
 conforme suas permissões.
Apoiar o agendamento, a confirmação, o cancelamento e a
 remarcação de consultas.
Consultar agendas de profissionais quando autorizado.
Apoiar atividades administrativas e a comunicação com
 pacientes.
Consultar ou atualizar outros registros administrativos
 apenas nos limites das permissões concedidas.
Restrições:
Não possui acesso automático a dados confidenciais do
 prontuário psicológico.
Não pode executar operações fora das permissões de seu
 perfil.
Rastreabilidade principal: RF-017, RF-025, RF-026,
RF-037 a RF-045, RF-049 e RF-053; RN-016, RN-019, RN-027, RN-038 a
RN-043 e RN-046.
2.4 Paciente
Tipo: ator interno/externo conforme o cenário de
interação; só realiza ações autenticadas quando possui uma conta
de acesso.
Responsabilidades:
Solicitar ou realizar agendamento de consulta, conforme as
 funcionalidades habilitadas.
Consultar e cancelar seus próprios agendamentos, conforme as
 permissões definidas.
Consultar os próprios dados e informações disponibilizadas
 para seu perfil.
Consultar seu histórico quando essa funcionalidade estiver
 disponível e autorizada.
Registrar a opção de não participar de pesquisas
 (opt-out).
Participar de pesquisa quando aplicável e quando houver o
 TCLE exigido e registrado.
Ao atingir a maioridade, passar a exercer os direitos sobre
 os próprios dados e, se desejar e estiver previsto, utilizar uma
 conta própria.
Restrições:
Não pode consultar dados, situação, agendamentos ou
 informações pertencentes a outro paciente.
O cadastro administrativo de paciente não cria
 automaticamente uma conta de acesso.
A conta de acesso é criada pelo Administrador nas situações
 previstas pelas regras de negócio.
O paciente não confirma o agendamento como responsabilidade
 própria no conjunto atual de RFs; a confirmação cabe ao Psicólogo
 ou ao Atendente autorizado.
Rastreabilidade principal: RF-031, RF-034, RF-035, RF-038,
RF-041, RF-054, RF-060, RF-068 e RF-069; RN-005, RN-006, RN-023,
RN-032, RN-033, RN-050 e RN-051.
2.5 Responsável legal
Tipo: ator interno/externo conforme o cenário; pode
interagir com funcionalidades autenticadas quando possuir conta
própria.
Responsabilidades:
Manter vínculo cadastral com o paciente menor de idade que
 representa.
Consultar informações administrativas do paciente dentro
 dos limites de sua representação e das permissões aplicáveis.
Solicitar acesso ao prontuário psicológico por meio do
 sistema, após a verificação de identidade exigida.
Receber, quando autorizada, a entrega mediada de informações
 do prontuário pelo Psicólogo responsável.
Ter sua solicitação encaminhada para avaliação quando a
 informação for solicitada por canais da clínica.
Restrições:
A conta do responsável legal, quando existente, é
 independente da conta do paciente; credenciais não podem ser
 compartilhadas.
O responsável legal não recebe acesso irrestrito ao
 prontuário: aplicam-se o processo de entrega mediada e as exceções
 de restrição previstas.
Quando o paciente completa 18 anos, a representação legal
 cessa e o acesso ao prontuário é revogado, salvo autorização
 expressa do paciente.
A existência de cadastro de responsável legal não
 significa, por si só, que exista uma conta de acesso.
Rastreabilidade principal: RF-026, RF-032, RF-034, RF-036,
RF-053 e RF-056 a RF-060; RN-024 a RN-027, RN-032, RN-033, RN-035 e
RN-036.
2.6 Pesquisador
Tipo: papel funcional que, no escopo atual, é desempenhado
por um Psicólogo autorizado; não pressupõe uma conta separada.
Responsabilidades:
Criar pesquisas e definir critérios e recortes dos dados a
 serem utilizados.
Submeter pesquisas ao fluxo de avaliação ética e
 acompanhar seus estados.
Utilizar dados anonimizados conforme as regras de pesquisa.
Garantir que a coleta não comece sem aprovação ética.
Garantir o registro do TCLE aplicável e respeitar a opção
 de não participação.
Manter a pesquisa dentro das transições de estado
 permitidas.
Em caso de inativação ou bloqueio administrativo do
 Psicólogo responsável, seguir o processo de suspensão,
 transferência ou cancelamento aplicável, com rastreabilidade e
 comunicação ao Comitê de Ética.
Restrições:
Não pode iniciar coleta sem aprovação prévia do Comitê
 de Ética.
Não pode receber dados de pesquisa antes da anonimização
 exigida nem apresentar identificadores diretos nos resultados.
Não pode incluir participantes que tenham optado por não
 participar.
Rastreabilidade principal: RF-061 a RF-070; RN-047 a
RN-053; RNF de proteção de dados, autorização, auditoria e
confidencialidade.
2.7 Comitê de Ética
Tipo: ator externo.
Responsabilidades:
Receber pesquisas submetidas à avaliação ética.
Avaliar a pesquisa e registrar o parecer/decisão.
Aprovar ou rejeitar pesquisas e participar das decisões
 éticas que condicionem o início, a suspensão, a retomada, a
 transferência de responsabilidade ou o encerramento da coleta.
Ser comunicado sobre a inativação do Psicólogo responsável
 por pesquisas quando exigido pela regra de negócio.
Nota de escopo: o fluxo atual contempla estados como
Submetida, Em Avaliação, Aprovada, Rejeitada,
Em Coleta, Suspensa, Concluída e Cancelada.
“Solicitar alterações” pode ser representado pelo retorno da
pesquisa rejeitada para Rascunho para ajustes; não está
definido como estado independente.
Rastreabilidade principal: RF-064 a RF-070; RN-047, RN-052
e RN-053.
3. Atores externos de apoio
3.1 Serviço de e-mail
Tipo: sistema externo de apoio, se a implementação
utilizar um provedor separado.
Responsabilidades: entregar mensagens de
recuperação/redefinição de senha, notificação de bloqueio
temporário e outras comunicações exigidas pelos requisitos.
Rastreabilidade principal: RF-004, RF-005, RF-009;
RN-014 e RN-011, conforme aplicável.
3.2 Base externa do Conselho Federal de Psicologia (CFP)
Tipo: sistema externo consultado quando disponível (API).
Responsabilidade: apoiar a validação do CRP no
cadastro/ativação de Psicólogos. Quando a consulta externa não
estiver disponível, aplica-se o processo de validação manual pelo
Administrador; cadastros com CRP inválido não devem ser ativados.
Rastreabilidade principal: RF-021 e RF-022; RN-021.
.


