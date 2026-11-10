HISTÓRIAS DE USUÁRIO E CRITÉRIOS DE ACEITE
Módulo 1 — Autenticação e Segurança
HU01 — Autenticação no sistema
Como usuário com conta de acesso, quero realizar login utilizando minhas credenciais, para acessar as funcionalidades autorizadas para meu perfil. Rastreabilidade: RF-001, RF-008; RN-009, RN-010; RNF-001, RNF-007.
Critérios de aceite:
    • CA01. Dado que o usuário possui uma conta com status Ativo e credenciais válidas, quando informar e-mail e senha corretos, então o sistema permite o acesso e apresenta as funcionalidades autorizadas para seu perfil.
    • CA02. Dado que o usuário informa uma senha incorreta, quando tentar autenticar-se, então o sistema rejeita o acesso e apresenta uma mensagem genérica de credenciais inválidas.
    • CA03. Dado que a conta está com status Inativo ou Bloqueado, quando o usuário informar credenciais corretas, então o sistema impede a autenticação.
HU02 — Controle de sessões simultâneas
Como usuário, quero que minha conta não seja utilizada em sessões simultâneas em dispositivos diferentes, para reduzir o risco de uso indevido das minhas credenciais. Rastreabilidade: RF-011; RN-001; RNF-005.
Critérios de aceite:
    • CA01. Dado que existe uma sessão ativa para uma conta, quando ocorrer um novo login com as mesmas credenciais em outro dispositivo, então o sistema invalida a sessão anterior e permite a nova sessão após concluir as verificações de segurança.
    • CA02. Dado que a sessão anterior foi invalidada, quando o usuário tentar utilizá-la, então o sistema exige nova autenticação.
    • CA03. Dado que o usuário encerrou a sessão atual, quando realizar novo login com credenciais válidas e sem outra sessão ativa, então o sistema permite a autenticação normalmente.
    • CA04. Dado que uma sessão anterior foi invalidada por novo login, quando a operação for concluída, então o sistema notifica o usuário conforme o requisito de controle de sessões.
HU03 — Alteração de senha
Como usuário autenticado, quero alterar minha senha, para manter a segurança da minha conta. Rastreabilidade: RF-002; RN-007, RN-013; RNF-001.
Critérios de aceite:
    • CA01. Dado que o usuário está autenticado, quando informar a senha atual, a nova senha e sua confirmação, então o sistema valida os dados e registra a alteração se estiverem corretos.
    • CA02. Dado que a nova senha não contém ao menos uma letra maiúscula, uma minúscula, um número e um caractere especial, quando o usuário tentar salvá-la, então o sistema rejeita a alteração e informa os requisitos não atendidos.
    • CA03. Dado que a confirmação é diferente da nova senha, quando o usuário tentar salvar, então o sistema rejeita a alteração.
    • CA04. Dado que a senha foi alterada com sucesso, quando o usuário realizar um novo login, então deverá utilizar a nova senha.
    • CA05. Dado que a senha foi alterada, quando qualquer perfil consultar os dados da conta, então o sistema não apresenta a senha em texto legível.
HU04 — Recuperação e redefinição de senha
Como usuário não autenticado, quero recuperar minha senha por e-mail, para voltar a acessar minha conta quando esquecer minhas credenciais. Rastreabilidade: RF-004, RF-005; RN-014; RNF-040, RNF-041.
Critérios de aceite:
    • CA01. Dado que o usuário solicita recuperação de senha, quando informar um endereço de e-mail, então o sistema apresenta uma mensagem genérica de confirmação, sem revelar se o endereço está cadastrado.
    • CA02. Dado que o e-mail informado pertence a uma conta, quando a solicitação for processada, então o sistema envia ao endereço associado à conta um link de redefinição.
    • CA03. Dado que o link foi gerado, quando transcorrerem 30 minutos sem que a redefinição seja concluída, então o link expira e não pode ser utilizado.
    • CA04. Dado que o link foi utilizado com sucesso para redefinir a senha, quando houver nova tentativa de utilizá-lo, então o sistema rejeita a operação.
    • CA05. Dado que o link está expirado, já foi utilizado ou é inválido, quando o usuário tentar redefinir a senha, então o sistema não altera a credencial e orienta o usuário a iniciar uma nova solicitação.
    • CA06. Dado que a redefinição de senha é uma operação crítica, quando o fluxo exigir confirmação adicional de identidade, então o sistema exige o segundo fator antes de concluir a operação.
HU05 — Alteração obrigatória de senha no primeiro acesso
Como usuário que recebeu uma senha provisória, quero alterá-la no primeiro acesso, para possuir uma credencial conhecida somente por mim. Rastreabilidade: RF-003, RF-012; RN-004, RN-008; RNF-001.
Critérios de aceite:
    • CA01. Dado que o usuário possui uma senha provisória, quando realizar o primeiro login, então o sistema exige a alteração da senha antes de liberar as demais funcionalidades.
    • CA02. Dado que a alteração obrigatória ainda não foi concluída, quando o usuário tentar acessar outra funcionalidade, então o sistema mantém o acesso restrito ao fluxo de alteração de senha.
    • CA03. Dado que o usuário informa uma nova senha que atende à política de complexidade e confirma corretamente, quando salvar, então o sistema registra a alteração e libera as funcionalidades autorizadas.
    • CA04. Dado que a nova senha não atende à política de complexidade, quando o usuário tentar salvá-la, então o sistema rejeita a alteração e mantém a exigência de troca da senha provisória.
HU06 — Criação de contas de acesso para usuários da clínica
Como Administrador, quero criar contas de acesso para Administradores, Psicólogos e Atendentes, para permitir que esses profissionais utilizem a plataforma com identidade individual. Rastreabilidade: RF-012; RN-001 a RN-005, RN-007, RN-008, RN-017.
Critérios de aceite:
    • CA01. Dado que o Administrador está autenticado e possui permissão, quando informar os dados obrigatórios e o perfil de um novo usuário da clínica, então o sistema cria uma conta individual para esse usuário.
    • CA02. Dado que o e-mail informado já está associado a outra conta, quando o Administrador tentar concluir o cadastro, então o sistema rejeita a operação e informa que o endereço não pode ser reutilizado.
    • CA03. Dado que a conta foi criada, quando forem definidas as credenciais iniciais, então o sistema exige a alteração da senha provisória no primeiro acesso.
    • CA04. Dado que uma conta foi criada, quando a operação for concluída, então o sistema registra a operação de acordo com as regras de auditoria aplicáveis.
    • CA05. Dado que um usuário sem permissão de Administrador tenta criar uma conta de acesso para usuário da clínica, quando realizar a operação, então o sistema nega a ação.
    • CA06. Dado que um usuário tenta criar a própria conta sem intervenção do Administrador, quando acessar a plataforma, então o sistema não disponibiliza auto-cadastro.
    • CA07. Dado que se deseja criar uma conta de Paciente ou Responsável Legal, quando o Administrador iniciar o procedimento, então o sistema utiliza os fluxos específicos de criação dessas contas, e não o fluxo genérico de usuários da clínica.
HU07 — Gerenciamento de status do usuário
Como Administrador, quero ativar, inativar ou bloquear administrativamente usuários, para controlar o acesso ao sistema. Rastreabilidade: RF-007, RF-008, RF-016; RN-009, RN-010, RN-012, RN-016, RN-017.
Critérios de aceite:
    • CA01. Dado que o Administrador possui permissão, quando alterar o status de um usuário para Ativo, Inativo ou Bloqueado, então o sistema registra o novo status.
    • CA02. Dado que o usuário está Inativo ou administrativamente Bloqueado, quando tentar autenticar-se com credenciais corretas, então o sistema impede o acesso.
    • CA03. Dado que o status de um usuário foi alterado, quando a operação for auditada, então o registro contém o responsável, a data e hora, a operação e os dados alterados, conforme aplicável.
    • CA04. Dado que uma conta sofre bloqueio temporário por tentativas inválidas, quando esse bloqueio ocorrer, então o sistema não altera o status administrativo da conta.
    • CA05. Dado que o Administrador tenta executar uma alteração sem possuir a permissão necessária, quando confirmar a operação, então o sistema nega a ação.
