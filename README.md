# dlete

This is a ML project for classifying the length of x8664 machine instructions. 

Obviously you can't use this as a length diassembly engine, I just made it to learn some ML.

It uses a CNN classifier which is trained on the output of 20 vanilla neural nets, each NN is 

trained on a different set of 400k samples and have an accuracy of between 98.5 - 99.1%. I Trained

the CNN on the pool of probas output (predictions from 500k samples) by the NNs and thus learning from 

the mistakes of the neural nets the accuracy increased to 99.43% not much for my effort, but I am happy 

with the results. It also outperformed a voting ensemble algorithm which was pretty cool.

Overall I am bit paranoid that I have some data leakage going on, once do you training on training 

and things like that it is easy to get a bit confused.


Generating the data sets was quite tricky, I decided to use an input shape of 128 bits, rather 

than 120 bits (or 15 bytes for the maximum size legal instruction size) and ignore the last class

which worked a lot better.

Initially I used tracing live code to produce data but the output was very unevenly populated 

by class as expected, which leads to poor learing. So I turned to the capstone disassembler and 

bruteforced random instructions of varying sizes to get a better spread. While

this worked well for the most part, bruteforcing still did not solve all the problems, generating 

any instructions of a length for classes above 11 bytes is very intensive work. 120 bits of imput 

space is a very large problem for a bruteforcing mechanism to produce a legal instruction. I have 

been meaning to do a survey of executable instructions found on an operating system like Winodws and

look at the frequency, but still haven't gotten around to it. For test data sets as a compromise I 

ennded up using some real data from executable modules in conjunction with the generated data from c

apstone, and focused on lengths of up to 10 bytes (11-12 byte instructions seem to be reasonably 

common from casual observation however). 

