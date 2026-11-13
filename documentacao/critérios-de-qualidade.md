Critérios de Qualidade (ISO/IEC 25019 / ISO/IEC 25010)
Segurança
Critério Verificável :As senhas dos usuários devem ser armazenadas utilizando criptografia de hash (ex: bcrypt) e o acesso às rotas restritas deve ser validado por token de sessão. 
Evidência no Modelo:RNF-002 e Diagrama de Classes (classe Usuario e métodos de autenticação). 
Eficiência de Desempenho
Critério Verificável:As consultas e buscas realizadas no sistema devem processar e retornar os resultados em menos de 2 segundos sob condições normais.
Evidência no Modelo:RNF-004, Diagrama de Sequência (UC34) e índices nas tabelas do DER. 
Confiabilidade 
Critério Verificável:O sistema deve impedir 100% das tentativas de transações inválidas ou duplicadas (como agendamentos no mesmo horário) e tratar exceções sem perda de dados. 
Evidência no Modelo:Máquina de Estados de Agendamento, fluxos do UC20 e integridade referencial no DER. 
Capacidade de Interação
Critério Verificável:Os fluxos das tarefas principais devem ser concluídos em no máximo 4 etapas, fornecendo feedback visual imediato em caso de sucesso ou erro. 
Evidência no Modelo:Diagramas de Atividades (UC20 e UC34) e especificação de fluxos alternativos nos Casos de Uso. 
Manutenibilidade
Critério Verificável:O projeto arquitetural deve manter separação estrita e modular entre as camadas de Apresentação, Regra de Negócio e Persistência.
Evidência no Modelo:Diagrama de Componentes e Diagrama de Pacotes. 