HU08 — Bloqueio temporário após tentativas inválidas
Como usuário, quero que minha conta seja temporariamente bloqueada após várias tentativas inválidas de autenticação, para reduzir o risco de acesso indevido. Rastreabilidade: RF-006, RF-009; RN-011, RN-012; RNF-006.
Critérios de aceite:
    • CA01. Dado que o usuário realizou quatro tentativas consecutivas de autenticação inválida, quando realizar a quinta tentativa inválida, então o sistema aplica bloqueio temporário por 15 minutos.
    • CA02. Dado que a conta está temporariamente bloqueada, quando houver uma nova tentativa antes do término do prazo, então o sistema impede a autenticação.
    • CA03. Dado que o bloqueio temporário foi aplicado, quando transcorrerem 15 minutos, então o sistema libera novas tentativas, desde que a conta não esteja Inativa ou administrativamente Bloqueada.
    • CA04. Dado que o bloqueio temporário foi aplicado, quando o sistema processar o evento, então envia uma notificação por e-mail ao usuário.
    • CA05. Dado que o bloqueio temporário está ativo, quando um Administrador consultar o status administrativo da conta, então o sistema não o apresenta como administrativamente Bloqueado apenas por causa desse evento temporário.
HU09 — Gerenciamento de perfis e permissões
Como Administrador, quero configurar perfis e associar permissões, para controlar quais operações cada tipo de usuário pode executar. Rastreabilidade: RF-014, RF-015, RF-017; RN-016, RN-017, RN-018; RNF-004.
Critérios de aceite:
    • CA01. Dado que o Administrador está autenticado e autorizado, quando criar um perfil, então o sistema permite registrar o perfil e associar a ele um conjunto explícito de permissões.
    • CA02. Dado que um usuário tenta executar uma operação não permitida ao seu perfil, quando solicitar a operação, então o sistema impede sua execução.
    • CA03. Dado que o Administrador altera as permissões de um perfil, quando salvar as alterações, então o sistema passa a aplicar as novas permissões aos usuários vinculados ao perfil.
    • CA04. Dado que um perfil ou permissão foi criado ou alterado, quando a operação for classificada como sensível, então o sistema registra a operação para auditoria.
    • CA05. Dado que um usuário tenta alterar perfis ou permissões sem autorização, quando confirmar a ação, então o sistema a nega.
HU10 — Autenticação de dois fatores
Como usuário em uma operação que exige proteção adicional, quero confirmar minha identidade por um segundo fator, para aumentar a segurança da conta e das informações da clínica. Rastreabilidade: RF-010; RN-015, RN-020; RNF-004.
Critérios de aceite:
    • CA01. Dado que um Administrador informa credenciais válidas, quando iniciar a autenticação, então o sistema exige a validação do segundo fator antes de conceder acesso.
    • CA02. Dado que uma operação crítica exige confirmação adicional, quando o usuário tentar concluí-la sem validar o segundo fator, então o sistema impede sua conclusão.
    • CA03. Dado que o código ou mecanismo do segundo fator é inválido, quando o usuário tentar validá-lo, então o sistema nega a autenticação adicional.
    • CA04. Dado que o segundo fator é validado corretamente, quando as demais verificações de segurança forem concluídas, então o sistema permite continuar a autenticação ou a operação.
    • CA05. Dado que o sistema recebe uma tentativa de autenticação de dois fatores, quando o processamento terminar, então registra o usuário, a data, a hora e o resultado da tentativa, com sucesso ou falha.
    • CA06. Dado que o usuário tenta acessar por dispositivo não reconhecido ou redefinir a senha, quando a política exigir confirmação adicional, então o sistema solicita o segundo fator.
Módulo 2 — Administração, Profissionais, Pacientes e Vínculos
HU11 — Gerenciamento de usuários cadastrados
Como Administrador, quero consultar e gerenciar os usuários cadastrados, para manter o controle sobre as contas e os dados de acesso à plataforma. Rastreabilidade: RF-013, RF-016, RF-017, RF-018, RF-019, RF-020; RN-001, RN-009, RN-013, RN-016, RN-017, RN-018.
Critérios de aceite:
    • CA01. Dado que o Administrador está autenticado e possui permissão, quando acessar a lista de usuários, então o sistema apresenta os registros que ele está autorizado a consultar.
    • CA02. Dado que o Administrador aplica filtros disponíveis, quando executar a busca, então o sistema exibe os registros correspondentes aos critérios informados.
    • CA03. Dado que o Administrador altera dados permitidos de um usuário, quando salvar, então o sistema valida e registra a alteração.
    • CA04. Dado que o Administrador consulta as informações de uma conta, quando os dados forem exibidos, então a senha não é apresentada em texto legível.
    • CA05. Dado que um usuário está cadastrado, quando seus dados forem consultados, então o sistema mantém uma conta individual por pessoa, sem compartilhamento de credenciais.
    • CA06. Dado que o Administrador realiza uma operação sensível em uma conta, quando a operação for concluída, então ela fica disponível para auditoria.
    • CA07. Dado que um usuário não possui permissão de Administrador ou a permissão específica necessária, quando tentar gerenciar contas de terceiros, então o sistema nega a operação.
    • CA08. Dado que o Administrador precisa gerenciar um Atendente, quando cadastrar, consultar, alterar ou atualizar seus dados cadastrais e funcionais, então o sistema permite realizar essas operações conforme as permissões definidas.
HU12 — Validação de campos cadastrais críticos
Como usuário que preenche um cadastro, quero que o sistema valide os campos críticos, para evitar inconsistências nos dados registrados. Rastreabilidade: RF-021; RN-021, RN-024; RNF-007.
Critérios de aceite:
    • CA01. Dado que o usuário preenche um campo CPF, quando informar valor com formato ou dígito verificador inválido, então o sistema rejeita o valor e sinaliza o erro.
    • CA02. Dado que o usuário informa um CRP, quando o formato não for válido, então o sistema sinaliza o erro; a validação profissional segue também o fluxo de validação de CRP previsto para ativação do Psicólogo.
    • CA03. Dado que o usuário informa um e-mail em formato inválido ou já associado a outra conta quando a unicidade for exigida, quando tentar salvar, então o sistema rejeita o valor.
    • CA04. Dado que o usuário informa telefone fora do formato brasileiro esperado, quando tentar salvar, então o sistema sinaliza o erro.
    • CA05. Dado que o usuário informa data de nascimento inválida ou incompatível com a idade declarada, quando tentar salvar, então o sistema rejeita os dados inconsistentes.
    • CA06. Dado que o usuário corrige os campos inválidos, quando os dados passarem nas validações aplicáveis, então o sistema permite prosseguir com o cadastro ou alteração.
HU13 — Auditoria de operações sensíveis
Como Administrador com permissão, quero consultar os logs de auditoria, para acompanhar operações sensíveis realizadas no sistema. Rastreabilidade: RF-018, RF-019, RF-059; RN-017, RN-018, RN-020, RN-035; RNF-009, RNF-010, RNF-011.
Critérios de aceite:
    • CA01. Dado que uma operação sensível foi realizada, quando o sistema registrar o evento, então a persistência do log ocorre em até 500 ms, conforme o requisito não funcional de desempenho de auditoria.
    • CA02. Dado que um log é consultado, quando seus detalhes forem exibidos, então devem conter, quando aplicável, usuário responsável, data e hora, operação realizada e dados alterados.
    • CA03. Dado que o Administrador possui a permissão necessária, quando consultar os logs, então o sistema permite filtrar os registros conforme os recursos disponíveis.
    • CA04. Dado que um log existe, quando qualquer perfil tentar editá-lo ou excluí-lo, então o sistema impede a operação.
    • CA05. Dado que um log está dentro do prazo de retenção aplicável, quando for consultado, então permanece disponível conforme os requisitos de guarda.
    • CA06. Dado que ocorreu solicitação, entrega, restrição ou visualização de prontuário psicológico, quando o evento for registrado, então o log permite identificar solicitante, paciente, psicólogo responsável, data e hora, tipo de operação e fundamento da restrição, quando houver.
    • CA07. Dado que houve tentativa de autenticação de dois fatores, quando o evento for concluído, então seu resultado fica rastreável.
