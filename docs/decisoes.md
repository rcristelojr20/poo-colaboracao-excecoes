# Decisoes da pratica A

1. Na falta de calibracao, qual funcao lanca, qual apenas propaga e qual recupera a falha? Responda para C++ e Python.

Em C++, a funcao adquirir verifica se a fonte esta calibrada e lanca FalhaCalibracao quando nao esta. A funcao lerServico apenas chama adquirir e deixa a falha passar. A funcao executarCiclo captura a falha e retorna "calibracao".

Em Python acontece a mesma coisa. A funcao adquirir lanca FalhaCalibracao, ler_servico apenas passa a excecao e executar_ciclo captura e retorna "calibracao".

2. Por que a captura de `FalhaCalibracao` vem antes da de `FalhaLeitura`? Quando a sessao e liberada em cada linguagem?

FalhaCalibracao vem antes porque ela e um tipo de FalhaLeitura. Se FalhaLeitura viesse primeiro, ela capturaria tambem a falha de calibracao.

No C++, a Sessao e liberada automaticamente quando sai do escopo. No Python, o finally garante que sessao.fechar() seja executado mesmo quando acontece uma falha.

3. Como `FonteNivel` e `FonteConstante` podem ser consultadas pelo mesmo contrato? Dê um exemplo observado em `make run`.

As duas fontes seguem a mesma interface IFonteLeitura, por isso podem ser usadas pelas mesmas funcoes.

No make run apareceu "Fonte simulada: 42.5 %", mostrando uma leitura da FonteConstante, e tambem apareceu "Leitura: 20", mostrando uma leitura da fonte de nivel.