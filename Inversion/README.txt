README File for Programs Submitted for Comprehensive Exams
Paul Cottle  -  January 31, 2013
------------------------------------------------------------
This is wat I've accomplished thus for on the inversion of lidar data.
Although writing and playing with these scripts has been informative, since
designing them I have learned a great deal about the CALIPSO data analysis process
that will be useful in going about this in a much more effective way.
However, they at least show I've been thinking abot the problem and working
on it, even if in simplistic fashion.

These programs are very much in flux, and none are what I would call complete
so some of the algorithms are already
out of date (i.e. I've shown them not to work sufficiently well but haven't
changed them yet)

Goals:
1) To create a forward model of receiver signals from elastic and raman scattering.
This includes adding a background and noise component and inserting layers of
particulate sctterers

2) To Attempt a simple inversion of a raman scattered signal (later elastic as well)

3) To determine background and noise levels in a signal

4) To write a latin hypercube sampler

5) To write a Markov chain monte carlo model to be applie to noise components and other
analysis of uncertainty

Modules:

lidar_tools_v1: tools for generating a baseline elastic profile.  The class Ealstic is a simple
bucket of properties at the moment as I wanted to keep it flexible until the properties
I needed were better determined.  

raman_tools_v1: similar tools to lidar_tools, but for raman-scattering instead of elastic

pricess_tools_v1:  Tools for adding and calculating noise and backgrund, and the tool
'raman_analytical' that uses an analytical inversion of Raman scattering to determine
extinction coefficients as a function of altitude

mcmc: a simplistic first attempt at designing a random-walk markov chain using the metropolis-
hastings algorithm.  This can be done with any number of tools, but I worked this up
as a way to help me understand te process

lhc_samplers: a tool for latin-hypercube sampling of data sets.  I'm still working on expanding
it to multi-dimensional data sets

inversion_tools:  A start at a way to invert a profile by treating it like the linear
multiplocation of an unknown diagonal matrix A and a vector of desired values (such as
extiction coefficients)  If such a matrix can be generated, it can be employed in
a regularization scheme such as least difference or Tinkhonov regularization.