HU14 — Gestão de profissionais
Como Administrador, quero cadastrar, consultar, alterar e gerenciar profissionais, para manter os registros profissionais da clínica atualizados. Rastreabilidade: RF-021, RF-022, RF-033; RN-017, RN-021, RN-031; RNF-013.
Critérios de aceite:
    • CA01. Dado que o Administrador está autenticado e autorizado, quando informar os dados obrigatórios de um novo profissional, então o sistema registra o cadastro profissional.
    • CA02. Dado que existe um profissional cadastrado, quando o Administrador consultar ou alterar dados permitidos, então o sistema exibe as informações autorizadas e salva as alterações válidas.
    • CA03. Dado que o profissional cadastrado é um psicólogo, quando o Administrador solicitar a ativação da conta, então o sistema exige a validação do CRP antes de ativá-la.
    • CA04. Dado que a consulta automática à base externa do CFP não estiver disponível, quando for necessário validar um CRP, então o sistema permite a validação manual pelo Administrador, sem ativar cadastros com CRP inválido.
    • CA05. Dado que já existe um profissional cadastrado com determinado CRP, quando houver tentativa de cadastrar outro com o mesmo CRP, então o sistema rejeita o cadastro duplicado.
    • CA06. Dado que uma operação sensível foi realizada sobre o cadastro profissional, quando o registro de auditoria for consultado, então a operação deve estar rastreável conforme as regras de auditoria.
    • CA07. Dado que um psicólogo é inativado ou administrativamente bloqueado, quando a alteração de status for efetivada, então o sistema encerra os vínculos ativos com pacientes, registrando o motivo conforme as regras de encerramento de vínculo.
    • CA08. Dado que os vínculos de um psicólogo foram encerrados por inativação ou bloqueio administrativo, quando o processo terminar, então o sistema preserva os históricos e comunica os pacientes afetados.
    • CA09. Dado que os vínculos de um psicólogo foram encerrados por inativação ou bloqueio, quando o processo for concluído, então a clínica pode avaliar a continuidade do cuidado sem que o sistema apague o histórico anterior.
    • CA10. Dado que ocorreu apenas bloqueio temporário de autenticação, quando esse evento for aplicado, então o sistema não encerra os vínculos profissionais por esse motivo.
HU15 — Perfil profissional
Como Psicólogo, quero consultar e atualizar meu próprio perfil profissional, para manter minhas informações profissionais atualizadas. Rastreabilidade: RF-023; RN-016, RN-021; RNF-013.
Critérios de aceite:
    • CA01. Dado que o Psicólogo está autenticado, quando acessar seu perfil profissional, então o sistema exibe seus próprios dados conforme as permissões aplicáveis.
    • CA02. Dado que o Psicólogo altera dados permitidos do próprio perfil, quando salvar, então o sistema valida e registra as alterações.
    • CA03. Dado que o Psicólogo tenta alterar dados do perfil de outro profissional sem autorização, quando salvar, então o sistema nega a operação.
    • CA04. Dado que uma alteração de perfil é classificada como sensível, quando for concluída, então a operação fica disponível para auditoria.
    • CA05. Dado que a alteração envolver informação profissional sujeita a validação específica, quando for solicitada, então o sistema aplica a validação correspondente antes de efetivá-la.
HU16 — Área de atuação profissional
Como Psicólogo, quero informar e gerenciar minha área de atuação, para manter meu perfil profissional atualizado. Rastreabilidade: RF-024; RN-016; RNF-018.
Critérios de aceite:
    • CA01. Dado que o Psicólogo está autenticado, quando acessar a seção de área de atuação, então o sistema exibe as opções disponíveis.
    • CA02. Dado que o Psicólogo seleciona uma ou mais áreas disponíveis, quando salvar, então o sistema associa as áreas ao seu perfil.
    • CA03. Dado que uma nova área de atuação é cadastrada no sistema, quando o Psicólogo acessar a seção, então a nova opção fica disponível conforme a configuração da plataforma.
    • CA04. Dado que o Psicólogo remove uma área de seu perfil, quando salvar, então o sistema atualiza as associações correspondentes.
HU17 — Gestão administrativa de pacientes
Como Administrador, Atendente ou Psicólogo autorizado, quero cadastrar, consultar e atualizar dados administrativos de pacientes, para manter os registros necessários à prestação do serviço. Rastreabilidade: RF-021, RF-025; RN-022, RN-023, RN-024; RNF-013.
Critérios de aceite:
    • CA01. Dado que o usuário possui permissão para cadastrar pacientes, quando informar os campos obrigatórios válidos, então o sistema registra o paciente como cadastro administrativo.
    • CA02. Dado que um paciente está cadastrado, quando um usuário autorizado consultar ou atualizar seus dados, então o sistema exibe ou altera apenas os campos permitidos para esse perfil.
    • CA03. Dado que o paciente tem menos de 18 anos, quando o cadastro for concluído, então deve existir responsável legal cadastrado e atualizado.
    • CA04. Dado que o cadastro administrativo do paciente foi concluído, quando nenhuma conta de acesso tiver sido solicitada ou criada, então o paciente permanece registrado sem que isso crie automaticamente credenciais de login.
    • CA05. Dado que um usuário não possui permissão para acessar determinado registro, quando tentar consultá-lo ou alterá-lo, então o sistema nega a operação.
HU18 — Cadastro do responsável legal
Como usuário autorizado, quero cadastrar e associar o responsável legal a um paciente menor de idade, para manter formalmente registrada a relação de representação legal. Rastreabilidade: RF-026; RN-024, RN-025.
Critérios de aceite:
    • CA01. Dado que o usuário possui permissão, quando informar os dados obrigatórios de identificação e contato do responsável legal, então o sistema registra o responsável e o associa ao paciente menor de 18 anos.
    • CA02. Dado que o paciente tem menos de 18 anos, quando o cadastro administrativo for concluído, então o sistema exige que exista responsável legal cadastrado e atualizado.
    • CA03. Dado que um responsável legal foi associado ao paciente, quando um usuário autorizado consultar o cadastro, então o vínculo entre ambos é exibido.
    • CA04. Dado que o responsável legal consta apenas como registro cadastral, quando tentar acessar funcionalidades autenticadas, então o sistema não concede acesso sem que exista uma conta própria e válida para ele.
    • CA05. Dado que o responsável legal já possui identidade própria no sistema, quando for associado a outro paciente sob sua representação, então o sistema mantém sua identidade independente da conta do paciente.
HU19 — Criação de conta de acesso do paciente
Como Administrador, quero criar uma conta de acesso para um paciente quando isso for necessário ou solicitado nas situações previstas, para permitir que ele utilize as funcionalidades autenticadas da plataforma. Rastreabilidade: RF-035; RN-001, RN-002, RN-004, RN-005, RN-006, RN-008.
Critérios de aceite:
    • CA01. Dado que o Administrador está autenticado e autorizado, quando houver uma situação prevista para criação de conta do paciente, então o sistema permite criar uma conta individual associada ao registro administrativo correto.
    • CA02. Dado que o paciente não solicitou ou não necessita de funcionalidades autenticadas, quando seu cadastro administrativo for realizado, então o sistema não cria automaticamente uma conta de acesso.
    • CA03. Dado que a conta do paciente foi criada, quando forem definidas as credenciais iniciais, então a senha provisória deve ser alterada no primeiro acesso.
    • CA04. Dado que a conta do paciente será criada por ele ter atingido a maioridade, quando o cadastro for processado, então o sistema considera as regras de transição para maioridade.
    • CA05. Dado que já existe uma conta de acesso do paciente, quando houver nova solicitação de criação, então o sistema evita a duplicação da identidade.
