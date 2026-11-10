Restrições
RES-001 — Limitação do escopo acadêmico
O projeto contempla a análise e a modelagem da plataforma, incluindo a especificação dos requisitos, a representação dos processos, a arquitetura conceitual e a estrutura de persistência. A documentação produzida não representa, por si só, a implementação ou a validação operacional de um sistema em ambiente de produção.
RES-002 — Dependência de serviços externos
Determinadas funcionalidades dependem da disponibilidade e das condições de acesso a serviços externos. A validação automatizada de registros profissionais depende da disponibilidade da fonte de consulta do CFP, enquanto o envio de notificações depende do serviço externo de e-mail configurado. A indisponibilidade desses serviços pode limitar temporariamente suas respectivas funcionalidades.
RES-003 — Limitação da atuação automatizada da plataforma
A plataforma tem como finalidade apoiar a organização administrativa, o gerenciamento das informações e os processos profissionais da clínica. Suas funcionalidades não substituem as decisões técnicas dos psicólogos nem a avaliação ética realizada pelas instâncias responsáveis.
RES-004 — Restrição ao uso de dados reais nas atividades acadêmicas
A documentação, os exemplos, as demonstrações e os testes acadêmicos do projeto não devem utilizar dados reais de pacientes ou informações clínicas identificáveis. Devem ser utilizados dados fictícios ou adequadamente anonimizados.
RES-005 — Dependência de parâmetros operacionais definidos pela organização
O funcionamento de determinadas classificações e políticas administrativas depende de parâmetros previamente definidos pela clínica. Enquanto esses valores não forem estabelecidos, não será possível determinar concretamente critérios como prazo de cancelamento antecipado, tolerância para não comparecimento e quantidade máxima de remarcações.
RES-006 — Limitação da especificação analítica do LAPI
A definição dos métodos estatísticos, dos algoritmos de análise e dos formatos de exportação dos resultados ainda depende de decisões de projeto. A utilização do padrão Strategy permanece como uma possibilidade arquitetural, não constituindo, por enquanto, uma decisão definitiva de implementação.