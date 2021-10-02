# Hopfield Network 

**Authors**: Alessandro Fella, Lucia Depaoli, Lorenzo Mandolito and Simone Mistrali 

Project on Hopfield Network Model for Laboratory of Computational Physics at UniPD.

## Theory

A Hopefiled network is a form of recurrent artificial neural network  and a type of spin glass system (Disordered system) based on the Ising model. Hopfield networks serve as content-addressable ("associative") memory systems with binary threshold nodes, or with continuous variables. Hopfield networks also provide a model for understanding human memory.

This spin system has many nontrivial minima, it is  a neural
network where patterns are intentionally generated by an external agent, by encoding them in the coupling matrix $J_{ij}$ between neurons, which are biologically realized by axons. In
this case each ![formula](https://render.githubusercontent.com/render/math?math=e^{i \pi} = -1) $$ represents a synaptic efficiency, i.e. the kind of transmission of the axon from neuron $j$ to neuron $i$. We will map neurons to spins and $J_{ij}$ to their coupling, thus translating patterns into energetic minima.
Biologically, a neuron is activated when the incoming electrical signal overcomes a
threshold. We define neuron states as
$$
S_i = +1\, \text{(excited), and } S_i = −1\text{ (at rest)}
$$
and a local field collecting all other impulses as
$$
h_i =\sum_{i=0}^NJ_{ij} (S_j + 1)
$$
Given a pattern $\xi^\mu=\left\{\xi^\mu_1,\dots, \xi^\mu_N\right\}$, with $\xi^i_1=\left\{+1,-1\right\}$, this is essentially a spin configuration. We can retrieve the couplings matrix in the following way:
$$
J_{ij}= \frac{1}{N}\sum_{\mu=0}^{P-1}\xi^\mu_i\xi^\mu_j
$$
 where $P$ in the number of patterns. For semplicity we apply the so called *Hebb’s rule*, so we neglect the auto-interation $J_{ii}=0$.

We use the following update rule (i.e *sign* rule):
$$
S_i(t+1)=\text{sng}\left[\sum_{j=1}^NJ_{ij}S_j(t)\right]
$$

## Project

In this project we basically try to figure out if this type of model works fine using different patterns ($1$-D and $2$-D), i.e given a corrupted pattern $y^a$ (i.e. a pattern $y^a_i = \xi^a_i$ with probability $q<1$, otherwise $y^a_i = -\xi^a_i$ with probability $1-q$) it can reconstruct the original pattern $\xi^a$ with the *sign* rule.

The first part shows a simple example using random generated patterns made by $+1$ and $-1$ numbers and random corrupted patterns, defined by a grade of corruption $q$ respect to the original ones. We have see the averaged mean of pattern retrived by varying the number of patterns given different probability of corruption. 

The second part is focused on a simple $2$-D toy model, we use as a pattern the number of the handwritten MNST database. We try different approach:

- We use the vanilla database with poor results.
- We crop the images and in this case we can see that the model can correct retrieve up to $5$ images using $10\times 10$ images.
- We crop and vary the number of patterns.
- We crop the images to $14 \times 14$ pixels and apply a so called *nearest neighbor* $J$, we set to $0$ the interaction between pixels which are farther away than a given distance.

## Requirements & Contact

To properly run this project please clone this directory and from a terminal run this command:

``` python3 -m pip install -r requirements.txt```

Contact Simone Mistrali at simone.mistrali at gmail.com for any questions or comments.

To properly see the formulas please set the light theme on Github settings.