HU20 — Criação de conta de acesso do responsável legal
Como Administrador, quero criar uma conta própria para o responsável legal, para que ele possa acessar as funcionalidades autorizadas sem compartilhar a identidade do paciente. Rastreabilidade: RF-036; RN-001, RN-002, RN-004, RN-025.
Critérios de aceite:
    • CA01. Dado que o Administrador está autenticado e autorizado, quando criar uma conta para o responsável legal, então o sistema estabelece uma identidade de acesso própria, separada da conta do paciente.
    • CA02. Dado que a conta do responsável legal foi criada, quando forem definidas as credenciais iniciais, então o sistema exige alteração da senha provisória no primeiro acesso.
    • CA03. Dado que o responsável legal possui conta própria, quando for associado a um ou mais pacientes sob sua representação legal, então o sistema preserva a distinção entre sua identidade e a identidade de cada paciente.
    • CA04. Dado que um usuário tenta compartilhar ou mesclar as contas do responsável e do paciente, quando solicitar a operação, então o sistema impede essa associação de identidades.
    • CA05. Dado que não existe conta de acesso do responsável legal, quando seu cadastro administrativo for criado, então o sistema não gera credenciais automaticamente.
HU21 — Transição do paciente para a maioridade
Como paciente que está completando 18 anos, quero que o sistema trate corretamente a mudança da representação legal, para que meus dados e acessos passem a respeitar minha condição de maior de idade. Rastreabilidade: RF-034, RF-035, RF-036; RN-006, RN-032, RN-033, RN-036.
Critérios de aceite:
    • CA01. Dado que o paciente completa 18 anos, quando o sistema identificar a mudança de idade, então registra ou sinaliza a transição para aplicação das regras de maioridade.
    • CA02. Dado que o paciente atingiu a maioridade, quando a transição for processada, então o vínculo de representação legal é encerrado e o acesso do responsável ao prontuário é revogado, salvo autorização expressa do paciente.
    • CA03. Dado que o paciente já possui conta de acesso, quando atingir a maioridade, então essa conta permanece válida, respeitadas as demais regras de segurança.
    • CA04. Dado que o paciente não possui conta de acesso, quando atingir a maioridade, então o sistema sinaliza à clínica a necessidade de avaliar a criação de uma conta, sem criar credenciais automaticamente.
    • CA05. Dado que a representação legal foi encerrada, quando os dados cadastrais do responsável forem tratados, então permanecem armazenados pelos prazos legais e só podem ser anonimizados ou eliminados conforme as regras de retenção aplicáveis.
    • CA06. Dado que o paciente autoriza expressamente a manutenção do acesso do responsável, quando essa autorização for registrada e validada, então o sistema mantém apenas o acesso expressamente autorizado, conforme as regras aplicáveis.
HU22 — Isolamento dos dados de pacientes por psicólogo
Como Psicólogo, quero acessar informações confidenciais somente dos pacientes vinculados a mim, para preservar o sigilo das informações dos demais pacientes. Rastreabilidade: RF-030; RN-022, RN-034; RNF-013, RNF-014.
Critérios de aceite:
    • CA01. Dado que o Psicólogo está autenticado, quando consultar a lista de pacientes sob seu atendimento, então o sistema exibe somente pacientes com vínculo ativo ou outro acesso expressamente autorizado pelas regras aplicáveis.
    • CA02. Dado que o Psicólogo tenta acessar informações confidenciais de paciente sem vínculo autorizado por URL ou identificador direto, quando efetuar a requisição, então o sistema nega o acesso.
    • CA03. Dado que o Psicólogo manipula parâmetros de consulta para tentar acessar dados de outro paciente, quando efetuar a requisição, então o sistema aplica as mesmas verificações de autorização e nega o acesso indevido.
    • CA04. Dado que uma tentativa de acesso indevido é classificada como evento sensível, quando o sistema registrá-la, então a ocorrência fica disponível para auditoria.
HU23 — Múltiplos vínculos paciente–psicólogo
Como paciente, quero poder ter vínculos com mais de um Psicólogo quando forem autorizados, para permitir atendimentos por diferentes profissionais. Rastreabilidade: RF-029; RN-028, RN-030; RNF-013.
Critérios de aceite:
    • CA01. Dado que o paciente possui vínculo ativo com um Psicólogo, quando for criado e autorizado vínculo com outro profissional, então o sistema registra o novo vínculo sem eliminar o anterior.
    • CA02. Dado que o paciente possui múltiplos vínculos, quando um usuário autorizado consultar os registros, então cada vínculo é apresentado separadamente.
    • CA03. Dado que um vínculo foi criado, quando os detalhes forem consultados, então devem constar data de início, motivo e responsável pela criação.
    • CA04. Dado que um vínculo é encerrado, quando o histórico de vínculos for consultado, então o registro encerrado permanece preservado.
    • CA05. Dado que já existe vínculo ativo entre o mesmo paciente e o mesmo Psicólogo, quando houver tentativa de criar uma duplicata sem encerrar ou corrigir o vínculo existente, então o sistema impede a duplicidade.
HU24 — Criação de vínculo paciente–psicólogo
Como Administrador ou Psicólogo autorizado, quero criar um vínculo entre paciente e Psicólogo, para formalizar a relação de atendimento. Rastreabilidade: RF-027, RF-029; RN-028, RN-030, RN-016.
Critérios de aceite:
    • CA01. Dado que o usuário está autenticado e possui permissão, quando criar um vínculo entre paciente e Psicólogo, então o sistema registra a relação.
    • CA02. Dado que o vínculo foi criado, quando seu registro for consultado, então contém data de início, motivo e responsável pela criação.
    • CA03. Dado que o paciente já possui vínculo ativo com outro Psicólogo, quando um novo vínculo for autorizado, então o sistema registra ambos sem eliminar o anterior.
    • CA04. Dado que já existe vínculo ativo entre o mesmo paciente e o mesmo Psicólogo, quando o usuário tentar criar uma duplicata, então o sistema impede o registro duplicado.
    • CA05. Dado que um usuário não possui permissão para criar vínculos, quando tentar executar a operação, então o sistema nega a ação.
    • CA06. Dado que a criação de vínculo for uma operação sensível, quando for concluída, então a operação fica rastreável para auditoria.
HU25 — Encerramento de vínculo paciente–psicólogo
Como Administrador ou Psicólogo autorizado, quero encerrar um vínculo entre paciente e Psicólogo, para registrar o fim da relação de atendimento e preservar o histórico. Rastreabilidade: RF-028, RF-055; RN-029, RN-034.
Critérios de aceite:
    • CA01. Dado que existe um vínculo ativo, quando um usuário autorizado solicitar seu encerramento, então o sistema registra o encerramento.
    • CA02. Dado que o vínculo foi encerrado, quando seu registro for consultado, então contém data de encerramento, motivo e responsável pela ação.
    • CA03. Dado que o vínculo foi encerrado, quando o histórico de atendimentos for consultado por usuário autorizado, então os registros anteriores permanecem armazenados.
    • CA04. Dado que o vínculo foi encerrado, quando o Psicólogo tentar acessar informações confidenciais sem vínculo ou outra autorização aplicável, então o sistema aplica as restrições de acesso pertinentes.
    • CA05. Dado que um usuário não possui permissão para encerrar vínculos, quando tentar fazê-lo, então o sistema nega a operação.
    • CA06. Dado que o encerramento foi concluído, quando a operação for classificada como sensível, então ela fica registrada para auditoria.
