---
title: Mitochondrial mutations
layout: post
---

My colleague Young Seok has just published his paper _Origins and functional consequences of somatic mitochondrial 
DNA mutations in human cancer_ in ![eLife](http://dx.doi.org/10.7554/eLife.02935). I am a coauthor on
this paper and have helped derive an analytical expression for the expected number of mitochondrial
mutations in cancer samples.

Young Seok showed that mitochondrial mutations occur at greater numbers than mutations in the nuclear genome
and that they are characterised by a very distinct mutation spectrum, which is related to the mitochondrial replication.
Still the high incidence of mitochondrial mutations was puzzling (on average 1.1 per cancer sample) and has led to much
speculation about the functional impact of these mutations. We observed however, that after correcting for the mutation spectrum
there was virtually no sign of positive selection and the evolution appeared mostly neutral. Could that be?

The dynamics of mitochondrial mutations are somewhat peculiar, because each cell contains 10 to 1000 mitochondrial
copies which are randomly partitioned during cell division. That said, mitochondrial mutations _drift_ and can either 
go extinct or fixate in a cellular lineage. On top of that selection exists at the cellular level, favouring those cells
with a growth advantage. So what are the odds of observing a selectively neutral mitochondrial mutation in cancer samples?
After a bit of pondering, we realised that the cellular selection part may be ignored we only need to consider the number of 
cell divisions until the last clonal expansion of cancer cells. 

But what about the dynamics of mitochondria within that cell lineage which will eventually found the cancer cell population? 
Suppose there are \\(M\\)  mitochondria in these cells. Using ![Kimura's neutral theory](http://en.wikipedia.org/wiki/Neutral_theory_of_molecular_evolution), the probability of reaching fixation in a population of size 
\\(M\\) is \\(\rho=1/M\\).  Fixation takes, on average, \\(2M\\) cell generations.

The rate at which mutations are introduced is \\(\mu = 10^{-7}\\)/bp/generation multiplied by the length of the mitochondrial genome \\(L=16569\\) times 
the number of mitochondria \\(M\\).  Hence the expected number of mutations having occurred within \\(T\\) generations is \\(E[N] = \mu L M T\\).  
But some of these will have died out and only a fraction\\( \rho\\) will have reached fixation, and this quantity lags by \\(2M\\) generations. 

So the expected number of mitochondrial mutations having reached fixation by time \\(T\\) is:

$$E[N_{fix}(T)] =  \rho E[N(T-2M)] = \mu L (T - 2M).$$

No the reality check comes by plugging in some numbers: _Young Seok found about 1 mitochondrial mutation per cancer_. Can neutral theory explain that?

We have \\( \mu = 10^{-7}\\), \\( M \approx 100\\), \\( L = 1.6 \times 10^4\\).  Realistically a cancer cell has undergone about \\( T=1000\\) cell divisions. 
This yields \\( E[N_{fix}(T)] = 10^{-7} \times 1.6 \times 10^4 \times (1000 - 200) = 1.28\\).  Very close, isn't it?