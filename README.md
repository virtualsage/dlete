# dlete

This is a ML project for classifying the length of x8664 instructions. 

Obviously you can't use this as a length diassembly engine, I just made it to learn some ML

It uses a CNN classifier which is trained on the output of 20 neural nets each trained on

a different set of 400k samples and having an accuracy of between 98.5 - 99.1%. Training 

the CNN on the pool of probas out put by the neural nets and thus learning from the mistakes 

of the neural nets the accuracy increased to 99.43% not much for my effort, but I am happy with

the results.
