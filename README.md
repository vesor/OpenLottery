# OpenLottery
As we know the biggest problem of lottery is the untrusted center node, which usually results in black box operations.
In recent years, block chain technology successfully get rid of centralized node in the domain of ledger. 
That could be a good clue for designing a lottery system.

## Hence I propose a method for lottery:
Assume we know there is N person participant in. And every one has a unique id.

(TODO: undetermined number of participants?)

For every participant, generate a string S. Then sort the value hash(S), and make the first K participant be the luck guys.

(I consider finding a S to make hash(S) very small is a hard task, because bitcoin use such way.)

Here is how the S is generated:

S = id + LuckyNumber + SumOfAllLuckyNumbers + TimeSeed + Salt

1) id make sure S is unique for everyone. id can be anything such as name/ employee number/ cell phone number/ seat number/ etc.

2) LuckyNumber is provided by every participant him/herself. It makes sure the final lottery result is "controled" by yourself, not anyone else.

3) SumOfAllLuckyNumbers make sure you cannot control lottery result only by yourself. It is controled by all the participants.

4) TimeSeed is to make sure the result is different everytime, in case if we want to do lottery multiple times. 
It doesn't need to be accurate. You can use 20180101A for first place prices, 20180101B for second place prices, etc.

5) Salt could be a very long string, which makes it very hard to compute hash(S). 
So that even if we know all S, it still hard for one to try to find a LuckyNumber which makes a hash(S) small.
Salt can also be provided by the helder of the lottery, which makes sure the lottery result can't be manupilated even if all the participants make an agreement to cheat.

## NOTE: 
for LuckyNumber, if we want to make sure a participant cannot have chance to adjust his/her LuckyNumber according to other one's LuckyNumber, we may need to use a two phase commit way. 

That is: everyone commit his/her hash(LuckyNumber) in first round, then commit LuckyNumber in second round.

It is said Ethereum use such way to generate random numbers.

## Welcome
Since I am quite a idiot in cryptography, I highly welcome experts to check if there are any errors in my method.
