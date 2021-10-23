# Grammar Engineering

 This project is to engineer a grammar of a small subset of English using NLTK with Python3. It contains a pure context-free grammar(P2C.cfg) and also a   feature(unification) grammar(P2.cfg).

 p2.py is a small programme that compiles a parser, which applies on two files, p2.pos and p2.neg, one with positive exapmples and one with negative examples

## Lexicon and Context-free Grammar

 To implement context-free grammar for positive examples, some parts of speech(POS) are introduced to represent the grammar rules in English, like Det, Prep,  Adj, etc.. The answer,is definitely able to parse all sentences in p2.pos but also some sentences p2.neg, so there are still several drawbacks. 
 1. it can not distinguish between singular and plural nous, neither nor between various verb forms.
 2. ambiguity is unavoidable, since some words can be treated as different POS. for example, 'in the kitchen' is once an adjunct and once is an argument.

## Subcategorisation and Feature Grammar

To solve the above issues, the Feature Grammar introduces number agreement and subcategorisation, as well as tense for this simple example.
The parse rulse is like, for grammar:

VP[Sub = ?arg] -> V[Sub = ?arg] 

the 'Sub' must keep consistent, no matter how it is named. Based on this, the idea is specific in the report.

## Reflection

Since my poor English, there are issues in both grammars, I list them here and I will restore it when I am free(will I?).

1.there is a significant misunderstanding about adjunct and PPs, like
V[TENSE = present, NUM = pl, SUBCAT = [ HEAD= np,TAIL = [HEAD = pp, TAIL = nil]]]-> 'drink'
I have an adjunct here, but for sentence ' Bart and Lisa drink milk in the kitchen ':
A rule of the form VP[ SUBCAT=nil ] -> VP[ SUBCAT=nil ] PP  would have solved this.

2.NP[ NUM=?n ] -> ProperNoun[ NUM=?n ] | Nominal    Here I lose the NUM of the Nominal. 

3.V[TENSE = present, NUM = sg, SUBCAT = [ HEAD= np,TAIL = subsentence ]]-> 'drinks'

4.PP -> Prep Det Noun | Prep Noun Overly specific. 
