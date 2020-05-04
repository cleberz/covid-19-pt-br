<div class="section">
    <div>
    	<iframe id="splash" width="960" height="480" src="banners/splash.html"></iframe>
        <div style="top: 70px;font-size: 75px;font-weight: bold;">
        	O Que Acontece em Seguida?
       	</div>
		<div style="font-weight: 500;top: 140px;left: 10px;font-size: 29px;">
			COVID-19, Futuros Explicados com Simulações
		</div>
		<div style="font-weight: 100;top: 189px;left: 10px;font-size: 19px;line-height: 21px;">
			<b>
				🕐 Leitura/Simulações em 30 min
				&nbsp;&middot;&nbsp;
			</b>
			by
			<a href="https://scholar.google.com/citations?user=_wHMGkUAAAAJ&amp;hl=en">Marcel Salathé</a>
			(epidemiologista)
			&
			<a href="https://ncase.me/">Nicky Case</a>
			(arte/código)
		</div>
	</div>
</div>

"A única coisa a temer é o próprio medo" é um conselho estúpido.

Claro, não junte papel higiênico - mas se os governantes temem o próprio medo eles irão minimizar os reais perigos de "pânico em massa". O medo não é o problema, mas, sim, como nós *canalizamos* nosso medo. O medo nos dá energia para lidar com os perigos agora, e se preparar para os perigos mais à frente.

Honestamente, nós (Marcel, epidemiologista + Nicky, artista/programador) estamos preocupados. Nós podemos apostar que você está também! Por isto nós canalizamos nosso medo para criar estas **simulações lúdicas**, para que *você* possa canalizar seu medo para entender:

* **Os Últimos Meses** (epidemiologia 101, modelo SEIR, R & R<sub>0</sub>)
* **Os Próximos Meses** (lockdowns, rastreamento de contato, máscaras)
* **Os Próximos Anos** (perda de imunidade? sem vacinas?)

Este guia (publicado em 1º de Maio de 2020. clique nesta nota de rodapé!->[ˆtimestamp]) visa trazer para você esperança *e* medo. Para derrotar o COVID-19 **de uma forma que também proteja nossa saúde mental e financeira**, nós precisamos de otimismo para criar planos, e pessimismo para criar planos emergenciais. Como Gladys Bronwyn Stern disse uma vez, *"O otimista inventa o avião e o pessimista o paraquedas."*

[ˆtimestamp]: Estas notas de rodapé terão fontes, links ou comentário bônus. Como este comentário!
    
	**Este guia foi publicado em 1º de maio de 2020.** Muitos detalhes irão se tornar desatualizados, mas nós estamos confiantes que o guia cobrirá 95% dos futuros possíveis, e que Epidemiologia 101 será útil para sempre.

Então, apertem os cintos: nós estamos prestes a experimentar alguma turbulência.

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Os Últimos Meses</div>
    </div>
</div>

Pilotos usam simuladores de vôo para aprender a não destruir aviões.

**Epidemiologistas usam simuladores epidêmicos para aprender como não destruir a humanidade.**

Então, vamos construir um "simulador de vôo epidêmico" muito, muito simples!, <icon i></icon> Nesta simulação, pessoas infectadas podem tornar <icon s></icon> Pessoas suscetíveis em mais <icon i></icon>Pessoas infectadas:

![](pics/spread.png)

É estimado que, *no início* do surto de COVID-19, o vírus passa de uma <icon i></icon> para uma <icon s></icon> a cada 4 dias, *em média*. [^serial_interval] (lembre-se, há muita variação)

[^serial_interval]: “The mean [serial] interval was 3.96 days (95% CI 3.53–4.39 days)”. [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article) (Disclaimer: Early release articles are not considered as final versions)

Se nós simularmos "dobra a cada 4 dias" *e nada mais*, em uma população, começando com apenas 0.001% <icon i></icon>, o que acontece? 

**Clique "Iniciar" para rodar a simulação! Você pode rodar outras vezes com outros parâmetros:**
(ressalvas técnicas: [ˆcaveats])

[^caveats]: **Lembre-se: todas estas simulações são super simplificadas, para propósitos educacionais.**
    
	Uma simplificação: Quando você pede que a simulação "Infecte 1 nova pessoa a cada x dias", ele de fato está aumentando o número de infectados 1/x a cada dia. O mesmo ocorre para os demais ajustes destas simulações.
	- "Recuperar a cada x dias" está de fato reduzindo o número de infectados 1/x a cada dia.
    
	Estas *não são* exatamente as mesmas coisas, mas são próximas o suficiente, e para propósitos educacionais é menos obscuro que ajustar as taxas de transmissão e recuperação diretamente.

<div class="sim">
		<iframe src="sim?stage=epi-1" width="800" height="540"></iframe>
</div>

Esta é a **curva de crescimento exponencial.** Começa pequena, e então explode. "Oh é apenas uma gripe"para "Tá certo, gripes não criam *cemitérios de valas comuns em cidades ricas*".

![](pics/exponential.png)

Mas, esta simulação está errada. O crescimento exponencial, ainda bem, não pode ser perpétuo. Uma razãopara impedir o espalhamento do vírus é se outras pessoas *já* tem o vírus:

![](pics/susceptibles.png)

Quanto mais <icon i></icon>s existem, mais rápido <icon s></icon>s se tornam <icon i></icon>s, **mas quanto menos <icon s></icon>s existem, mais *lentamente* <icon s></icon>s se tornam <icon i></icon>s.**

Como isto muda o crescimento de uma epidemia? Vamos descobrir:

<div class="sim">
		<iframe src="sim?stage=epi-2" width="800" height="540"></iframe>
</div>

Esta é a **curva de crescimento logístico.** em formato de S. Começa devagar, explode, e desacelera de novo.

Mas, esta simulação *ainda* está errada. Nós estamos esquecendo o fato que <icon i></icon>Pessoas infectadas em algum momento param de ser infecciosas, seja 1) se recuperando, 2)"se recuperando" com dano aos pulmões, ou 3) morrendo.


Por questão de simplicidade, vamos fingir que todas as <icon i></icon> Pessoas infectadas se tornem <icon r></icon> Recuperadas. (Apenas lembrem-se que na realidade algumas morrem.) <icon r></icon>s não podem ser infectadas de novo, e vamos assumir – *por enquanto!* – que se tornam imunes por toda a vida.

No caso da COVID-19, é estimado que você permaneça <icon i></icon> Infectado por 10 dias, *em média*.[^infectiousness] Isto significa que alguns vão se recuperar antes de 10 dias e outros depois. **Este é o resultado, com uma simulação *começando* com 100% <icon i></icon>:**

