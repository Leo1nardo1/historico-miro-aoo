ON DELETE CASCADE:
tb_sessao, tb_token_redefinicao e tb_tentativa_2fa devem ser excluídas automaticamente se a tb_conta_acesso for excluída.
tb_registro_atendimento e tb_registro_documental devem ser excluídas se o tb_prontuario for excluído.
ON DELETE SET NULL:
Em tb_log_auditoria, se uma tb_conta_acesso for excluída (por LGPD, por exemplo), o campo id_conta no log deve se tornar NULL, mas o log permanece intacto (RN-013).
ON DELETE RESTRICT (ou NO ACTION):
Não é permitido excluir um tb_paciente se ele possuir agendamentos ou prontuário. A exclusão deve ser feita via inativação/anonimização (RN-036).
Não é permitido excluir um tb_psicologo se ele possuir vínculos ativos (RN-031).
CHECK Constraints (Validações de Domínio):
tb_agendamento.status deve pertencer ao conjunto: ('PENDENTE', 'CONFIRMADO', 'CANCELADO', 'REMARCADO', 'REALIZADO', 'NAO_COMPARECEU').
tb_conta_acesso.status deve pertencer ao conjunto: ('ATIVA', 'INATIVA', 'BLOQUEADA').
tb_pesquisa.estado deve pertencer ao conjunto: ('RASCUNHO', 'SUBMETIDA', 'EM_AVALIACAO', 'APROVADA', 'REJEITADA', 'EM_COLETA', 'SUSPENSA', 'CONCLUIDA', 'CANCELADA').
tb_registro_atendimento.data_hora_inicio deve ser menor ou igual à data/hora atual (impede data futura - RN-045).
UNIQUE Constraints (Garantias de Unicidade):
tb_pessoa.cpf (não pode haver dois CPFs iguais).
tb_conta_acesso.email_login (não pode haver dois logins com o mesmo e-mail).
tb_prontuario.id_paciente (um paciente só tem um prontuário).
tb_registro_atendimento.id_agendamento (um agendamento gera apenas um registro de atendimento).