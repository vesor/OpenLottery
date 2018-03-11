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
It doesn't need to be accurate. You can use 20180101A for first place prizes, 20180101B for second place prizes, etc.

5) Salt is optional, it could be a very long string, which makes it very hard to compute hash(S). 

## NOTE: 
id, TimeSeed, Salt all must be determined *before* LuckyNumbers are provided. Otherwise one can itentionally select an  id/TimeSeed/Salt which makes some hash(S) small, by trying different values of id/TimeSeed/Salt.

For LuckyNumber, we need to use a two phase commit way. First, everyone publish/commit his/her hash(LuckyNumber). Then everyone publish/commit LuckyNumber.

This make sure a participant cannot have chance to adjust his/her LuckyNumber according to other one's LuckyNumber/SumOfAllLuckyNumbers.

It is said Ethereum use such way to generate random numbers.

## Welcome
Since I am quite a idiot in cryptography, I highly welcome experts to check if there are any errors in my method.
