
Métricas:
--------

Todo nodo depois de um decided(h-1) 
                 Algum processamento do bloco h-1
                 espera um tempo  (sincronizar ou remuneração?)

                 entra no próximo propose (h)      -> inicio do blocktime      (b)
	           Proposer envia proposta         -> Inicio do consensus time do proposer (cp)
	           Nodos recebem a proposta        -> Inicio do consensus time do nodo     (cn)
	          Consenso
	           Nodo entra em commit (decided)  -> Fim dos tempos                       (f)
 
                                                 Cada flecha é uma entrada no log do nodo  

Processamento do log

        Para cada nodo, 
             Para cada altura
                  Amostra de blocktime:    f-b                        [obs:  qual a relacao com 
                  Amostra de consensustime:   proposer   f-cp         [obs:  inclui tempo do propose, mas so proponente]
                                              nodo       f-cn         [obs:  nao inclui o tempo do propose no prop até commit no nodo]

        Para cada nodo, 
             Para cada altura
                  Amostra de 2Nblocktime   f (no nodo) -  cp (do proposer)      

Estudo
------
Fig 1.a
       Plota amostras de consensustime de cada proposer

Fig 1.b 
       Plota p todos nodos
             o 2Nblocktime


Experimentos          
------------
Usa blocktime



???  Qual a relacao de blocktime com 2Nblocktime                                               





Conteúdo dos diretórios:
-----------------------

Os nomes de arquivos com dados se repetem pelas pastas

            leaderblocktimecdf.svg           block-time medido em cada proponente;   CDF 

            decideddeviationallcdf.svg       consensus-time medido em todos nodos de todos proponentes;    CDF             decideddeviationnodecdf.svg      consensus-time medido em todos nodos separado por proponente;   CDF



10x   
    Topologia da aws, com latencias fixas conforme a matriz.

    Experimento da Fig 1.a :  cada proponente mede seu block-time

		leaderblocktimecdf.svg  apresenta a CDF dos pontos da fig1.a
 
    Experimento da Fig 1.b :  Cada nodo mede consensus-time de cada proposer

		decideddeviationallcdf.svg    CDF com todos os pontos da fig 1 b     		decideddeviationnodecdf.svg   CDF com pontos relativos a cada proposer na fig 1 b Aws-static

     Topologia da aws, com latencias fixas conforme a matriz.

     Relativo aa Figura 3

     Pastas Run 1 a Run 5 sao repetições do experimento.

     Em cada Run:
             Alg1 a Alg6: são execuções com sequencias de proponentes reconfiguradas conforme o algoritmo proposto
             Def1 : seria o baseline, road-robin  (sem algoritmo proposto)
             Rem2 : seria a técnica que remove dois nodos mais lentos
     Para cada diretorio destes, repete as medidas como descritas antes
            leaderblocktimecdf.svg           block-time medido em cada proponente
            decideddeviationallcdf.svg       consensus-time medido em todos nodos de todos proponentes            decideddeviationnodecdf.svg      consensus-time medido em todos nodos separado por proponente               

Aws
     
     Topologia da was, mas latencias tem media (M) e variação (V), valor adotado em cada msg 
                               é uniformemente distribuído em [ M-V,M+V ]
     Relativo aa Fig 4  
     Em cada Run:
             Alg1 a Alg5: mesma sequencia acima, com 5 estágios.
             Def1 e Def2 são duas execuções rotativas baseline
     Para cada diretorio destes, repete as medidas como descritas antes



Como avaliar:
------------

Teriamos que ver, por exemplo

            AWS-static/Run1a5/Alg1/decideddeviationallcdf.svg    próximo a
            AWS-static/Run1a5/Def1/decideddeviationallcdf.svg 

            AWS-static/Run1a5/Alg6/decideddeviationallcdf.svg    melhor que
            AWS-static/Run1a5/Def1/decideddeviationallcdf.svg 

            AWS-static/Run1a5/Rem2/decideddeviationallcdf.svg    melhor que os outros


Algo análogo para AWS/...


        
 




     