HU26 — Atualização dos dados do responsável legal
Como usuário autorizado, quero consultar e atualizar os dados cadastrais do responsável legal, para manter as informações atualizadas e preservar o vínculo com o paciente. Rastreabilidade: RF-032; RN-024, RN-025, RN-033; RNF-013.
Critérios de aceite:
    • CA01. Dado que o usuário possui permissão, quando consultar o responsável legal associado ao paciente, então o sistema exibe os dados cadastrais permitidos.
    • CA02. Dado que o usuário autorizado altera dados permitidos do responsável legal, quando salvar, então o sistema valida e registra as alterações.
    • CA03. Dado que os dados do responsável foram alterados, quando o cadastro do paciente for consultado, então o vínculo entre paciente e responsável permanece íntegro.
    • CA04. Dado que um usuário não possui permissão, quando tentar alterar os dados do responsável legal, então o sistema nega a operação.
    • CA05. Dado que uma alteração cadastral é classificada como sensível, quando for concluída, então a operação fica disponível para auditoria.
Módulo 3 — Agenda e Atendimento
HU27 — Disponibilidade profissional
Como Psicólogo, quero informar e gerenciar minha disponibilidade, para permitir agendamentos em horários nos quais posso atender. Rastreabilidade: RF-037, RF-052.
Critérios de aceite:
    • CA01. Dado que o Psicólogo está autenticado, quando acessar a seção de disponibilidade, então o sistema exibe os horários já definidos.
    • CA02. Dado que o Psicólogo informa novos horários dentro dos limites de funcionamento da clínica, quando salvar, então o sistema registra a disponibilidade.
    • CA03. Dado que o Psicólogo remove um horário disponível, quando salvar, então esse horário deixa de ser oferecido para novos agendamentos.
    • CA04. Dado que o paciente consulta horários para agendamento, quando o sistema apresenta as opções, então exibe apenas horários disponíveis e compatíveis com o horário comercial configurado pela clínica.
HU28 — Consulta consolidada de agendas
Como Atendente ou Administrador autorizado, quero consultar as agendas dos profissionais, para acompanhar os agendamentos da clínica conforme minhas permissões. Rastreabilidade: RF-049; RN-016, RN-046; RNF-013.
Critérios de aceite:
    • CA01. Dado que o usuário possui permissão para consultar agendas, quando selecionar um profissional, então o sistema exibe os agendamentos correspondentes às permissões concedidas.
    • CA02. Dado que o usuário aplica filtro por período, quando efetuar a consulta, então o sistema apresenta apenas os agendamentos daquele período.
    • CA03. Dado que o usuário aplica filtro por situação, quando efetuar a consulta, então o sistema apresenta os agendamentos correspondentes à situação escolhida.
    • CA04. Dado que o Psicólogo tenta consultar a agenda de outro profissional sem autorização, quando efetuar a consulta, então o sistema nega o acesso.
    • CA05. Dado que o usuário consulta a agenda, quando os detalhes forem apresentados, então o sistema respeita as permissões do perfil e não revela informações clínicas não autorizadas.
HU29 — Agendamento de consulta
Como paciente com conta de acesso, quero solicitar ou realizar um agendamento, para marcar consulta com um Psicólogo disponível. Rastreabilidade: RF-037, RF-038, RF-052; RN-037; RNF-019.
Critérios de aceite:
    • CA01. Dado que o paciente está autenticado, quando acessar a área de agendamento, então o sistema apresenta horários disponíveis compatíveis com a disponibilidade profissional e o horário comercial da clínica.
    • CA02. Dado que o paciente seleciona um horário disponível, quando confirmar a solicitação, então o sistema registra o agendamento com a situação inicial prevista pelo fluxo da plataforma.
    • CA03. Dado que o horário selecionado não está disponível ou está fora do horário configurado pela clínica, quando o paciente tentar confirmar, então o sistema impede o registro.
    • CA04. Dado que o agendamento foi registrado, quando o paciente consultar seus agendamentos, então o novo registro é apresentado com sua situação atual.
    • CA05. Dado que o paciente ainda não possui conta de acesso, quando precisar realizar uma ação que exige autenticação, então o sistema não cria credenciais automaticamente e aplica o fluxo de criação de conta previsto.
HU30 — Confirmação de agendamento
Como Psicólogo ou Atendente autorizado, quero confirmar um agendamento, para formalizar a consulta. Rastreabilidade: RF-039; RN-016, RN-042.
Critérios de aceite:
    • CA01. Dado que existe um agendamento pendente, quando um usuário autorizado o consultar, então o sistema disponibiliza a opção de confirmação.
    • CA02. Dado que o usuário autorizado confirma o agendamento, quando salvar, então o sistema altera a situação para Confirmado.
    • CA03. Dado que o agendamento foi confirmado, quando for consultado posteriormente, então o sistema apresenta a situação atualizada.
    • CA04. Dado que o usuário não possui permissão para confirmar agendamentos, quando tentar executar a ação, então o sistema a nega.
    • CA05. Dado que um agendamento foi criado por remarcação, quando for confirmado, então a confirmação deve ser realizada novamente, sem herdar automaticamente a confirmação do agendamento anterior.
HU31 — Validação de conflitos de horário
Como Psicólogo, quero que o sistema impeça agendamentos conflitantes, para evitar sobreposição de consultas no mesmo horário. Rastreabilidade: RF-040; RN-037; RNF-019.
Critérios de aceite:
    • CA01. Dado que existe agendamento Pendente ou Confirmado para determinado horário do Psicólogo, quando outro agendamento com sobreposição for solicitado, então o sistema impede a criação ou confirmação conflitante.
    • CA02. Dado que existe conflito de horário, quando a operação for rejeitada, então o sistema informa que o horário não está disponível.
    • CA03. Dado que o sistema executa a validação de conflito, quando processar a solicitação, então deve atender ao limite de desempenho definido no RNF-019.
    • CA04. Dado que os agendamentos existentes foram cancelados ou substituídos por remarcação, quando o sistema avaliar conflitos, então esses registros não são considerados para impedir o novo agendamento.
    • CA05. Dado que não existe conflito com agendamentos Pendente ou Confirmado, quando todas as demais validações forem atendidas, então o sistema permite prosseguir com a operação.
HU32 — Cancelamento de agendamento
Como paciente, Psicólogo ou Atendente autorizado, quero cancelar um agendamento, para registrar que a consulta não ocorrerá naquele horário. Rastreabilidade: RF-041, RF-042, RF-043, RF-050; RN-038, RN-039, RN-040, RN-041, RN-017.
Critérios de aceite:
    • CA01. Dado que existe um agendamento, quando paciente, Psicólogo ou Atendente autorizado solicitar o cancelamento, então o sistema registra a operação.
    • CA02. Dado que o cancelamento foi registrado, quando os detalhes forem consultados, então exibem o responsável e a data e hora do cancelamento.
    • CA03. Dado que o usuário informa o motivo do cancelamento, quando confirmar a operação, então o sistema registra o motivo; se nenhum motivo for informado, o sistema mantém os demais dados exigidos.
    • CA04. Dado que o cancelamento foi realizado, quando o sistema aplicar a política configurada pela clínica, então classifica o cancelamento como antecipado ou tardio conforme os critérios vigentes.
    • CA05. Dado que um agendamento foi cancelado, quando o histórico for consultado, então o registro anterior permanece preservado.
    • CA06. Dado que as informações de cancelamento são utilizadas para políticas de cobrança ou bloqueio, quando a clínica tiver configurado tais políticas, então os dados necessários para sua aplicação ficam disponíveis aos usuários autorizados.
    • CA07. Dado que um usuário não possui permissão para cancelar o agendamento, quando tentar realizar a operação, então o sistema a nega.
    • CA08. Dado que o cancelamento é concluído, quando a operação for classificada como sensível, então fica disponível para auditoria.
    • CA09. Dado que o usuário tenta registrar um não comparecimento por meio do fluxo de cancelamento, quando realizar a operação, então o sistema mantém a distinção entre cancelamento e não comparecimento.
