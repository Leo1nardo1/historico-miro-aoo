REQUISITOS NÃO FUNCIONAIS
Módulo 1 — Autenticação e Segurança
RNF-001 — Segurança de armazenamento de senhas
As senhas devem ser armazenadas utilizando algoritmo de hash criptográfico adequado, não sendo permitido seu armazenamento em texto puro.
Característica: Segurança.
RNF-002 — Hash bcrypt
O sistema deve utilizar o algoritmo bcrypt para armazenamento das senhas, com custo mínimo igual a 10.
Característica: Segurança.
RNF-003 — Proteção de dados em trânsito e repouso
Os dados protegidos pelo sistema devem ser transmitidos e armazenados utilizando mecanismos adequados de criptografia, compatíveis com a sensibilidade das informações.
Característica: Segurança.
RNF-004 — Proteção contra acesso não autorizado
O sistema deve garantir que informações e funcionalidades sejam acessíveis somente aos usuários devidamente autenticados e autorizados, respeitando seus perfis e permissões.
Característica: Segurança.
RNF-005 — Controle de sessões
O sistema deve impedir que a mesma conta mantenha sessões autenticadas simultâneas em dispositivos diferentes, como medida de proteção contra compartilhamento indevido de contas (RN-001).
Característica: Segurança.
RNF-006 — Desempenho da autenticação
O processo de autenticação deve ser concluído em até 2 segundos em condições normais de carga.
Característica: Eficiência de desempenho.
RNF-007 — Mensagens de erro seguras
As mensagens de erro devem ser claras e orientativas, sem revelar informações sensíveis ou permitir inferências indevidas sobre a existência de contas.
Característica: Capacidade de interação / Segurança.
RNF-008 — Recuperação de senha
O processo de recuperação de senha deve ser concluído em no máximo três etapas para o usuário, sem comprometer a segurança da conta.
Característica: Capacidade de interação / Segurança.

Módulo 2 — Administração, Perfis e Auditoria
RNF-009 — Desempenho do registro de auditoria
Os registros de auditoria devem ser persistidos em até 500 milissegundos após a conclusão da operação sensível, sem comprometer a integridade dos registros.
Característica: Eficiência de desempenho / Confiabilidade.
RNF-010 — Imutabilidade dos logs
Os logs de auditoria devem possuir mecanismos que impeçam sua alteração ou exclusão, inclusive por usuários com privilégios administrativos.
Característica: Segurança / Confiabilidade.
RNF-011 — Retenção dos logs
Os logs de auditoria devem ser mantidos por no mínimo cinco anos, respeitando os requisitos legais aplicáveis.
Característica: Confiabilidade.
RNF-012 — Integridade do histórico de atendimento
O sistema deve preservar a integridade e a rastreabilidade dos registros históricos de atendimentos, mesmo após alterações ou encerramentos de vínculos entre pacientes e psicólogos.
Característica: Confiabilidade.

Módulo 3 — Profissionais e Pacientes
RNF-013 — Isolamento dos dados dos pacientes
O sistema deve garantir o isolamento dos dados entre pacientes e restringir o acesso às informações clínicas conforme os vínculos paciente–psicólogo e as permissões aplicáveis.
Característica: Segurança.
RNF-014 — Proteção contra acesso indevido por identificador
O sistema deve impedir o acesso não autorizado a informações de pacientes por meio da manipulação direta de identificadores, URLs ou parâmetros de consulta.
Característica: Segurança.
RNF-015 — Proteção do sigilo profissional
Os dados clínicos dos pacientes devem possuir mecanismos técnicos de proteção contra acesso, divulgação, alteração ou utilização não autorizados, compatíveis com o sigilo profissional.
Característica: Segurança.
RNF-016 — Proteção de dados pessoais
O tratamento de dados pessoais pelo sistema deve observar os princípios e requisitos aplicáveis da Lei Geral de Proteção de Dados Pessoais (LGPD).
Característica: Segurança / Confiabilidade.
RNF-017 — Proteção das informações profissionais
O sistema deve restringir o acesso às informações cadastrais e profissionais dos psicólogos, permitindo sua consulta ou alteração somente por usuários autorizados.
Característica: Segurança.
RNF-018 — Extensibilidade das áreas de atuação
O sistema deve permitir a inclusão de novas áreas de atuação profissional sem exigir alterações significativas na estrutura existente do modelo de dados.
Característica: Flexibilidade / Manutenibilidade.

Módulo 4 — Agenda e Atendimento
RNF-019 — Desempenho da validação de agenda
A validação de conflitos de horário deve ser concluída em até 1 segundo após a solicitação de agendamento, em condições normais de carga.
Característica: Eficiência de desempenho.
RNF-020 — Configuração das políticas de ausência
As políticas relacionadas a cancelamento tardio e não comparecimento devem poder ser configuradas pela clínica sem alteração do código-fonte.
Característica: Flexibilidade.
RNF-021 — Configuração do limite de remarcações
O limite de remarcações deve poder ser configurado pela clínica sem alteração do código-fonte.
Característica: Flexibilidade.
RNF-022 — Integridade do histórico diante de falhas
O sistema deve preservar os registros históricos de atendimento diante de falhas operacionais, indisponibilidades ou interrupções inesperadas, permitindo sua recuperação conforme os requisitos de backup e recuperação definidos neste documento.
Característica: Confiabilidade.

