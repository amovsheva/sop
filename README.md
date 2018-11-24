Broadly speaking, I am interested in investigating physical and biological systems in which, one can observe interesting phenomena--evolutionary/population dynamics, pattern formation or emergent phenomena from collective behavior--that is driven by fundamental physical principles. The goal is to identify the underlying rules that govern these systems and construct from them a mathematical theory that can not only describe the phenomena but also generalize to more complicated scenarios. My interest in this flavor of problems was cemented over the last year during my work in theoretical evolutionary genetics with Professor Matveyev.

The goal of my research is to estimate, given a specific gene for any two organisms, how many generations ago did they share the ancestor from whom they inherited that gene. For example, our closest relatives on the evolutionary tree are chimpanzees. I want to answer the question how long ago did our most recent common ancestor live? I am building a probabilistic model that can estimate this quantity, which is called the coalescent time. Current (paleontological) methods put the coalescent time for humans and chimpanzees to be somewhere between 4 to 13 million years ago, which is quite a wide range. We hope that our model will validate and make more precise this estimate as well as be applied to organisms for which we do not have well-preserved records.

Formally, we want to construct an algorithm that inputs two sequences of nucleotides (DNAs), which we assume to be of equal length, and outputs the coalescent times. However, mutation and recombination add randomness to the inheritance process. To account for this, we treat coalescent time as a random variable and calculate a probability distribution for the coalescent time of each nucleotide in the DNA.



To be precise, in our approach, coalescent time for two DNA depends not only on the discrepancy vector but also on the choice of the position i in the sequence of nucleotides that make the DNA. We postulate that the distribution we are looking for can be derived from the dynamics of genes in a population is represented by a directed (random) graph. By definition, a graph is a collection of directed edges (parent-child relation) that connect vertices (spices in the population). In our case, graphs have additional structures. Firstly it is a function t from the collection of vertices into nonpositive integers that is interpreted as time. Note that the number of vertices for the given time is fixed and is equal to n - the size of the population. The edges can go only from vertices at times t to vertices at time t+1. A vertex can have only two incoming edges (we interpret them as parents). Vertex a also carries a label that is supposed to represent genetics of the individual. One piece of data that makes the label is a function f_a on the set of integers from 1 to N, called X (interpreted as positions of nucleotides in a genome of length N), into the set of 0 and 1. 0 and 1 are supposed to represent different types of nucleotides. We work only with two kinds of nucleotide. In addition to f_a a label of a vertex a with two incoming edges carries an information about decomposition X = X_1(a) union X_2(a). These labels have to satisfy one consistency condition that will correspond to recombination genetics. Let vertex a have two incoming edges from vertices b and c (b and c correspond to parents of a). We require that f_a = f_b on X_1(a) (mother subset) and f_a=f_c on X_2(a) (father subset). We will call b the mother of a and c the father of a. We will refer to the structure just described as a rigged graph.

A rigged graph has a property that can be used to formally define coalescent time. Fix a terminal point a with t = 0. Fix i in X. There is a distinct path (nucleotide history) in the graph that terminates at a, which is determined by the nucleotide in the position i. To reconstruct this path we have to follow edges in the opposite direction. In case the vertex has two confluent edges, we need to see what subset (mother’s or father’s) i belongs to and depending on this, choose the mother or father vertex at level t - 1 to go to. If we fix two terminal vertices (e.g. two modern organisms) and choose position i in the DNA (same for the two vertices) we will get two paths that will meet at some time t, we call coalescent time. We want to find the probability distribution p(i, f_a, f_b)(t) for the coalescent time t. During the course of the work we derived equations that relate p(i, f_a, f_b(t) and p(i+1, f_a, f_b)(t). Right now, we can find p(i, f_a, f_b)(t) for small 'i' under some simplifying assumptions. I’m currently working to find on how to drop these assumptions.

We have also tried to tie in selection into our theory. The simplest case is when there is selection on one nucleotide. In the case when X consists of one element the structure of the rigged graph simplifies: in the decomposition X = X_1(a) union X_2(a) one set must be empty, the function f_a coincides with its value. This data enables us to replace rigged graph by a tree (or better a forest) that captures the i-th nucleotide dynamics. If X_1(a) is empty we drop the arrow from 'b' to 'a'. Otherwise, we drop the arrow from 'c' to 'a'. The probability measure on the full set of a rigged graph is presently out of reach but its push forward on the set of such trees is much more feasible. ??

In the setup without selection, the probability of having an edge from vertex i to j is equal to 1/n. If selection is introduced this probability becomes some p_ij (0 < i, j < n+1), a component of a Markov matrix. One of the problems we tried to solve is finding the expression for p_ij that accounts for selection coefficient s. For this, we have to reverse some known Markov process q_ij(s) in time. The central component of solving this problem is finding the stationary distribution of the forward Markov process. Since the matrix’s size and complexity of its terms depended on the size of the population 'n' my solution to this problem was to send 'n' to infinity. The components of the matrix are a certain sum. In my limit, they become integrals that can be approximated with the stationary phase method. I borrowed it from the course on quantum field theory where it is applied to infinite-dimensional integrals. I learned of this approach during the summer before my senior year in undergrad from Professor Jevicki’s lectures he gave his research advisees (of whom I was one) and from online QFT lectures from the Perimeter Institute that I watched concurrently.


In my research, I’ve enjoyed finding and leveraging both analytical and computational tools from physics, statistics, mathematics and CS. This experience makes Stanford Applied Physics’ interdisciplinary environment very appealing. While researching the department and talking to current graduate students, it stood out that the department really encourages taking courses and collaborating with people in other disciplines. It would be very exciting to bring in new theoretical/computational ideas inspired by the cutting edge research happening in so many different fields. I also want to look at real data and collaborate with experimentalists so that I can make a connection between theory and experiment, something that I have not yet had the opportunity to do. I am very interested in Professor Daniel Fisher’s work in evolutionary population geneticс, especially his paper on the simulation of spread of a mutation in an evenly dispersed population as random individuals of the population moved to random distances in random directions. It showed how changes to probability distribution of distances effected the global spread speed of the mutation. I wonder whether it was possible to prove this behavior analytically (meh). My interests are not restricted to genetics, however, and I am also interested in Professor Andy Spakowitz analytic approach to the mechanics / chemistry of organic molecules.



/Having had some formal education in physics, mathematics, and statistics my interest is not restricted to genetics. What I found fascinating about working with Dr. Matveyev, was to see how methods and techniques used in other (sometimes remote) fields can be applied to our research. I want to utilize the interdisciplinary nature of Stanford Applied Physics department to be able to collaborate with people in different departments to become more experienced in applying methods from other fields to my study. I would love to be able to work for Daniel Fisher, for example. I have come across his papers while doing a survey of the landscape of theoretical evolutionary genetics. I was especially intrigued by his paper on the dynamics of a mutation in a population as individuals of the population move in a random direction to random distances. I could learn a lot working for him since I am new to theoretical evolutionary genetics./

The kind of research I like to do consists of deriving basic mathematical or physical axioms of the process / system at hand. These axioms would govern the entirety of the system’s behavior so by building a theory using these axioms would (hopefully) be able to catch / explain the global phenomena that happen to the system. I like to be able to take a system like that and solve it in the simplest of cases (with the most restricting and simplifying assumptions). By introducing one new parameter at a time I would solve the more generalized system. This kind of incremental approach really interests me because it makes me understand how each parameter contributes to the complexity of the system and it is systematic leading a more clear and logical way of doing research.