HU33 — Registro de não comparecimento
Como Psicólogo ou Atendente autorizado, quero registrar o não comparecimento do paciente, para manter o histórico da situação do agendamento. Rastreabilidade: RF-043, RF-044, RF-050; RN-040, RN-041, RN-017.
Critérios de aceite:
    • CA01. Dado que existe um agendamento e o horário previsto passou sem comparecimento do paciente, quando um usuário autorizado registrar a ausência, então o sistema classifica o registro como Não Comparecimento.
    • CA02. Dado que o não comparecimento foi registrado, quando o agendamento for consultado, então a situação aparece distinta de um cancelamento antecipado ou tardio.
    • CA03. Dado que o não comparecimento foi registrado, quando o histórico do paciente for consultado por usuário autorizado, então a ocorrência permanece associada ao agendamento correspondente.
    • CA04. Dado que o atendimento foi realizado ou o horário do agendamento ainda não passou, quando houver tentativa de registrar não comparecimento, então o sistema impede o registro.
    • CA05. Dado que a clínica possui política de cobrança ou bloqueio configurada para não comparecimentos, quando a ocorrência for registrada, então seus dados permitem aplicar essa política por meio do fluxo autorizado.
    • CA06. Dado que o não comparecimento foi registrado, quando a operação for classificada como sensível, então fica disponível para auditoria.
HU34 — Remarcação de consulta
Como usuário autorizado, quero remarcar um agendamento confirmado, para alterar o horário da consulta mantendo o histórico da alteração. Rastreabilidade: RF-040, RF-045, RF-051; RN-037, RN-042, RN-043; RNF-021.
Critérios de aceite:
    • CA01. Dado que existe um agendamento confirmado, quando o usuário autorizado solicitar remarcação, então o sistema permite selecionar novo horário disponível.
    • CA02. Dado que a remarcação for confirmada, quando o histórico for consultado, então existe um novo registro de agendamento associado à alteração.
    • CA03. Dado que a remarcação foi concluída, quando o histórico for consultado, então o registro anterior permanece preservado.
    • CA04. Dado que o limite de remarcações configurado pela clínica foi atingido, quando o usuário tentar realizar uma nova remarcação, então o sistema impede a operação.
    • CA05. Dado que o novo horário conflita com outro agendamento Pendente ou Confirmado do Psicólogo, quando o usuário tentar concluir a remarcação, então o sistema rejeita a operação.
    • CA06. Dado que a remarcação foi registrada, quando o fluxo for concluído, então o novo agendamento fica pendente de nova confirmação pelo Psicólogo ou Atendente.
    • CA07. Dado que a remarcação foi concluída, quando a operação for classificada como sensível, então fica disponível para auditoria.
HU35 — Registro de atendimento realizado
Como Psicólogo, quero registrar um atendimento realizado, para manter o histórico das sessões do paciente. Rastreabilidade: RF-046, RF-047, RF-048; RN-044, RN-045, RN-034; RNF-012, RNF-022.
Critérios de aceite:
    • CA01. Dado que o Psicólogo está autenticado e autorizado, quando registrar um atendimento, então o sistema exige a associação a um agendamento confirmado.
    • CA02. Dado que o atendimento é registrado, quando salvo, então fica vinculado ao paciente correspondente e ao Psicólogo responsável.
    • CA03. Dado que o Psicólogo informa data futura para o atendimento, quando tentar salvar, então o sistema impede o registro.
    • CA04. Dado que o atendimento foi salvo, quando o histórico for consultado por usuário autorizado, então o registro aparece associado ao agendamento, paciente e profissional correspondentes.
    • CA05. Dado que o usuário não possui autorização para registrar atendimento naquele contexto, quando tentar salvar o registro, então o sistema nega a operação.
    • CA06. Dado que o registro de atendimento contém informações clínicas, quando for armazenado ou consultado, então o sistema respeita as permissões e o sigilo profissional aplicáveis.
HU36 — Consulta ao histórico de atendimentos
Como usuário autorizado, quero consultar o histórico de atendimentos, para acompanhar os registros anteriores conforme minhas permissões. Rastreabilidade: RF-054, RF-055; RN-022, RN-029, RN-034; RNF-012, RNF-022.
Critérios de aceite:
    • CA01. Dado que o usuário está autenticado e possui permissão, quando consultar o histórico de um paciente, então o sistema apresenta somente os registros autorizados para seu perfil.
    • CA02. Dado que o vínculo entre paciente e Psicólogo foi encerrado, quando o histórico for consultado por usuário autorizado, então os registros anteriores permanecem preservados.
    • CA03. Dado que o usuário não possui permissão para acessar o histórico de um paciente, quando tentar consultá-lo, então o sistema nega o acesso.
    • CA04. Dado que o Psicólogo consulta o histórico de um paciente, quando não houver vínculo ou outra autorização aplicável para acesso às informações confidenciais, então o sistema aplica a restrição pertinente.
    • CA05. Dado que o paciente possui conta de acesso e a funcionalidade está autorizada, quando consultar seu próprio histórico, então o sistema exibe apenas as informações liberadas para seu perfil.
    • CA06. Dado que a consulta ao prontuário ou histórico é classificada como operação rastreável, quando ocorrer, então o evento fica disponível para auditoria conforme as regras de acesso ao prontuário.
HU37 — Configuração das políticas de cancelamento e ausência
Como Administrador, quero configurar as políticas de cancelamento e não comparecimento da clínica, para que a classificação e o tratamento dessas ocorrências sigam critérios definidos. Rastreabilidade: RF-050; RN-040, RN-041, RN-016, RN-017.
Critérios de aceite:
    • CA01. Dado que o Administrador possui permissão, quando configurar o prazo mínimo para cancelamento antecipado, então o sistema salva o critério para classificar os cancelamentos.
    • CA02. Dado que o Administrador opta por adotar cobrança, quando configurar percentuais para cancelamento tardio ou não comparecimento, então o sistema registra os valores definidos.
    • CA03. Dado que o Administrador opta por adotar bloqueio de pacientes, quando definir os critérios aplicáveis, então o sistema registra esses critérios para uso nos fluxos pertinentes.
    • CA04. Dado que uma ocorrência de cancelamento ou ausência é processada, quando existir política correspondente configurada, então o sistema disponibiliza os dados necessários à aplicação dessa política.
    • CA05. Dado que o Administrador não possui permissão para alterar políticas, quando tentar salvar mudanças, então o sistema nega a operação.
HU38 — Configuração do limite de remarcações
Como Administrador, quero definir o número máximo de remarcações permitidas por agendamento, para aplicar a política de remarcação da clínica. Rastreabilidade: RF-051; RN-043, RN-016, RN-017.
Critérios de aceite:
    • CA01. Dado que o Administrador está autorizado, quando definir um limite máximo de remarcações, então o sistema salva a configuração.
    • CA02. Dado que um agendamento alcançou o limite configurado, quando um usuário tentar remarcar novamente, então o sistema impede a nova remarcação.
    • CA03. Dado que o Administrador altera a configuração, quando salvar, então o sistema passa a utilizar o limite atualizado conforme as regras aplicáveis.
    • CA04. Dado que um usuário sem permissão tenta alterar o limite, quando salvar, então o sistema nega a operação.
