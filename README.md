In this project I studied the morphological data (i.e. physical attributes) of a set of 36 different fossils, each corresponding to a different species of prehistoric penguins. The carbon-dated ages of these penguins ranged from anywhere between 62 million years ago (M.y.a) to present day. The contents and results of this project are a simplified form of the model inherited for Bayesian inference in the paper "Bayesian phylogenetic estimation of fossil ages" by Alexei Drummond and Tanja Standler[1]. The link for the paper is here: https://royalsocietypublishing.org/doi/10.1098/rstb.2015.0129.

To model the evolution of morphological data, the paper adopts a generalized Jukes-Cantor (JC69) model. The model is used to set up the likelihood function for the Bayesian inference, where each morphological trait of a given species has $k$ different possible states. For example, the dorsal color of the feet have 5 different possible states - dark, pink, orange, white-flesh, or blue. Thus this particular trait has $k=5$. There are 245 such morphological traits available in the data, and the JC69 model expresses the transition probability of a species to go from one state to another, where $\alpha$, the instantaneous rate of transition between states, is set to 1 in this notebook. The matrix and the transition probabilities are below:

$P_{ii} = \frac{1}{k} + \frac{k-1}{k}e^{-k\alpha t}$

$P_{ij} = \frac{1}{k} - \frac{1}{k}e^{-k\alpha t}$

As for the prior distributions, I had to consider the prior distributions for several different variables, such as the time at the start of the process $T$, net diversification rate $d$ ($\frac{1}{4}$ speciation rate – extinction rate), the turnover $r$ ($\frac{1}{4}$ extinction rate/speciation rate) and the sampling probability with which a fossil is observed $s$ ($\frac{1}{4}$ sampling rate/(extinction rate + sampling rate)). I assumed a uniform prior for $T$, $s$, and $r$, while assuming a lognormal prior for d, with the mean set at -3.5 and the standard deviation at .5. (Speciation rate s the rate at which new species appear in an interval of time, whereas extinction rate is the number of species that go extinct in that same interval of time).

The paper uses the fossilized birth-death process as a model for the prior. In essence, the process models the phylogenetic tree, starting from the ancestral species (here labeled "reference" in the program). It uses a Poisson process to model whether or not a given lineage goes extinct or survives. I do not inherit this process in my notebook for the sake of simplicity, although adopting this would also improve my estimated ages.

All the relevant packages necessary to run the Python notebook is inside the 'environment.yml' file.

Special thanks to R.J. Furnstahl in the course Physics 8820 at the Ohio State University for help with emcee syntax and general syntax.

Citations:

[1] Drummond Alexei J. and Stadler Tanja 2016. Bayesian phylogenetic estimation of fossil agesPhil. Trans. R. Soc. B37120150129. http://doi.org/10.1098/rstb.2015.0129
