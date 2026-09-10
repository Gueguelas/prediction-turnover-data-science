# Dicionário de Dados — Material recebido (Aula 1)

Estas são as bases que a Marina (RH) conseguiu extrair rapidamente dos sistemas internos. Repare que **nenhuma delas contém, sozinha, o quadro completo de colaboradores** (quem está ativo, quem saiu, dados cadastrais completos) — isso é algo que vocês vão precisar identificar e solicitar.

Todas as bases têm o campo `nIdPessoa`, um identificador anonimizado de colaborador (dado como nome/CPF foi removido por LGPD), que pode ser usado para relacionar registros entre bases diferentes.

## FtAbsenteismoMensalRH.csv

Espelho de ponto diário de um grupo pequeno de colaboradores (apenas ~82 no recorte enviado). A maioria das linhas representa **dias normais de trabalho** (sem ausência); só uma fração das linhas (`cTipo`/`cOcorrencia` preenchidos) representa uma ausência de fato (atestado médico, falta injustificada etc.).


| Coluna                         | Descrição                                                                                                    |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| nCodColigada / nChapa / cChapa | Identificadores internos de filial e matrícula                                                               |
| dAnoMes                        | Mês de referência do registro                                                                                |
| nQtdeAbsenteismo               | Preenchido **apenas** quando há uma ausência real (junto com `cTipo`); nulo em dias normais                  |
| cTipo                          | Tipo da ausência (HORASMEDICAS, HORASLEGAIS, HORASINJUSTIFICADAS etc.) — nulo em dias sem ausência           |
| cCodOcorrencia / cOcorrencia   | Código e descrição da ocorrência (ex.: "ATESTADO MÉDICO", "FALTA INJUSTIFICADA") — nulo em dias sem ausência |
| cSistemaOrigem                 | Sistema de origem do registro (majoritariamente `ForPonto`, um sistema de ponto digital)                     |
| nHoraPrevista                  | Minutos previstos de jornada no dia (preenchido nos dias normais, nulo nos dias de ausência)                 |
| nIdPessoa                      | Identificador do colaborador                                                                                 |


⚠️ **Cobertura baixa e provavelmente enviesada:** só ~82 colaboradores aparecem nesta base, quase certamente porque apenas eles são monitorados por esse sistema de ponto digital específico — o resto da empresa deve registrar ponto por outro meio, não capturado nesta extração. Vale que os alunos questionem se esse padrão de absenteísmo pode ser generalizado para toda a empresa (resposta: não, com segurança).

## FtAcidentesRH.csv

Um registro por acidente de trabalho ou de trajeto.


| Coluna                                       | Descrição                                |
| -------------------------------------------- | ---------------------------------------- |
| dDataAcidente / nPeriodoAcidente             | Data e período (turno) do acidente       |
| nComAfastamento / nComObito                  | Indicadores se houve afastamento / óbito |
| cTipoAcidente / cCausaAcidente / cUtilizaEPI | Tipo, causa do acidente e uso de EPI     |
| nDiasDebito / nDiasPerdidos                  | Dias de afastamento decorrentes          |
| nIdPessoa                                    | Identificador do colaborador             |




## FtHoraExtraRH.csv

Um registro por ocorrência de hora extra.


| Coluna                  | Descrição                                |
| ----------------------- | ---------------------------------------- |
| dAnoMes                 | Mês de referência                        |
| cCodEvento / cDescricao | Código e descrição do tipo de hora extra |
| nReferencia / nValor    | Quantidade de horas e valor pago         |
| nIdPessoa               | Identificador do colaborador             |




## FtHorasIrregularesRH.csv

Um registro por ocorrência de hora trabalhada fora do padrão esperado (ex.: interjornada).


| Coluna                                                 | Descrição                               |
| ------------------------------------------------------ | --------------------------------------- |
| dOcorrencia / nDiaOcorrencia                           | Data da ocorrência                      |
| nMinutosJornada / nMinutosTrabalhados / nMinutosExtras | Minutos previstos, trabalhados e extras |
| cTipoOcorrencia / cTipoOcorrenciaDetalhes              | Classificação da irregularidade         |
| nIdPessoa                                              | Identificador do colaborador            |