HU39 — Configuração do horário comercial da clínica
Como Administrador, quero configurar os dias e horários de funcionamento da clínica, para limitar a disponibilidade e os agendamentos aos períodos definidos. Rastreabilidade: RF-037, RF-038, RF-052; RN-016, RN-017.
Critérios de aceite:
    • CA01. Dado que o Administrador possui permissão, quando definir os dias da semana e as faixas de horário de funcionamento, então o sistema salva a configuração.
    • CA02. Dado que o horário comercial foi configurado, quando o sistema apresentar horários para agendamento, então oferece apenas horários compatíveis com essa configuração e com a disponibilidade do Psicólogo.
    • CA03. Dado que um usuário tenta agendar fora dos períodos definidos, quando confirmar a solicitação, então o sistema impede o agendamento.
    • CA04. Dado que o Administrador altera o horário comercial, quando salvar, então o sistema utiliza a nova configuração nos cálculos de disponibilidade e nos agendamentos futuros.
    • CA05. Dado que um usuário não possui permissão para alterar o horário comercial, quando tentar fazê-lo, então o sistema nega a operação.
Módulo 4 — Dados do Paciente, Solicitações e Prontuário
HU40 — Acesso do paciente aos próprios dados
Como paciente com conta de acesso, quero consultar meus próprios dados, para acessar minhas informações dentro dos limites permitidos pelo sistema. Rastreabilidade: RF-031; RN-023; RNF-014.
Critérios de aceite:
    • CA01. Dado que o paciente está autenticado, quando acessar sua área de dados, então o sistema exibe somente as informações e funcionalidades autorizadas ao perfil.
    • CA02. Dado que o paciente tenta acessar dados de outro paciente por URL, identificador direto ou alteração de parâmetros, quando efetuar a requisição, então o sistema nega o acesso.
    • CA03. Dado que o paciente tenta executar operação fora de suas permissões, quando solicitar a operação, então o sistema a impede.
    • CA04. Dado que uma tentativa de acesso indevido é classificada como sensível, quando for registrada, então a ocorrência fica disponível para auditoria.
HU41 — Encaminhamento de solicitações de informações por terceiros
Como usuário autorizado da clínica, quero registrar e encaminhar solicitações de informações sobre pacientes feitas por responsáveis legais ou terceiros, para que sejam avaliadas por pessoal competente antes de qualquer divulgação. Rastreabilidade: RF-053; RN-027, RN-034, RN-017.
Critérios de aceite:
    • CA01. Dado que o usuário está autenticado e autorizado, quando registrar uma solicitação de informação sobre paciente feita por terceiro, então o sistema cria um registro da solicitação.
    • CA02. Dado que a solicitação foi registrada, quando o sistema realizar o encaminhamento, então a direciona aos canais de atendimento da clínica.
    • CA03. Dado que a solicitação foi encaminhada, quando o registro for consultado, então é possível acompanhar seu encaminhamento e avaliação.
    • CA04. Dado que a solicitação aguarda avaliação, quando for processada pelo sistema, então nenhuma informação confidencial é divulgada automaticamente.
    • CA05. Dado que a solicitação é registrada ou atualizada, quando a operação for classificada como sensível, então fica disponível para auditoria.
HU42 — Solicitação de acesso ao prontuário pelo responsável legal
Como responsável legal de paciente menor de 18 anos, quero registrar uma solicitação de acesso ao prontuário psicológico, para que o pedido seja avaliado e tratado pelo Psicólogo responsável. Rastreabilidade: RF-056, RF-059; RN-026, RN-034, RN-035.
Critérios de aceite:
    • CA01. Dado que o responsável legal está identificado e associado a paciente menor de 18 anos, quando solicitar acesso ao prontuário pelo sistema, então o sistema registra a solicitação.
    • CA02. Dado que a solicitação foi registrada, quando o fluxo de atendimento for iniciado, então o sistema a encaminha ao Psicólogo responsável para avaliação e processamento.
    • CA03. Dado que a solicitação está pendente de avaliação, quando o responsável consultar seu estado, então o sistema informa o andamento permitido, sem liberar automaticamente o prontuário.
    • CA04. Dado que uma solicitação de acesso é registrada, quando o evento for salvo, então os dados necessários à rastreabilidade ficam disponíveis para auditoria.
    • CA05. Dado que o solicitante não foi identificado ou não está vinculado como responsável legal, quando tentar registrar o pedido por esse fluxo, então o sistema impede o prosseguimento até que a autorização seja verificada.
HU43 — Entrega mediada do prontuário psicológico
Como Psicólogo responsável, quero processar uma solicitação de acesso e realizar a entrega mediada do prontuário, para atender ao pedido conforme as regras de acesso e sigilo. Rastreabilidade: RF-057, RF-059; RN-026, RN-034, RN-035.
Critérios de aceite:
    • CA01. Dado que existe uma solicitação registrada e avaliada, quando o Psicólogo autorizar a entrega, então o sistema permite disponibilizar o conteúdo por documento PDF ou visualização on-line.
    • CA02. Dado que o conteúdo será entregue, quando o sistema preparar a disponibilização, então exclui documentos que constituam registro documental privativo do Psicólogo e que não façam parte do prontuário abrangido pelo acesso.
    • CA03. Dado que o prontuário foi entregue, quando a operação for concluída, então o sistema registra data e hora, conteúdo disponibilizado, identidade do destinatário e confirmação/assinatura de recebimento quando aplicável ao fluxo.
    • CA04. Dado que a entrega foi realizada, quando a solicitação ou o prontuário for consultado por usuário autorizado, então a entrega permanece rastreável.
    • CA05. Dado que o usuário não é o Psicólogo responsável nem possui autorização para realizar a entrega, quando tentar disponibilizar o prontuário, então o sistema nega a operação.
HU44 — Registro de restrição de acesso ao prontuário
Como Psicólogo responsável, quero registrar a decisão de restringir o acesso do responsável legal ao prontuário quando houver fundamento aplicável, para preservar a segurança do paciente e documentar a justificativa. Rastreabilidade: RF-058, RF-059; RN-026, RN-034, RN-035.
Critérios de aceite:
    • CA01. Dado que existe uma solicitação de acesso ao prontuário, quando o Psicólogo identificar uma situação prevista para restrição, então o sistema permite registrar a decisão de restringir o acesso.
    • CA02. Dado que uma restrição é registrada, quando o Psicólogo salvar a decisão, então deve informar fundamento específico, como suspeita de abuso pelo responsável, conflito de guarda com determinação judicial ou risco iminente à segurança do menor.
    • CA03. Dado que a restrição foi registrada, quando a operação for consultada por usuário autorizado, então o sistema apresenta a decisão e sua justificativa conforme as permissões aplicáveis.
    • CA04. Dado que a restrição foi registrada, quando a operação for concluída, então o sistema registra os dados necessários à auditoria do prontuário.
    • CA05. Dado que um usuário sem autorização tenta registrar ou modificar a restrição, quando executar a operação, então o sistema nega a ação.
HU45 — Solicitação de exclusão ou anonimização de dados pessoais
Como paciente ou representante legal autorizado, quero registrar uma solicitação de exclusão ou anonimização de dados pessoais, para que ela seja avaliada conforme as obrigações legais aplicáveis. Rastreabilidade: RF-060; RN-018, RN-034, RN-036.
Critérios de aceite:
    • CA01. Dado que o paciente ou representante legal está identificado e autorizado, quando solicitar exclusão ou anonimização de dados, então o sistema registra a solicitação para avaliação.
    • CA02. Dado que a solicitação foi registrada, quando for processada, então o sistema não elimina automaticamente dados que devam ser mantidos por obrigação legal ou prazo de guarda aplicável.
    • CA03. Dado que existem dados clínicos sujeitos a retenção, quando a solicitação for avaliada, então o tratamento respeita os prazos de guarda e as condições previstas para prontuários psicológicos.
    • CA04. Dado que existem logs de auditoria ou dados de pesquisa já anonimizados, quando a solicitação for processada, então o sistema não viola a imutabilidade dos logs nem aplica exclusão incompatível com a regra de dados de pesquisa anonimizados.
    • CA05. Dado que a solicitação foi tratada, quando o registro for consultado por usuário autorizado, então é possível identificar a solicitação e seu tratamento sem divulgar dados além do permitido.