Módulo 5 — Pesquisa e Ética
RNF-023 — Desempenho da anonimização
O processo de anonimização deve ser concluído em até 5 segundos para o volume de dados definido para a pesquisa. O volume utilizado para verificar esse desempenho deve ser documentado e considerado nos testes do sistema.
Característica: Eficiência de desempenho.
RNF-024 — Integridade do fluxo da pesquisa
O sistema deve garantir que as transições de estado da pesquisa sejam controladas e auditáveis, não permitindo transições incompatíveis com o fluxo definido na RN-052.
Característica: Confiabilidade / Segurança.
RNF-025 — Integridade do consentimento
O registro do Termo de Consentimento Livre e Esclarecido (TCLE) deve permanecer associado à pesquisa e ao paciente correspondente, preservando sua integridade e rastreabilidade.
Característica: Confiabilidade.
RNF-026 — Registro do opt-out
O registro da opção do paciente de não participar de pesquisas deve ser preservado de forma íntegra e rastreável, permitindo verificar a opção registrada.
Característica: Segurança / Confiabilidade.

Módulo 6 — Requisitos Transversais
RNF-027 — Acessibilidade
A interface deve seguir as diretrizes de acessibilidade WCAG 2.1, nível AA.
Característica: Capacidade de interação.
RNF-028 — Compatibilidade com navegadores
O sistema deve ser acessível pelas duas últimas versões estáveis dos navegadores Chrome, Firefox, Edge, Safari e Brave.
Característica: Portabilidade / Compatibilidade.
RNF-029 — Responsividade
A interface deve adaptar-se adequadamente a dispositivos móveis, tablets e computadores, mantendo a legibilidade das informações e o acesso às funcionalidades disponíveis.
Característica: Portabilidade / Capacidade de interação.
RNF-030 — Integração com serviço de e-mail
O sistema deve permitir integração com serviço externo de e-mail por SMTP ou mecanismo equivalente para envio de notificações.
Característica: Compatibilidade.
RNF-031 — Tolerância à falha do serviço de e-mail
Em caso de indisponibilidade do serviço externo de e-mail, o sistema deve preservar as notificações pendentes para posterior reenvio, evitando sua perda.
Característica: Confiabilidade.
RNF-032 — Disponibilidade
O sistema deve apresentar disponibilidade mínima de 99,5% durante o horário comercial configurado pela clínica, considerando o período de apuração definido para avaliação desse requisito.
Característica: Confiabilidade.
RNF-033 — Backup
O sistema deve realizar backup automático diário dos dados necessários à recuperação do sistema, incluindo os registros essenciais para a continuidade das operações.
Característica: Confiabilidade.
RNF-034 — Recuperação de falhas
O sistema deve permitir a recuperação dos dados e a retomada das operações em até 4 horas após uma falha crítica, com RPO (Recovery Point Objective) máximo de 24 horas e RTO (Recovery Time Objective) máximo de 4 horas.
Característica: Confiabilidade.
RNF-035 — Capacidade de usuários simultâneos
O sistema deve suportar 500 usuários simultâneos sem degradação superior a 20% no tempo de resposta de referência, definido como 2 segundos para operações de leitura e 3 segundos para operações de escrita, nas condições de teste estabelecidas para o projeto.
Característica: Eficiência de desempenho.
RNF-036 — Evolução modular
O sistema deve permitir a inclusão de novos módulos ou funcionalidades sem exigir alterações significativas nos módulos existentes.
Característica: Flexibilidade / Manutenibilidade.
RNF-037 — Qualidade estrutural do software
A arquitetura do sistema deve favorecer baixo acoplamento, alta coesão e separação adequada de responsabilidades, facilitando a manutenção e a evolução do software.
Característica: Manutenibilidade.
RNF-038 — Tratamento de falhas críticas
O sistema deve registrar e tratar falhas críticas de forma a reduzir o risco de perda ou corrupção do histórico de atendimentos e permitir a identificação das ocorrências.
Característica: Confiabilidade / Segurança.
RNF-039 — Desempenho do 2FA
A validação do segundo fator de autenticação deve ser concluída em até 3 segundos, desconsiderando o tempo necessário para o recebimento de códigos ou confirmações por serviços externos.
Característica: Eficiência de desempenho / Segurança.
RNF-040 — Expiração do link de redefinição de senha
O link de redefinição de senha deve expirar em até 30 minutos após sua geração, conforme a RN-008.
Característica: Segurança.
RNF-041 — Uso único do link de redefinição
Um link de redefinição de senha deve ser utilizado uma única vez, não podendo ser reutilizado após sua utilização bem-sucedida.
Característica: Segurança.