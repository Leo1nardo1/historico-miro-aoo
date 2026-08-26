INOVAÇÃO:

Laboratório de Pesquisa Integrado (LAPI) para Análise Epidemiológica em Psicologia.
Um ambiente integrado de pesquisa epidemiológica em Psicologia que permite transformar dados anonimizados provenientes da operação da plataforma em estudos quantitativos controlados controlados, submetidos a um fluxo de aprovação ética por meio de estatísticas intercambiáveis onde a distribuição ou probabilidade não muda se a ordem é trocada.
O LAPI muda a finalidade dos dados. Em vez de os registros servirem somente para operação administrativa e acompanhamento dos atendimentos, eles passam a constituir uma base anonimizada para investigação epidemiológica e produção de conhecimento científico.
Motor de recortes semânticos (Pesquisador define uma população de interesse utilizando as seguintes características):
tags associadas aos atendimentos;
área de atuação do psicólogo;
faixa etária;
período dos atendimentos;
outros atributos não identificáveis.
Por exemplo: "Quero analisar a frequência de determinadas categorias de atendimento entre pacientes entre 18 a 25 anos atendidos por psicólogos da área de psicologia clínica durante determinado período."
A partir daí o sistema faria o recorte automaticamente, exportando os dados para um banco de dados ou Excel.
Fluxo de aprovação ética:
Cada pesquisa teria um estado, podendo ser eles em ordem: Rascunho → Em submissão → Em análise → Aprovada → Em execução → Concluída → Arquivada. Assim o sistema não permite que qualquer usuário consulte os dados epidemiológicos.
Precisariamos de uma modelagem de estado de aprovação ética para cada pesquisa criada.
Modo cego / anonimização:
O pesquisador não deve receber dados sensíveis dos indivíduos presentes na pesquisa, tanto psicologos quanto pacientes, mas sim algo semelhante a:
Paciente A7F3
Faixa etária: 18–25
Categoria: Ansiedade
Profissional: Psicologia Clínica
Período: 2026

Estudar a possibilidade de implementar o padrão strategy para os algoritmos estatísticos. A ideia principal é que possamos ter diferentes algoritmos de análise mantendo a mesma interface, para que posteriormente possamos adicionar outros métodos estatísticos sem precisar modificar toda a estrutura LAPI.