[^infectiousness]: “The median communicable period \[...\] was 9.5 days.” [Hu, Z., Song, C., Xu, C. et al](https://link.springer.com/article/10.1007/s11427-020-1661-4) Yes, we know "median" is not the same as "average". For simplified educational purposes, close enough.

<div class="sim">
		<iframe src="sim?stage=epi-3" width="800" height="540"></iframe>
</div>

Isto é o oposto do crescimento exponencial, a **curva de decaimento exponencial.**

Agora, o que acontece se você simular crescimento logístico em formato de S *com* a recuperação?

![](pics/graphs_q.png)

Vamos descobrir.

<b style='color:#ff4040'>Curva vermelha</b> são os casos *atuais*<icon i></icon>,    
<b style='color:#999999'>Curva cinza</b> é o *total* de casos (atuais + recuperados <icon r></icon>), 
que se inicia em apenas 0.001% <icon i></icon>:

<div class="sim">
		<iframe src="sim?stage=epi-4" width="800" height="540"></iframe>
</div>

E é *daí* que esta famosa curva veio! Não é uma curva em sino, e não é nem mesmo uma curva "log-normal". Ela não tem nome. Mas você já deve ter visto um zilhão de vezes, e torcido muito para que ela achatasse.

Este é o **Modelo SIR**,[^sir]    
(<icon s></icon>**S**uscetível <icon i></icon>**I**nfectado <icon r></icon>**R**ecuperado)      
a *segunda* idéia mais importante em Epidemiologia 101:

[^sir]: Para mais explicações técnicas do Modelo SIR, veja [the Institute for Disease Modeling](https://www.idmod.org/docs/hiv/model-sir.html#) e [Wikipedia](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SIR_model)

![](pics/sir.png)

**NOTA: A simulações que informam as políticas são muito, *muito* mais sofisticadas que isto!** Mas o Modelo SIR ainda serve para encontrarmos as mesmas conclusõesgerais, mesmo que deixando passar algumas nuances.

De fato, vamos acrescentar uma nuance adicional: antes de um <icon s></icon> se tornar <icon i></icon>, ele primeiro se torna <icon e></icon> Exposto. Isto é quando ele tem o vírus mas ainda não pode passar adiante - infec*tado* mas não infec*cioso*.

![](pics/seir.png)

(Esta variante é chamada o  **Modelo SEIR**[^seir], onde o "E" significa <icon e></icon> "Exposto". Note que este *não é* o significado usual de "exposto", em que você pode ou não ter o vírus. Nesta definição técnica "Exposto" significa que você definitivamente tem. A terminologia científica é ruim.)

[^seir]: Para mais explicações técnicas do Modelo SEIR, veja [the Institute for Disease Modeling](https://www.idmod.org/docs/hiv/model-seir.html) e [Wikipedia](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SEIR_model)


No caso da COVID-19, é estimado que você fique <icon e></icon> infectado-mas-não-infeccioso por 3 dias, *em média*.[^latent] O que acontece se adicionarmos isto à simulação?

[^latent]: “Assumindo uma distribuição do período de incubação de 5.2 dias, em média, resultado de um estudo em separado dos primeiros casos de COVID-19, nós inferimos que o contágio começa a partir de 2.3 dias ((95% IC, 0.8-3.0 dias) antes dos sintomas se instalarem." (traduzindo: assumindo que os sintomas começam no dia 5, o contágio começa 2 dias antes = contágio começa no dia 3) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)

<b style='color:#ff4040'>Curva Vermelha</b> <b style='color:#FF9393'>+ Rosa</b> são os casos *atuais* (infeccioso <icon i></icon> + exposto <icon e></icon>),    
<b style='color:#888'>Curva cinza</b> são casos *totais* (atuais + recuperados <icon r></icon>):

<div class="sim">
		<iframe src="sim?stage=epi-5" width="800" height="540"></iframe>
</div>
Não há muitas mudanças! O tempo que você permanece <icon e></icon> Exposto muda a razão de <icon e></icon>-para-<icon i></icon>, e *quando* os casos correntes atingem o pico... mas a *altura* do pico, e o total de casos no final, permanecem os mesmos.

Por que isto acontece? Por causa da mais importante idéia em Epidemiologia 101:

![](pics/r.png)

Abreviação de "Número de reprodução". É o número *médio* de pessoas que um <icon i></icon> infecta *antes* de se recuperar (ou morrer).

![](pics/r2.png)

**R** muda durante o curso de um surto, já que ganhamos mais imunidade e intervenções.


**R<sub>0</sub>** (pronounced R-nought) is what R is *at the start of an outbreak, before immunity or interventions*. R<sub>0</sub> more closely reflects the power of the virus itself, but it still changes from place to place. For example, R<sub>0</sub> is higher in dense cities than sparse rural areas.

(Most news articles – and even some research papers! – confuse R and R<sub>0</sub>. Again, science terminology is bad)

The R<sub>0</sub> for "the" seasonal flu is around 1.28[^r0_flu]. This means, at the *start* of a flu outbreak, each <icon i></icon> infects 1.28 others *on average.* (If it sounds weird that this isn't a whole number, remember that the "average" mom has 2.4 children. This doesn't mean there's half-children running about.)

[^r0_flu]: “The median R value for seasonal influenza was 1.28 (IQR: 1.19–1.37)” [Biggerstaff, M., Cauchemez, S., Reed, C. et al.](https://bmcinfectdis.biomedcentral.com/articles/10.1186/1471-2334-14-480)

The R<sub>0</sub> for COVID-19 is estimated to be around 2.2,[^r0_covid] though one *not-yet-finalized* study estimates it was 5.7(!) in Wuhan.[^r0_wuhan]

[^r0_covid]: “We estimated the basic reproduction number R0 of 2019-nCoV to be around 2.2 (90% high density interval: 1.4–3.8)” [Riou J, Althaus CL.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7001239/)

[^r0_wuhan]: “we calculated a median R0 value of 5.7 (95% CI 3.8–8.9)” [Sanche S, Lin YT, Xu C, Romero-Severson E, Hengartner N, Ke R.](https://wwwnc.cdc.gov/eid/article/26/7/20-0282_article)

Nas nossa simulações – *no início & na média* – um <icon i></icon> infecta alguém a cada 4 dias, em 10 dias. "4 dias" ocorre dentro de "10 dias" duas vezes e meia. Isto significa – *no início & na média* – cada <icon i></icon> infecta 2.5 outros. Então, R<sub>0</sub> = 2.5. (ressalvas:[^r0_caveats_sim])

[^r0_caveats_sim]: Isto é assumindo que você é igualmente infeccioso durante todo o "período infeccioso". Mais uma vez simplificações para propósitos educacionais.

**Brinque com esta calculadora de R<sub>0</sub>, para ver como  R<sub>0</sub> depende dos tempos de recuperação e nova infecção:**

<div class="sim">
		<iframe src="sim?stage=epi-6a&format=calc" width="285" height="255"></iframe>
</div>

But remember, the fewer <icon s></icon>s there are, the *slower* <icon s></icon>s become <icon i></icon>s. The *current* reproduction number (R) depends not just on the *basic* reproduction number (R<sub>0</sub>), but *also* on how many people are no longer <icon s></icon> Susceptible. (For example, by recovering & getting natural immunity.)

Mas lembre-se, quanto menos <icon s></icon>s há, mais *lentamente* <icon s></icon>s tornam-se <icon i></icon>s. O número de reprodução (R) *corrente* depende não apenas do número de reprodução *básico* (R<sub>0</sub>), mas *também* em quantas pessoas não são mais <icon s></icon> Suscetíveis. (Por exemplo, por se recuperar e conseguindo imunidade natural.)

<div class="sim">
		<iframe src="sim?stage=epi-6b&format=calc" width="285" height="390"></iframe>
</div>

When enough people have immunity, R < 1, and the virus is contained! This is called **herd immunity**. For flus, herd immunity is achieved *with a vaccine*. Trying to achieve "natural herd immunity" by letting folks get infected is a *terrible* idea. (But not for the reason you may think! We'll explain later.)
Quando pessoas suficientes tem imunidade, R < 1, e o vírus é contido! Isto é chamado **imunidade de rebanho**. Para gripes, a imunidade de rebanho é atingida *com uma vacina*. Tentando atingir "imunidade de rebanho natural" deixando as pessoas se infectarem é uma idéia *terrível*. (Mas não pelas razões que você pode pensar! Explicaremos mais a frente.)

Vamos rodar o Modelo SEIR outra vez, mas mostrando R<sub>0</sub>, R ao longo do tempo, e o limiar de imunidade de rebanho:

<div class="sim">
		<iframe src="sim?stage=epi-7" width="800" height="540"></iframe>
</div>

**NOTA: O total de casos *não para* na imunidade de rebanho, mas ultrapassa ele!** E ele cruza o limiar *exatamente* quando os casos correntes atingem o pico. (Isto acontece não importa como você mude os ajustes - tente você mesmo!)

Isto ocorre porque quando há mais não-<icon s></icon>s do que o limiar da imunidade de rebanho, você tem R < 1. E quando R < 1, novos casos param de crescer: um pico.

**Se houver apenas uma lição para você tirar deste guia é esta** - é um diagrama extremamente complexo, então tome um tempo para absorvê-lo completamente:

![](pics/r3.png)

**Isto significa: nós NÃO precisamos impedir todas as transmissões, ou nem mesmo algo próximo de todas as transmissões, para parar o COVID-19!**

É um paradoxo. COVID-19 é extremamente contagioso, porém para contê-lo, nós "só" precisamos impedir 60% das infecções. 60%?! Se fosse uma nota no boletim seria um D-. Mas se R<sub>0</sub> = 2.5, cortando isto por 61% nós temos R = 0.975, que é R < 1, vírus contido! (fórmula exata:[^exact_formula])

[^exact_formula]: Lembre-se R = R<sub>0</sub> * a proporção das transmissões ainda permitidas. Lembre-se ainda que a proporção das transmissões ainda permitidas = 1 - proporção das transmissões  *impedidas*.
    
    Logo, para ter R < 1, você precisa ter R<sub>0</sub> * TransmissõesPermitidas < 1. 
    
    Logo, TransmissõesPermitidas < 1/R<sub>0</sub>
    
    Logo, 1 - TransmissõesImpedidas < 1/R<sub>0</sub>
    
    Logo, TransmissõesImpedidas > 1 - 1/R<sub>0</sub>
    
    Logo, você precisa parar mais que **1 - 1/R<sub>0</sub>** das transmissões para conseguir R < 1 e conter o vírus!  

![](pics/r4.png)

(Se você pensa que R<sub>0</sub> ou outros números nas nossas simulações são muito baixos/altos, isto é bom pois está desafiando nossas premissas! Haverá um "Modo Caixa de Areia" no fim deste guia, onde você poderá inserir os seus *próprios* números, e simular o que acontece.)

*Cada* intervenção sobre COVID-19 que você já ouviu sobre - lavar as mãos, distanciamento social/físico, lockdowns, auto-isolamento, rastreamento de contatos e quarentena, máscaras faciais, e mesmo "imunidade de rebanho" - todas estão visando a mesma coisa:

Fazer R < 1.

Então agora, vamos usar nosso "simulador de vôo epidemico" para descobrir o seguinte: Como podemos conseguir ter R < 1 de uma forma que **também proteja nossa saúde mental *e* financeira?**

Preparem-se para uma aterrisagem de emergência...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Os Próximos Meses</div>
    </div>
</div>

...poderia ter sido pior. Aqui está um universo paralelo que evitamos:

###Cenário 0: Não Fazer Absolutamente Nada

Perto de 1 em cada 20 pessoas infectadas com COVID-19 precisam ir para um UTI(Unidade de Terapia Intensiva.)[^icu_covid] Em um país rico como os EUA, há 1 cama de UTI para cada 3400 pessoas. [^icu_us] Portanto os EUA podem tratar 20 de 3400 pessoas *simultaneamente* infectadas - ou 0.6% da população.

[^icu_covid]: ["Percentage of COVID-19 cases in the United States from February 12 to March 16, 2020 that required intensive care unit (ICU) admission, by age group"](https://www.statista.com/statistics/1105420/covid-icu-admission-rates-us-by-age-group/). Entre 4.9% e 11.5% de *todos* os casos de COVID-19 requereram UTI. Generosamente escolhendo a faixa inferior, isto significa 5% ou 1 em 20. Note que este total é específico para a estrutura etária dos EUA, e será maior em países com populações mais velhas, e menor em países com populações mais jovens.

[^icu_us]: “Números de camas de UTI = 96,596”. Em [the Society of Critical Care Medicine](https://sccm.org/Blog/March-2020/United-States-Resource-Availability-for-COVID-19) População dos EUA era 328.200.000 em 2019. 96.596 de cada 328,200,000 = aproximadamente 1 em 3400. 

Mesmo se nós *mais que triplicarmos* esta capacidade para 2%, aqui está o que aconteceria *se não fizessemos absolutamente nada:*

<div class="sim">
		<iframe src="sim?stage=int-1&format=lines" width="800" height="540"></iframe>
</div>

Nada bom.

Isto é o que [o relatório do Imperial College em 16 de março](http://www.imperial.ac.uk/mrc-global-infectious-disease-analysis/covid-19/report-9-impact-of-npis-on-covid-19/) descobriu: se não fizessemos nada ficaríamos sem camas de UTI, com mais de 80% da população infectada. (lembre-se: o número total de casos *ultrapassa* a imunidade de rebanho).

Mesmo se apenas 0.5% dos infectados morressem - uma suposição generosa quando não há mais vagas na UTI - em um país grande como os EUA, com 300 milhões de pessoas, 0.5% de 80% de 300 milhões = ainda são 1.2 milhões de mortos...
*SE não fizessemos nada.*

(Muitos canais de notícia e mídia social reportaram "80% serão infectados" *SEM* o "SE NÃO FIZERMOS NADA". O medo foi canalizado em clicks, e não para o entendimento. *Suspiro.*)

###Cenário 1: Achatar a Curva / Imunidade de Rebanho

O plano de "Achatar a Curva" foi apregoado por todas as organizações de saúde pública, enquanto que o plano original de "imunidade de rebanho" do Reino Unido era universalmente vaiado. Eles eram *o mesmo plano.* O Reino Unido apenas comunicou mal seu plano.[^yong]

"Ele diz que a meta real é a mesma dos outros países: achatar a curva ao escalonar o início as infecções. Como consequência, a nação deve atingir imunidade de rebanho; é um efeito colateral, e não um objetivo. [...] O verdadeiro plano de ação para o coronavírus do gorverno, disponível online, não menciona imunidade de rebanho em nenhum lugar.""
  
    Do [artigo de Ed Yong para o The Atlantic](https://www.theatlantic.com/health/archive/2020/03/coronavirus-pandemic-herd-immunity-uk-boris-johnson/608065/)

Ambos os planos, entretanto, tinham literalmente uma falha fatal.

Primeiro, vamos olhar nas duas principais formas de "achatar a curva": lavar as mãos e distanciamento físico.

O aumento da lavagem das mãos corta a incidência de gripes e resfriados em países de alta renda em ~25%[^handwashing], enquanto o lockdown de toda a cidade de Londres corta os contatos próximos em ~70%[ˆlondon]. Então, vamos assumir que a lavagem de mãos pode reduzir R *em até* 25%, e o distanciamento pode reduzir R *em até* 70%:

[^handwashing]:"Todos os oito estudos elegíveis reportaram que lavagem de mãos reduziram os riscos de infecção respiratória, com redução de riscos entre 6% a 44% [valor agrupado 24% (95% IC 6-40%)]."Nós arredondamos o valor agrupado para 25% nestas simulações por simplicidade.[Rabie, T. and Curtis, V.](https://onlinelibrary.wiley.com/doi/full/10.1111/j.1365-3156.2006.01568.x) Nota: como esta meta-análise aponta, a qualidade dos estudos para lavagem de mãos (pelo menos em países de alta renda) é péssima.

[^london]: "Nós encontramos uma redução de 73% no número de contatos diários observados por participante. Isto seria suficiente para reduzir R<sub>0</sub> de um valor de 2.6 antes do lockdown para 0.62 (0.37 - 0.89) durante o lockdown". Nós arredondamos este valor para 70% nestas simulações por simplicidade. [Jarvis and Zandvoort et al](https://cmmid.github.io/topics/covid19/comix-impact-of-physical-distance-measures-on-transmission-in-the-UK.html)

**Brinque com esta calculadora para ver qual o % de non-<icon s></icon>, lavagem de mão, e distanciamento reduzem R:** (esta calculadora visualiza os seus efeitos *relativos*, e é por isto que incrementando um *parece* como se estivessemos diminuindo o efeito de outros.[^log_caveat])

[^log_caveat]: Esta distorção sumiria se plotassemos R em uma escala logarítimca... mas então teríamos que explicar *escalas logarítimicas*

<div class="sim">
		<iframe src="sim?stage=int-2a&format=calc" width="285" height="260"></iframe>
</div>

Agora, vamos simular o que acontece com uma epidemia de COVID-19 se, começando em março de 2020, nós tivessemos aumentado a lavagem de mãos mas adotado apenas *leve* distanciamento físico - de tal forma que R é mais baixo, mas ainda acima de 1:

<div class="sim">
		<iframe src="sim?stage=int-2&format=lines" width="800" height="540"></iframe>
</div>

Três notas:

1. Isto *reduz* o total de casos! **Mesmo se você não consegue R < 1, reduzindo R ainda salva vidas, ao reduzir o tanto que se ultrapassa sobre a imunidade de rebanho.** Muitos pensam que "Achatar a Curva" espalha os casos sem reduzir o seu número total. Isto é impossível em *qualquer* modelo em Epidemiologia 101. Mas como a mídia reportou "mais de 80% serão infectados" como inevitável, as pessoas pensam que o número total de casos será o mesmo não importando nada. *Suspiro.*

2. Devido as intervenções extra, os casos correntes atingem o pico *antes* que a imunidade de rebanho seja alcançada. De fato, nesta simulação, o número total de casos apenas ultrapass *um pouco* acimna da imunidade de rebanho - o plano do Reino Unido! Neste ponto, R < 1, você pode descartar todas as outras intervenções, e a COVID-19 permanece contida! Bem, exceto por um problema...

3. Você continua sem leitos de UTI. Por vários meses. (e lembre-se, nós *já* triplicamos as UTIs nestas simulações)

Este foi o outro achado do relatório do Imperial College em 16 de março, que convenceu o Reino Unido a abandonar o plano original. Qualquer tentativa de **mitigação** (reduzir R, mas com R>1) iria falhar. A única saída seria **supressão** (reduzir R de forma que R < 1).

![](pics/mitigation_vs_suppression.png)

Isto é, não apenas "achate" a curva, *esmague* a curva. Por exemplo, com um...

###Cenário 3: Lockdown de Meses

Vamos ver o que acontece se nós *esmagamos* a curva com um lockdown de 5 meses, reduzindo <icon i></icon> para quase nada, e então - *finalmente* - retornando para a vida normal:

<div class="sim">
		<iframe src="sim?stage=int-3&format=lines" width="800" height="540"></iframe>
</div>

Oh.

Esta é a "segunda onda" que todo mundo está falando a respeito. Assim que removemos o lockdown, nós voltamos a ter R > 1 de novo. Então, um único <icon i></icon> deixado para trás (ou importado) pode causar um disparo nos casos que é quase tão ruim como se tivessemos feito o Cenário 0: Absolutamente Nada.

**Um lockdown não é a cura, ele é apenas um reinício.**

Então o que? Nós apenas entramos em lockdown de novo e de novo?

###Cenário 3: Lockdown Intermitente

Esta solução foi sugerida inicialmente pelo relatório do Imperial College de 16 de março, e de novo por um artigo de Harvard.[^lockdown_harvard]

[^lockdown_harvard]: "Na falta de outras intervenções, uma métrica chave para o sucesso do distanciamento social é se as capacidades críticas de cuidado são excedidas. Para evitar isto, distanciamento social prolongado ou intermitente pode ser necessário até 2022." [Kissler and Tedijanto et al](https://science.sciencemag.org/content/early/2020/04/14/science.abb5793)

**Aqui está uma simulação:** (Depois de brincar com o "cenário gravado", você pode tentar simular seus *próprios* cronogramas de lockdown, mudando os cursores *enquanto* a simulação está rodando! Lembre-se que você pode parar e continuar a simulação, e alterar a sua velocidade).

<div class="sim">
		<iframe src="sim?stage=int-4&format=lines" width="800" height="540"></iframe>
</div>

Isto *iria* manter os casos abaixo da capacidade das UTIs! E é *muito* melhor que um lockdown de 18 meses até que uma vacina esteja disponível. (E se não houver vacina, repita até que a imunidade de rebanho seja atingida... em 2022.)

Veja, é legal desenhar uma linha dizendo "capacidade das UTIs", mas tem várias coisas importantes que nós *não podemos* simular aqui. Como:

**Saúde Mental:** Solidão é um dos maiores fatores de risco para depressão, ansiedade, e suicídio. E está tão associado com a morte prematura quanto fumar 15 cigarros por dia.[^loneliness]

Veja [Figure 6 from Holt-Lunstad & Smith 2010](https://journals.sagepub.com/doi/abs/10.1177/1745691614568352). Claro, grande ressalva que eles encontraram uma *correlação*. Mas a não ser que você queira tentar aleatóriamente designar pessoas para serem solitárias a vida toda evidência de observação é tudo que você pode ter. 

**Saúde Financeira:** "E a respeito da economia" soa como se você se importasse mais com dólares que com vidas, mas "a economia" não é apenas a bolsa de valores: é a capacidade das pessoas prover comida e abrigo para os seus entes queridos, para investir no futuro dos seus filhos, e desfrutar de artes, comidas, videogames - as coisas que fazem a vida valer a pena. E além disto, pobreza *por si só* tem impactos horríveis na saúde mental e física.

Não estou dizendo que nós *não devamos* ter outro lockdown! Nós iremos falar de lockdowns "disjuntores" depois. De toda forma não é o ideal.

Mas espere... Formosa e a Coréia do Sul não contiveram a COVID-19? Por 4 meses inteiros *sem* quarentenas de longo prazo?

Como?

###Cenário 4: Teste, Rastreie, Isole

*"Claro, nós \*poderíamos\* ter feito o que Formosa e Coréia do Sul fizeram desde o início, mas agora é tarde demais. Nós perdemos a largada."*

Mas é exatamente isto! "Uma quarentena não é a cura, é apenas um recomeço"... **e um recomeço do zero é tudo que precisamos.**

Para entender como Formosa e Coréia do Sul contiveram o COVID-19, nós necessitaríamos entender a exata linha do tempo de uma típica infecção de COVID-19[^timeline]:  

[^timeline]: **3 dias em média para o contágio:** “Assumindo uma distribuição do período de incubação de 5.2 dias, em média, resultado de um estudo em separado dos primeiros casos de COVID-19, nós inferimos que o contágio começa a partir de 2.3 dias ((95% IC, 0.8-3.0 dias) antes dos sintomas se instalarem." (traduzindo: assumindo que os sintomas começam no dia 5, o contágio começa 2 dias antes = contágio começa no dia 3)[He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)
    
	**4 dias na média para infectar outra pessoa:** "The mean [serial] interval was 3.96 dias (95% IC 3.53-4.39 dias)" [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article)
    
   	**5 dias em média para sentir os sintomas:** "O período médio de incubação foi estimado em 5.1 dias (95% IC, 4.5 a 5.8 dias)" [Lauer SA, Grantz KH, Bi Q, et al](https://annals.org/AIM/FULLARTICLE/2762808/INCUBATION-PERIOD-CORONAVIRUS-DISEASE-2019-COVID-19-FROM-PUBLICLY-REPORTED)

![](pics/timeline1.png)

Se os casos só se auto-isolam quando eles sabem que estão doentes (isto é, eles sentem sintomas), o vírus ainda pode se espalhar:

![](pics/timeline2.png)

E de fato, 44% de todas as transmissões são assim: *pré*-sintomáticas! [^pre_symp]

[^pre_symp]: “We estimated that 44% (95% confidence interval, 25–69%) of secondary cases were infected during the index cases’ presymptomatic stage” [He, X., Lau, E.H.Y., Wu, P. et al](https://www.nature.com/articles/s41591-020-0869-5)

But, if we find *and quarantine* a symptomatic case's recent close contacts... we stop the spread, by staying one step ahead!

![](pics/timeline3.png)

This is called **contact tracing**. It's an old idea, was used at an unprecedented scale to contain Ebola[^ebola], and now it's core part of how Taiwan & South Korea are containing COVID-19!

[^ebola]: “Contact tracing was a critical intervention in Liberia and represented one of the largest contact tracing efforts during an epidemic in history.” [Swanson KC, Altare C, Wesseh CS, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6152989/)

(It also lets us use our limited tests more efficiently, to find pre-symptomatic <icon i></icon>s without needing to test almost everyone.)

Traditionally, contacts are found with in-person interviews, but those *alone* are too slow for COVID-19's ~48 hour window. That's why contact tracers need help, and be supported by – *NOT* replaced by – contact tracing apps.

(This idea didn't come from "techies": using an app to fight COVID-19 was first proposed by [a team of Oxford epidemiologists](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936).)

Wait, apps that trace who you've been in contact with?... Does that mean giving up privacy, giving in to Big Brother?

Heck no! **[DP-3T](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)**, a team of epidemiologists & cryptographers (including one of us, Marcel Salathé) is *already* making a contact tracing app – with code available to the public – that reveals **no info about your identity, location, who your contacts are, or even *how many contacts* you've had.**

Here's how it works:

![](pics/dp3t.png)

(& [here's the full comic](https://ncase.me/contact-tracing/))

Along with similar teams like TCN Protocol[^tcn] and MIT PACT[^pact], they've inspired Apple & Google to bake privacy-first contact tracing directly into Android/iOS.[^gapple] (Don't trust Google/Apple? Good! The beauty of this system is it doesn't *need* trust!) Soon, your local public health agency may ask you to download an app. If it's privacy-first with publicly-available code, please do!

[^tcn]: [Temporary Contact Numbers, a decentralized, privacy-first contact tracing protocol](https://github.com/TCNCoalition/TCN#tcn-protocol)

[^pact]: [PACT: Private Automated Contact Tracing](https://pact.mit.edu/)

[^gapple]: [Apple and Google partner on COVID-19 contact tracing technology ](https://www.apple.com/ca/newsroom/2020/04/apple-and-google-partner-on-covid-19-contact-tracing-technology/). Note they're not making the apps *themselves*, just creating the systems that will *support* those apps.

But what about folks without smartphones? Or infections through doorknobs? Or "true" asymptomatic cases? Contact tracing apps can't catch all transmissions... *and that's okay!* We don't need to catch *all* transmissions, just 60%+ to get R < 1.

(Rant about the confusion about pre-symptomatic vs "true" asymptomatic. "True" asymptomatics are rare:[^rant])

[^rant]: Lots of news reports – and honestly, many research papers – did not distinguish between "cases who showed no symptoms when we tested them" (pre-symptomatic) and "cases who showed no symptoms *ever*" (true asymptomatic). The only way you could tell the difference is by following up with cases later.
   
    Which is what [this study](https://wwwnc.cdc.gov/eid/article/26/8/20-1274_article) did. (Disclaimer: "Early release articles are not considered as final versions.") In a call center in South Korea that had a COVID-19 outbreak, "only 4 (1.9%) remained asymptomatic within 14 days of quarantine, and none of their household contacts acquired secondary infections."
    
    So that means "true asymptomatics" are rare, and catching the disease from a true asymptomatic may be even rarer!

Isolating *symptomatic* cases would reduce R by up to 40%, and quarantining their *pre/a-symptomatic* contacts would reduce R by up to 50%[^oxford]:

[^oxford]: From the same Oxford study that first recommended apps to fight COVID-19: [Luca Ferretti & Chris Wymant et al](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936/tab-figures-data) See Figure 2. Assuming R<sub>0</sub> = 2.0, they found that:    
    
    * Symptomatics contribute R = 0.8 (40%)
    * Pre-symptomatics contribute R = 0.9 (45%)
    * Asymptomatics contribute R = 0.1 (5%, though their model has uncertainty and it could be much lower)
    * Environmental stuff like doorknobs contribute R = 0.2 (10%)

    And add up the pre- & a-symptomatic contacts (45% + 5%) and you get 50% of R!

<div class="sim">
		<iframe src="sim?stage=int-4a&format=calc" width="285" height="340"></iframe>
</div>

Thus, even without 100% contact quarantining, we can get R < 1 *without a lockdown!* Much better for our mental & financial health. (As for the cost to folks who have to self-isolate/quarantine, *governments should support them* – pay for the tests, job protection, subsidized paid leave, etc. Still way cheaper than intermittent lockdown.)

We then keep R < 1 until we have a vaccine, which turns susceptible <icon s></icon>s into immune <icon r></icon>s. Herd immunity, the *right* way:

<div class="sim">
		<iframe src="sim?stage=int-4b&format=calc" width="285" height="230"></iframe>
</div>

(Note: this calculator pretends the vaccines are 100% effective. Just remember that in reality, you'd have to compensate by vaccinating *more* than "herd immunity", to *actually* get herd immunity)

Okay, enough talk. Here's a simulation of:

1. A few-month lockdown, until we can...
2. Switch to "Test, Trace, Isolate" until we can...
3. Vaccinate enough people, which means...
4. We win.

<div class="sim">
		<iframe src="sim?stage=int-5&format=lines" width="800" height="540"></iframe>
</div>

So that's it! That's how we make an emergency landing on this plane.

That's how we beat COVID-19.

...

But what if things *still* go wrong? Things have gone horribly wrong already. That's fear, and that's good! Fear gives us energy to create *backup plans*.

The pessimist invents the parachute.

###Scenario 4+: Masks For All, Summer, Circuit Breakers

What if R<sub>0</sub> is way higher than we thought, and the above interventions, even with mild distancing, *still* aren't enough to get R < 1?

Remember, even if we can't get R < 1, reducing R still reduces the "overshoot" in total cases, thus saving lives. But still, R < 1 is the ideal, so here's a few other ways to reduce R:

**Masks For All:**

*"Wait,"* you might ask, *"I thought face masks don't stop you from getting sick?"*

You're right. Masks don't stop you from getting sick[^incoming]... they stop you from getting *others* sick.

[^incoming]: “None of these surgical masks exhibited adequate filter performance and facial fit characteristics to be considered respiratory protection devices.” [Tara Oberg & Lisa M. Brosseau](https://www.sciencedirect.com/science/article/pii/S0196655307007742)

[^outgoing]: “The overall 3.4 fold reduction [70% reduction] in aerosol copy numbers we observed combined with a nearly complete elimination of large droplet spray demonstrated by Johnson et al. suggests that surgical masks worn by infected persons could have a clinically significant impact on transmission.” [Milton DK, Fabian MP, Cowling BJ, Grantham ML, McDevitt JJ](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3591312/)

[^homemade]: [Davies, A., Thompson, K., Giri, K., Kafatos, G., Walker, J., & Bennett, A](https://www.cambridge.org/core/journals/disaster-medicine-and-public-health-preparedness/article/testing-the-efficacy-of-homemade-masks-would-they-protect-in-an-influenza-pandemic/0921A05A69A9419C862FA2F35F819D55) See Table 1: a 100% cotton T-shirt has around 2/3 the filtration efficiency as a surgical mask, for the two bacterial aerosols they tested.

![](pics/masks.png)

To put a number on it: surgical masks *on the sick person* reduce cold & flu viruses in aerosols by 70%.[^outgoing] Reducing transmissions by 70% would be as large an impact as a lockdown!

However, we don't know for sure the impact of masks on COVID-19 *specifically*. In science, one should only publish a finding if you're 95% sure of it. (...should.[^replication]) Masks, as of May 1st 2020, are less than "95% sure".

[^replication]: Any actual scientist who read that last sentence is probably laugh-crying right now. See: [p-hacking](https://en.wikipedia.org/wiki/Data_dredging), [the replication crisis](https://en.wikipedia.org/wiki/Replication_crisis))

However, pandemics are like poker. **Make bets only when you're 95% sure, and you'll lose everything at stake.** As a recent article on masks in the British Medical Journal notes,[^precautionary] we *have* to make cost/benefit analyses under uncertainty. Like so:

[^precautionary]: “It is time to apply the precautionary principle” [Trisha Greenhalgh et al \[PDF\]](https://www.bmj.com/content/bmj/369/bmj.m1435.full.pdf)

Cost: If homemade cloth masks (which are ~2/3 as effective as surgical masks[^homemade]), super cheap. If surgical masks, more expensive but still pretty cheap.

Benefit: Even if it's a 50–50 chance of surgical masks reducing transmission by 0% or 70%, the average "expected value" is still 35%, same as a half-lockdown! So let's guess-timate that surgical masks reduce R by up to 35%, discounted for our uncertainty. (Again, you can challenge our assumptions by turning the sliders up/down)

<div class="sim">
		<iframe src="sim?stage=int-6a&format=calc" width="285" height="380"></iframe>
</div>

(other arguments for/against masks:[^mask_args])

[^mask_args]: **"We need to save supplies for hospitals."** *Absolutely agreed.* But that's more of an argument for increasing mask production, not rationing. In the meantime, we can make cloth masks.

   **"They're hard to wear correctly."** It's also hard to wash your hands according to the WHO Guidelines – seriously, "Step 3) right palm over left dorsum"?! – but we still recommend handwashing, because imperfect is still better than nothing.
   
   **"It'll make people more reckless with handwashing & social distancing."** Sure, and safety belts make people ignore stop signs, and flossing makes people eat rocks. But seriously, we'd argue the opposite: masks are a *constant physical reminder* to be careful – and in East Asia, masks are also a symbol of solidarity!
    
    

Masks *alone* won't get R < 1. But if handwashing & "Test, Trace, Isolate" only gets us to R = 1.10, having just 1/3 of people wear masks would tip that over to R < 1, virus contained!

**Summer:**

Okay, this isn't an "intervention" we can control, but it will help! Some news outlets report that summer won't do anything to COVID-19. They're half right: summer won't get R < 1, but it *will* reduce R.

For COVID-19, every extra 1° Celsius (2.2° Fahrenheit) makes R drop by 1.2%.[^heat] The summer-winter difference in New York City is 15°C (60°F), so summer will make R drop by 18%.

[^heat]: “One-degree Celsius increase in temperature [...] lower[s] R by 0.0225” and “The average R-value of these 100 cities is 1.83”. 0.0225 ÷ 1.83 = ~1.2%. [Wang, Jingyuan and Tang, Ke and Feng, Kai and Lv, Weifeng](https://papers.ssrn.com/sol3/Papers.cfm?abstract_id=3551767)

<div class="sim">
		<iframe src="sim?stage=int-6b&format=calc" width="285" height="220"></iframe>
</div>

Summer alone won't make R < 1, but if we have limited resources, we can scale back some interventions in the summer – so we can scale them *higher* in the winter.

**A "Circuit Breaker" Lockdown:**

And if all that *still* isn't enough to get R < 1... we can do another lockdown.

But we wouldn't have to be 2-months-closed / 1-month-open over & over! Because R is reduced, we'd only need one or two more "circuit breaker" lockdowns before a vaccine is available. (Singapore had to do this recently, "despite" having controlled COVID-19 for 4 months. That's not failure: this *is* what success takes.)

Here's a simulation a "lazy case" scenario:

1. Lockdown, then
2. A moderate amount of hygiene & "Test, Trace, Isolate", with a mild amount of "Masks For All", then...
3. One more "circuit breaker" lockdown before a vaccine's found.

<div class="sim">
		<iframe src="sim?stage=int-7&format=lines&height=620" width="800" height="620"></iframe>
</div>

Not to mention all the *other* interventions we could do, to further push R down:

* Travel restrictions/quarantines
* Temperature checks at malls & schools
* Deep-cleaning public spaces
* [Replacing hand-shaking with foot-bumping](https://twitter.com/V_actually/status/1233785527788285953)
* And all else human ingenuity shall bring

. . .

We hope these plans give you hope. 

**Even under a pessimistic scenario, it *is* possible to beat COVID-19, while protecting our mental and financial health.** Use the lockdown as a "reset button", keep R < 1 with case isolation + privacy-protecting contract tracing + at *least* cloth masks for all... and life can get back to a normal-ish!

Sure, you may have dried-out hands. But you'll get to invite a date out to a comics bookstore! You'll get to go out with friends to watch the latest Hollywood cash-grab. You'll get to people-watch at a library, taking joy in people going about the simple business of *being alive.*

Even under the worst-case scenario... life perseveres.

So now, let's plan for some *worse* worst-case scenarios. Water landing, get your life jacket, and please follow the lights to the emergency exits:

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>The Next Few Years</div>
    </div>
</div>

You get COVID-19, and recover. Or you get the COVID-19 vaccine. Either way, you're now immune...

...*for how long?*

* COVID-19 is most closely related to SARS, which gave its survivors 2 years of immunity.[^SARS immunity]
* The coronaviruses that cause "the" common cold give you 8 months of immunity.[^cold immunity]
* There's reports of folks recovering from COVID-19, then testing positive again, but it's unclear if these are false positives.[^unclear]
* One *not-yet-peer-reviewed* study on monkeys showed immunity to the COVID-19 coronavirus for at least 28 days.[^monkeys]

But for COVID-19 *in humans*, as of May 1st 2020, "how long" is the big unknown.

[^SARS immunity]: “SARS-specific antibodies were maintained for an average of 2 years [...] Thus, SARS patients might be susceptible to reinfection ≥3 years after initial exposure.” [Wu LP, Wang NC, Chang YH, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2851497/) "Sadly" we'll never know how long SARS immunity would have really lasted, since we eradicated it so quickly.

[^cold immunity]: “We found no significant difference between the probability of testing positive at least once and the probability of a recurrence for the beta-coronaviruses HKU1 and OC43 at 34 weeks after enrollment/first infection.” [Marta Galanti & Jeffrey Shaman (PDF)](http://www.columbia.edu/~jls106/galanti_shaman_ms_supp.pdf)

[^unclear]: “Once a person fights off a virus, viral particles tend to linger for some time. These cannot cause infections, but they can trigger a positive test.” [from STAT News by Andrew Joseph](https://www.statnews.com/2020/04/20/everything-we-know-about-coronavirus-immunity-and-antibodies-and-plenty-we-still-dont/)

[^monkeys]: From [Bao et al.](https://www.biorxiv.org/content/10.1101/2020.03.13.990226v1.abstract) *Disclaimer: This article is a preprint and has not been certified by peer review (yet).* Also, to emphasize: they only tested re-infection 28 days later. 

For these simulations, let's say it's 1 year.
**Here's a simulation starting with 100% <icon r></icon>**, exponentially decaying into susceptible, no-immunity <icon s></icon>s after 1 year, on *average*, with variation:

<div class="sim">
		<iframe src="sim?stage=yrs-1&format=lines&height=600" width="800" height="600"></iframe>
</div>

Return of the exponential decay!

This is the **SEIRS Model**. The final "S" stands for <icon s></icon> Susceptible, again.

![](pics/seirs.png)

Now, let's simulate a COVID-19 outbreak, over 10 years, with no interventions... *if immunity only lasts a year:*

<div class="sim">
		<iframe src="sim?stage=yrs-2&format=lines&height=600" width="800" height="600"></iframe>
</div>

In previous simulations, we only had *one* ICU-overwhelming spike. Now, we have several, *and* <icon i></icon> cases come to a rest *permanently at* ICU capacity. (Which, remember, we *tripled* for these simulations)

R = 1, it's **endemic.**

Thankfully, because summer reduces R, it'll make the situation better:

<div class="sim">
		<iframe src="sim?stage=yrs-3&format=lines&height=640" width="800" height="640"></iframe>
</div>

Oh.

Counterintuitively, summer makes the spikes worse *and* regular! This is because summer reduces new <icon i></icon>s, but that in turn reduces new immune <icon r></icon>s. Which means immunity plummets in the summer, *creating* large regular spikes in the winter.

Thankfully, the solution to this is pretty straightforward – just vaccinate people every fall/winter, like we do with flu shots:

**(After playing the recording, try simulating your own vaccination campaigns! Remember you can pause/continue the sim at any time)**

<div class="sim">
		<iframe src="sim?stage=yrs-4&format=lines" width="800" height="540"></iframe>
</div>

But here's the scarier question:

What if there's no vaccine for *years*? Or *ever?*

**To be clear: this is unlikely.** Most epidemiologists expect a vaccine in 1 to 2 years. Sure, there's never been a vaccine for any of the other coronaviruses before, but that's because SARS was eradicated quickly, and "the" common cold wasn't worth the investment. 

Still, infectious disease researchers have expressed worries: What if we can't make enough?[^vax_enough] What if we rush it, and it's not safe?[^vax_safe]

[^vax_enough]: “If a coronavirus vaccine arrives, can the world make enough?” [by Roxanne Khamsi, on Nature](https://www.nature.com/articles/d41586-020-01063-8)

[^vax_safe]: “Don’t rush to deploy COVID-19 vaccines and drugs without sufficient safety guarantees” [by Shibo Jiang, on Nature](https://www.nature.com/articles/d41586-020-00751-9)

Even in the nightmare "no-vaccine" scenario, we still have 3 ways out. From most to least terrible:

1) Do intermittent or loose R < 1 interventions, to reach "natural herd immunity". (Warning: this will result in many deaths & damaged lungs. *And* won't work if immunity doesn't last.)

2) Do the R < 1 interventions forever. Contact tracing & wearing masks just becomes a new norm in the post-COVID-19 world, like how STI tests & wearing condoms became a new norm in the post-HIV world.

3) Do the R < 1 interventions until we develop treatments that make COVID-19 way, way less likely to need critical care. (Which we should be doing *anyway!*) Reducing ICU use by 10x is the same as increasing our ICU capacity by 10x:

**Aqui está uma simulação de imunidade *não* duradoura, *sem* vacinas, e mesmo sem nenhuma intervenção - apenas incrementando lentamente a capacidade de sobrevivência aos surtos de longo prazo:**

<div class="sim">
		<iframe src="sim?stage=yrs-5&format=lines" width="800" height="540"></iframe>
</div>

Até mesmo sob o cenário de *pior* caso... a vida persevera.

. . .

Talvez você goste de desafiar nossas premissas, e tentar R<sub>0</sub>'s ou números diferentes. Ou tentar simular suas *próprias* combinações de planos de intervenção!

**Aqui está um Modo de Caixa de Areia(optional), com *tudo* disponível. (role a tela para ver todos os controles) Simule e brinque a vontade:**

<div class="sim">
		<iframe src="sim?stage=SB&format=sb" width="800" height="540"></iframe>
</div>

Este "simulador de vôo epidemico" básico nos ensinou tanto. Ele nos permite responder questões sobre nossos últimos meses, os próximos meses, e os próximos anos.

Então finalmente, vamos retornar para...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>O Agora</div>
    </div>
</div>

O avião afundou. Nós subimos nos botes salva-vidas. É hora de encontrar terra firme.[^dry_land]

[^dry_land]: A metáfora de terra firme [from Marc Lipsitch & Yonatan Grad, on STAT News](https://www.statnews.com/2020/04/01/navigating-covid-19-pandemic/)


Equipes de epidemiologistas e governantes ([left](https://www.americanprogress.org/issues/healthcare/news/2020/04/03/482613/national-state-plan-end-coronavirus-crisis/), [right](https://www.aei.org/research-products/report/national-coronavirus-response-a-road-map-to-reopening/ ), e [multi-partisan](https://ethics.harvard.edu/covid-roadmap)) chegaram a um consenso em como bater a COVID-19, enquento protegem nossas vidas *e* liberdades. 

Aqui segue uma idéia geral, com alguns (menos consensuais) planos de emergência:

![](pics/plan.png)

Então o que isto significa para VOCÊ, agora?

**Para todo mundo** Respeite a quarentena para que nós possamos sair da Fase I tão logo quanto possível. Continue lavando as suas mãos. Faça suaa própria máscara. Baixe um app de rastreamento de contatos *que protejam identidades* quando estes estiverem disponíveis no próximo mês. Se mantenha física e mentalmente saudável! E escreva para seu legislador local para levantar a bunda da cadeira e...

**Para legisladores:** Crie leis que deem suporte a quem tem que se isolar/ficar em quarentena. Contrate mais rastreadores de contato manuais, *auxiliados* por app de rastreamento de contatos *que protejam identidades*. Direcione mais fundos para as coisas que deveríamos estar fazendo, tais como...

**Para produtores:** Produzam testes. Produzam respiradores. Produzam equipamentos de proteção para hospitais. Produzam testes. Produzam máscaras. Produzam apps. Produzam antivirais, profiláticos, e outros tratamentos que não são vacinas. Produzam vacinas. Produzam testes. Produzam testes. Produzam testes. Produzam esperança.

Não minimize o medo para construir esperança. Nosso medo deve *trabalhar junto* com nossa esperança, como os inventores de aviões e paraquedas. Se preparar para futuros horríveis é como nós *criamos* um futuro de esperança.

A única coisa a temer é a idéia que a única coisa a temer é o próprio medo.
