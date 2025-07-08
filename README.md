**0 -> BASE DE DADOS**

 A base de dados utilizada foi a série histórica com o
 saldo total de admissões e desligamentos no município do Rio de Janeiro, mais
 especificamente no setor do comércio, desde janeiro de 2016 a dezembro de 2023.
 ![image](https://github.com/user-attachments/assets/16f24084-7f4d-4103-9d50-4a4f2da5ab27)

Visualmente, é possível identificar uma repetição de ciclos, ou seja, o fenômeno
 estudado possui natureza sazonal. Também se revelam diversos picos e vales acentuados na
 série, além de uma tendência crescente que é possível visualizar no software Microsoft Excel.
 Essas duas informações são de extrema importância pois permite logo no início selecionar
 aqueles modelos mais adequados.
 
 É possível identificar uma mudança nos padrões no período de fevereiro até agosto de
 2020. Este intervalo atípico pode ser explicado pelo período de pandemia de COVID-19, na  qual houve perdas humanas irreparáveis mas também muitas consequências socioeconômicas.
 Sendo assim, é compreensível a queda acentuada de geração de empregos nesse período.
 Portanto, dado que este período demonstra um fenômeno totalmente fora dos padrões,
 foi optado pelo recorte do ano de 2020. Tal decisão, apesar de diminuir a amostra, torna a
 análise mais realista. Esse recorte foi crucial para a modelagem utilizando os modelos
 autoregressivos. A Figura abaixo contém a série com o **recorte:**
![image](https://github.com/user-attachments/assets/f44f5db6-3c33-4e07-b4e0-5f2e02a10d81)





**1 -> ANÁLISE COM O MÉTODO HOLT - WINTERS**

 A primeira análise foi feita direcionada para algum modelo que se adequasse a
 tendência e sazonalidade. Sendo assim, o primeiro teste ocorreu utilizando o método de
 amortecimento exponencial triplo ou Holt-Winters. A modelagem foi feita no Microsoft
 Excel, sendo utilizado para a modelagem os últimos 3 anos da série temporal, 2021, 2022 e
 2023. Os coeficientes utilizados foram: α = 0,9, ß = 0,1 e γ = 0,9 pois apresentaram os
 menores erros percentuais.
 
 O processo de aplicação do modelo se deu, primeiramente, pela definição dos índices
 de sazonalidade iniciais com os dados observados do ano de 2021. Para esses índices iniciais
 utilizou-se: (dado registrado no mês / média dos dados do ano). Para 2022 e 2023 foi utilizado
 a equação It = γ*(Rt / Nt) + (1-γ)It-L. Para o primeiro valor de Nt foi utilizado o valor real do
 período de dezembro de 2021 que é 981, daí em diante foi utilizado a equação Nt = α(Rt / It-l)
 + (1-α)(Nt-1 + Tt-1). Para o primeiro valor de Tt foi utilizado 0, daí em diante foi utilizado a
 equação Tt = ß*(Nt- Nt-1) + (1-ß)*Tt-1. Foi feita uma previsão para o período de janeiro de
 2024 tendo como resultado um saldo negativo de-5522.
   ![image](https://github.com/user-attachments/assets/47fed5d5-5535-485e-b88c-d8a7a6347843)



**2 -> ANÁLISE COM ARIMA**

 A segunda análise se deu em razão da busca por uma modelo mais preciso, que
 gerasse resultados com um menor erro percentual. Na busca por um método de previsão mais
 robusto, optou-se por utilizar o método ARIMA, sendo adequado para séries que apresentam
 picos mais acentuados. A escolha também se deu pela análise da FAC e FACP, que será
 detalhada mais à frente.
 
 Para o uso do modelo ARIMA foi utilizada a linguagem Python na plataforma Google
 Colab, que permite utilizar bibliotecas variadas do Python em um ambiente colaborativo.
 Primeiramente, foi realizada a análise dos lags da FAC (Função de Autocorrelação Parcial) e
 FACP (Função de Autocorrelação Parcial) para analisar o comportamento de dependência
 serial.
 ![image](https://github.com/user-attachments/assets/f2af188a-50f3-464e-87b2-54df6ef8f812)

  Logo após, foi feito o teste de Fuller para estacionariedade, sendo necessário saber se
 será utilizado a etapa de diferenciação. Com o teste, foi indicado a não estacionariedade,
 sendo necessário realizar a etapa de diferenciação.
 Emsequência, foi utilizado o recurso auto arima, que consiste no programa gerar os
 resultados otimizados de p, d e q para o modelo, sendo esses p = 1, q = 1 e d = 3. Portanto, foi
 utilizado o modelo ARIMA(1,1,3). Com base nisso, foi feita uma previsão para 5 períodos no
 futuro, o que equivale no momento de escrita deste artigo aos meses de janeiro, fevereiro,
 março, abril e maio do ano de 2024. Para medir o desempenho do modelo foi analisado o erro percentual médio absoluto nos últimos 5 períodos de 2023. A Figura 5 contém a análise feita:
 ![image](https://github.com/user-attachments/assets/f3ff5615-0c22-4d11-ba6c-08048bbd1cbd)


 **3 -> ANÁLISE COM SARIMA**

  A terceira análise, assim como a segunda, teve como objetivo encontrar um modelo
 mais preciso que o anterior. Porém, considerando a sazonalidade da série, foi escolhido para
 teste o modelo SARIMA, que é apropriado pois a série temporal analisada possui uma
 repetição de padrões em ciclos.
 
 Para o uso do modelo SARIMA, também foi utilizado a linguagem Python no
 ambiente do Google Colab. O processo de aplicação do modelo foi similar ao anterior, sendo
 a análise das FAC e FACP já realizadas na aplicação do ARIMA assim como o teste Fuller e a
 diferenciação. Os valores de p, d, q, P, D e Q foram ajustados para o melhor resultado
 possível, sendo p = 1, d = 1, q = 2, P = 1, D = 1 e Q = 1. Como a sazonalidade é de 12
 períodos, temos o modelo SARIMA(1,1,2)(1,1,1)12. Com base nisso, foi feita uma previsão
 para 5 períodos no futuro, o que equivale no momento de escrita deste artigo aos meses de
 janeiro, fevereiro, março, abril e maio do ano de 2024. Para medir o desempenho do modelo
 foi analisado o erro percentual médio absoluto nos últimos 5 períodos de 2023. A Figura 6
 contém a análise feita:

![image](https://github.com/user-attachments/assets/da018ba4-d05d-4544-98d2-aea972c48c16)

**CONCLUSÃO**


![image](https://github.com/user-attachments/assets/aa84d360-08d9-4a2a-b11d-ad95c0d1b1f6)




 