## FtMovimentoSalarialRH.csv

Um registro por movimentação salarial (reajuste, promoção, etc.).


| Coluna                 | Descrição                              |
| ---------------------- | -------------------------------------- |
| dMudanca / dReferencia | Data de referência da mudança salarial |
| nValor / nPerc         | Valor e percentual do reajuste         |
| cMotivo                | Motivo da movimentação                 |
| nIdPessoa              | Identificador do colaborador           |




## FtDemitidosTurnoverRH.csv

Registros **apenas** de colaboradores que já saíram da empresa, com diversos dados cadastrais no momento do desligamento (cargo, seção, idade, tempo de casa, salário etc.).


| Coluna                                                       | Descrição                                            |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| cCargo / cFuncao / cSecao                                    | Cargo, função e área do colaborador                  |
| cEstadoCivil / cSexo / cCor / cEscolaridade / cNacionalidade | Dados demográficos                                   |
| cFaixasTempoDeCasa / cFaixasIdade / nIdade                   | Tempo de casa e idade (faixas e valor)               |
| nSalarioTotal / cPosicaoFaixaSalarial                        | Salário e posição na faixa salarial                  |
| cIniciativaDemissao                                          | Se a demissão foi **voluntária** ou **involuntária** |
| cDescricaoTipoDemissao / cDescricaoMotivoDemissao            | Tipo e motivo detalhado da saída                     |
| dDataDemissao / dDataAdmissao                                | Datas de desligamento e admissão                     |
| nIdPessoa                                                    | Identificador do colaborador                         |


# Dicionário de Dados — Material recebido (Aula 2)

## FtFuncionarioRH_amostra.csv
Cadastro de colaboradores (recorte de 24.000 colaboradores da base geral). Uma linha por colaborador.

| Coluna | Descrição |
|---|---|
| nIdPessoa | Identificador do colaborador (chave para relacionar com as demais bases) |
| cSituacao | Situação cadastral do colaborador no momento da extração (Ativo, Demitido, Férias, Aviso Prévio, etc.) |
| cCargo / cFuncao / cSecao | Cargo, função e área do colaborador |
| cEstadoCivil / cSexo / cCor / cEscolaridade / cGeracaoNascimento | Dados demográficos |
| cEstadoEndereco / cCidadeEndereco | Localização do colaborador |
| cTurno | Turno de trabalho |
| nTempoDeCasaAnos / cFaixasTempoDeCasa | Tempo de casa (valor e faixa) |
| nIdade / cFaixasIdade | Idade (valor e faixa) |
| nSalarioTotal / nRemuneracaoTotal / cPosicaoFaixaSalarial | Remuneração e posição salarial |
| nNrDependentes | Número de dependentes |
| nCodColigada / nCodFilial / EMPRESA / cMes / nAno / dAnoMes | Metadados administrativos (filial, competência) |

## Lembrete: a informação de quem pediu demissão já está com vocês

Não recebemos um arquivo novo com essa informação — ela já está na base `FtDemitidosTurnoverRH.csv`, recebida na Aula 1. Revisem o dicionário daquela aula: o campo `cIniciativaDemissao` (Voluntário / Involuntário) é o que vocês precisam para identificar quem pediu para sair.

Para montar a tabela completa (cadastro + quem pediu demissão), será necessário cruzar `FtFuncionarioRH_amostra.csv` com `FtDemitidosTurnoverRH.csv` pelo `nIdPessoa`.




## MotivosDemitidos.csv (material de apoio — não é para dar merge!)

Uma lista solta com **156.511 motivos de desligamento**, sem identificador de colaborador. Não representa as mesmas pessoas das outras bases (é um recorte de um período/população maior da empresa toda). Serve apenas como **referência da distribuição geral de motivos de saída** — útil para contexto, mas não deve ser combinada por posição de linha com nenhuma outra base, pois isso criaria associações falsas entre colaborador e motivo.