Módulo 5 — Pesquisa e Ética
HU46 — Criação e definição de recorte de pesquisa
Como Psicólogo autorizado, quero criar uma pesquisa e definir os critérios e recortes dos dados a utilizar, para conduzir estudos dentro das condições previstas pela plataforma. Rastreabilidade: RF-061, RF-062, RF-063; RN-048, RN-049; RN-016.
Critérios de aceite:
    • CA01. Dado que o Psicólogo possui permissão para criar pesquisas, quando cadastrar uma nova pesquisa, então o sistema a registra no estado Rascunho.
    • CA02. Dado que a pesquisa está em Rascunho, quando o responsável definir critérios ou recortes, então o sistema armazena essas definições associadas à pesquisa.
    • CA03. Dado que a pesquisa utiliza dados de pacientes, quando os dados forem disponibilizados para processamento ou análise, então já devem estar anonimizados.
    • CA04. Dado que os resultados da pesquisa forem apresentados ou exportados, quando contiverem dados de pacientes, então não podem expor nome, CPF, RG ou outros identificadores diretos.
    • CA05. Dado que um usuário não possui permissão para criar ou configurar pesquisas, quando tentar realizar essas operações, então o sistema nega a ação.
    • CA06. Dado que uma pesquisa foi criada ou alterada em operação classificada como sensível, quando a operação for concluída, então fica disponível para auditoria conforme as regras aplicáveis.
HU47 — Submissão e avaliação ética de pesquisa
Como Psicólogo responsável pela pesquisa, quero submeter a pesquisa à avaliação ética e acompanhar suas transições de estado, para obter aprovação antes do início da coleta de dados. Rastreabilidade: RF-064, RF-065, RF-066; RN-047, RN-052; RNF-024.
Critérios de aceite:
    • CA01. Dado que a pesquisa está em Rascunho, quando o responsável submetê-la, então o sistema altera o estado para Submetida; também deve permitir o cancelamento nesse estado.
    • CA02. Dado que a pesquisa está Submetida, quando iniciar a avaliação ética, então o sistema permite a transição para Em Avaliação; também deve permitir o cancelamento conforme o fluxo definido.
    • CA03. Dado que a pesquisa está Em Avaliação, quando uma decisão ética for registrada, então o sistema permite a transição para Aprovada, Rejeitada ou Cancelada, de acordo com a decisão válida.
    • CA04. Dado que a pesquisa foi Rejeitada, quando o responsável optar por fazer ajustes, então o sistema permite retornar a Rascunho; também deve permitir o cancelamento.
    • CA05. Dado que a pesquisa está Aprovada, quando a coleta for iniciada, então o sistema permite a transição para Em Coleta; antes do início da coleta, também deve permitir o cancelamento conforme o fluxo definido.
    • CA06. Dado que a pesquisa está Em Coleta, quando for registrada decisão válida de conclusão, suspensão ou cancelamento, então o sistema altera o estado para Concluída, Suspensa ou Cancelada, respectivamente.
    • CA07. Dado que a pesquisa está Suspensa, quando houver autorização para retomada, então o sistema permite retornar a Em Coleta; se houver cancelamento, registra Cancelada.
    • CA08. Dado que a pesquisa não está Aprovada pelo Comitê de Ética, quando o responsável tentar iniciar a coleta de dados, então o sistema impede a operação.
    • CA09. Dado que for solicitada uma transição de estado não prevista, ou uma alteração de pesquisa Concluída ou Cancelada, quando o sistema validar a operação, então rejeita a transição.
    • CA10. Dado que uma transição de estado foi concluída, quando o registro for consultado, então a mudança permanece rastreável e auditável.
HU48 — Registro do Termo de Consentimento Livre e Esclarecido (TCLE)
Como responsável autorizado pela pesquisa, quero registrar o TCLE associado à pesquisa e ao paciente participante, para documentar o consentimento para participação. Rastreabilidade: RF-067; RN-050; RNF-025.
Critérios de aceite:
    • CA01. Dado que existe uma pesquisa aprovada e o participante consentiu, quando o responsável registrar o TCLE, então o sistema o associa à pesquisa e ao paciente correspondente.
    • CA02. Dado que o TCLE foi registrado, quando o registro for consultado por usuário autorizado, então é possível verificar sua associação à pesquisa e ao participante.
    • CA03. Dado que o participante não possui TCLE registrado, quando o sistema verificar sua inclusão na pesquisa, então não o considera participante elegível para coleta que exija esse consentimento.
    • CA04. Dado que o TCLE foi registrado, quando houver consulta posterior, então o registro permanece rastreável conforme as permissões aplicáveis.
    • CA05. Dado que o TCLE foi registrado ou alterado em operação sensível, quando a operação for concluída, então fica disponível para auditoria.
HU49 — Registro e respeito à opção de não participação em pesquisas
Como paciente, quero registrar que não desejo participar de pesquisas, para que minha decisão seja respeitada nas pesquisas futuras. Rastreabilidade: RF-068, RF-069; RN-051; RNF-026.
Critérios de aceite:
    • CA01. Dado que o paciente está autenticado ou que sua decisão é registrada por fluxo autorizado, quando declarar que não deseja participar de pesquisas, então o sistema registra a opção.
    • CA02. Dado que o paciente registrou a opção de não participação, quando consultar suas preferências por meio de funcionalidade autorizada, então o sistema apresenta a decisão atual.
    • CA03. Dado que o paciente optou por não participar, quando uma pesquisa futura selecionar dados para inclusão, então o sistema exclui os dados desse paciente conforme a regra de opt-out.
    • CA04. Dado que o paciente alterou posteriormente sua decisão por fluxo válido, quando o sistema processar a alteração, então aplica a decisão atual às pesquisas futuras, respeitando os registros e obrigações aplicáveis.
    • CA05. Dado que a decisão de participação foi registrada ou alterada, quando a operação for sensível, então fica disponível para auditoria.
HU50 — Tratamento de pesquisas quando o Psicólogo responsável é inativado
Como Administrador ou responsável autorizado pela gestão da pesquisa, quero que o sistema trate as pesquisas sob responsabilidade de Psicólogo inativado ou administrativamente bloqueado, para preservar a conformidade ética e a rastreabilidade dos estudos. Rastreabilidade: RF-065, RF-070; RN-052, RN-053; RNF-024.
Critérios de aceite:
    • CA01. Dado que um Psicólogo responsável por uma pesquisa em Rascunho ou Submetida foi inativado ou administrativamente bloqueado, quando o sistema processar o evento, então a pesquisa pode ser cancelada ou transferida para outro pesquisador habilitado.
    • CA02. Dado que o Psicólogo responsável por pesquisa Aprovada ou Em Coleta foi inativado ou administrativamente bloqueado, quando o evento for processado, então a pesquisa é suspensa até que haja decisão sobre transferência ou cancelamento conforme o Comitê de Ética.
    • CA03. Dado que a pesquisa está Concluída, quando o Psicólogo responsável for inativado, então a pesquisa permanece arquivada e seu histórico é preservado.
    • CA04. Dado que a responsabilidade por uma pesquisa é transferida, quando a transferência for concluída, então o sistema registra a alteração para fins de auditoria.
    • CA05. Dado que o Psicólogo responsável foi inativado ou administrativamente bloqueado, quando o tratamento de suas pesquisas for processado, então a clínica comunica o Comitê de Ética conforme a regra aplicável.
    • CA06. Dado que ocorreu apenas bloqueio temporário de autenticação do Psicólogo, quando esse evento for aplicado, então não são acionadas as regras de inativação ou bloqueio administrativo de pesquisas.
