# Learning notes from Rosalind python challenges

Emeline Favreau, UCL, 2022

## On a Mac

I have been told that the vanilla python3 version on mac is not well connected to other applications. I downloaded Python3 using miniconda for OS Mac. I downloaded BioPython (set of tools for computational biology). I use Anaconda Navigator, set the Application Jupyter Notebook on miniconda3. Each challenge has its own file saved on [Github](https://github.com/EmelineFavreau/beginning-in-python).

## Data input

**For a text file**

    text = open("rosalind_dna.txt", "rt")

    dataset = text.read()	

    text.close()

## Simple methods on a list

This **counts** the elements in a list

    list.count()

This is useful in a loop to **iteratively add an item to a list**:

    list.append()

This measures the **length** of a sequence located in a list called *record*

    len(record.seq)

This **rounds** to the 6th digit after the comma

    round((float(ccount) + float(gcount)) / len(record.seq) * 100, 6)

## Data types

I am still a bit fuzzy here, but so far I've learnt:

**Integral**

    n = dataset.split()[0] # total experiment months in Fibonacci rabbit challenge
    n = int(n) # method to change a number/string to an integral to be able to use it in a loop

**Float**

    float(ccount) # represent real numbers and is written with a decimal point dividing the integer and fractional parts
    
## Useful syntax and modules for data wrangling

I used re for **greping** things

    import re # the regular expression module

I used SeqIO to read in a **fasta** sequence

    from Bio import SeqIO

A basic **loop** (no curly bracket à la R)

    for month in range(1, n-1):
    	print("current month:", month)


A loop that stores things incrementally in a list

    # create empty list
    res = []
    
    # calculate GC% for each sequence, save it in a list
    for record in SeqIO.parse(filename, "fasta"):
        dataset = record.seq
        ccount = str(dataset.count('C'))
        gcount = str(dataset.count('G'))
        thisseqlength = str(len(record.seq))
        gcpercent = round((float(ccount) + float(gcount)) / len(record.seq) * 100, 6)
        res.append(gcpercent)


This trick was cool to learn

    # slice(start, end, step) here the step is one step backward
    reversedataset = dataset[::-1] 


    # create a translation table, and then translate
    # importance to use str to convert to a string
    # This static method returns a translation table usable for str.translate().
    trans = str.maketrans('ATGC', 'TACG')
    # The translate() method returns a string where some specified characters are replaced 
    # with the character described in a dictionary, or in a mapping table.
    reversecomplement = reversedataset.translate(trans)

## Translation R - Python

* A Python list is used like a R vector, is written with square brackets. e.g. `bocaderiafruit = ["clementine", "orange", "pear", "tomato", "mango"]`
* A Python method is like a R function, is attached to an object with a full stop and followed by round bracket. e.g. `text.close()`
* A Python module is like a R package, is loaded with `import MODULE`
* A Python function is like a R function, is written with square brackets.

## References

* Write in Markdown: https://itsmetommy.com/2021/09/24/markdown-preview-using-sublime-text/

