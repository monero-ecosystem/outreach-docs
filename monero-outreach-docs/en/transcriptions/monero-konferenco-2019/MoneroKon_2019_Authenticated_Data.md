thank you again let's give Bennet Ben

fish along with joint work with Benedict

buns and Dan Bona a hand for

authenticated data structures for

blockchain consensus with minimal

storage thanks Brandon

okay so

at Green

got it no that's green arrow perfect so

okay

block genes are transactional databases

so naturally as with any transactional

database they grow in size with use but

the significant thing about you know

block chains like Bitcoin or Manero is

that they're supposed to be

decentralized in their maintenance so

they aim to have many many participants

called miners all be able to verify

transactions that update the database

and as the size of the database grows

then the the size the amount of storage

that that all the participants in the

system needs to maintain in order to

verify transactions grows as well and if

it grows to be too large to some degree

it inhibits the goals of

decentralization because we want to make

it as easy as possible for anyone to be

able to participate in consensus not

necessarily using a tremendous amount of

storage you could imagine a future where

even like you know a SmartWatch or

something very with very very little

memory to still be able to participate

in verification of the entire blockchain

right so let's start with a very

simplified view of what blockchain

consensus looks like in order to explain

what I'll call the difference between

stateful consensus versus stateless

consensus which will have involve

minimal storage among the miners

participating in consensus so in

stateful consensus transactions come in

and miners all listen to the

transactions they all tend the

transactions to their log and so

everybody is storing a copy of this

database now of course that could be

great because highly high replication is

a good thing for fault tolerance but you

might not want to design a system

where every single person participating

in consensus absolutely needs to

replicate the entire you know log of

transactions so the question is you know

what can we do to first of all so how do

these how do how do we handle miners

comparing that they are all talking

about the same database without sending

the entire database to eat to each other

well we know that's easy right we just

could compute a hash of the database and

compare efficiently now that's not

actually how it's done because we also

want and this is a little of a form of

stateless verification we want a a miner

who you know to who is not storing the

entire transaction log and able to

compute a big hash over everything to be

able to just store what's called the

state head and be able to immediately

verify that every other miner in the

system is still talking about the same

database let's say this miner is only

listening to transactions as they happen

not storing the whole database how can

that miner verify everyone else is still

talking about the same database well we

just defined the hash in a way that can

be computed in a streaming way and

that's and that's like this where the

hash gets updated by hashing in the

previous hash head with a new update and

that's where we get our you know our

blockchain so what happens now when we

add rules to this database well then

somebody who's just listening to the

system maybe they can verify that

everybody else still agrees about the

same sequence of updates all the same

the same transaction log but certainly

this miner is participating in the

system with no storage has no way of

verifying that new transactions coming

in are actually correct or not right for

example one rule is well this new

transaction spends the same coin that a

previous transaction spent so that

transaction should be rejected but this

miner with no storage has no way of

knowing this so what we would like from

stateless verification

the ability of a miner with very very

very small compact storage like just

storing a little hash representation of

everything that's happened so far would

be able to you know listen to

transactions coming in and say up this

should be rejected or up this should be

accepted so how could we possibly do

that how could we possibly define these

compact hashes in a way that you know

all the nodes can just store this hash

and still be able to check the validity

of transactions well clearly we need

something additional okay some kind of

additional proof that will be sent along

with transactions so we'll make the

transaction slightly more complicated

but what I'm going to talk about as well

how is that proof generated how

efficient is it and who generates the

proof first of all but to take a step

back just from maybe a philosophical

perspective or you know a more abstract

view what we're calling for is a

separation between the consensus layer

of the blockchain and this the state

storage of the box chain and both of

these we want to be decentralized or

distributed and fault tolerant but we

can really look at them as two different

systems and one which aims to you know

maintain the and store all the data in

the blockchain and and be able to

provide basically proofs and state

updates to the consensus which is really

not focused on on necessarily providing

you know a really high performance

database but rather just being able to

participate in agreement and and verify

that things look good so let's focus on

a concrete now it's like specific

example of a blockchain model and so

I'll focus on UT X OS as since it's

relevant to both Bitcoin and manera so

what are you TX O's it's in case you

know just as a reminder whatever every

transaction consumes inputs think of

like coins assigned addresses that are

the inputs and transactions every

transaction creates outputs

coins are reassigned to new addresses

and UTX those are simply the transaction

outputs that have not been consumed yet

so they can still be spent they're still

valid inputs to new transactions and

that's really what the miners all the

miners really need to agree on what are

the set of valid records which are still

valid and that's all you really need to

know in order to be able to verify the

correctness of of a transaction aside

from other things that don't depend on

the state of the debate database like

the transaction is well formatted so

this small compact hash thing that was

talking about it's going to be some kind

of commitment to the to the UT Exocet

and we'll talk about how to update that

commitment dynamically and how to and

how to verify proofs that that something

is in this set or not and the general

cryptographic technique that is needed

for this is called an accumulator we all

know a or maybe some of us know of like

the most popular example of an

accumulator which is a Merkel tree and

I'll and I'll talk about that in a

second and this kind of work is about

doing things that are better than Merkel

trees for this for this task but

abstractly what the accumulator does is

it allows you to give a short proof that

say all the UT exo's in the transaction

are actually part of the UT Exocet okay

so let's say we have this kind of

simplified you know picture of a

blockchain then the proposal for these

utx of commitments which was which was

actually you know propose a considerable

time ago was to say okay well let's say

every every block can basically keep

track of consensus can keep track of

what is this like small hash commitment

basically to you know all the all the UT

X OS and so let's just imagine that we

have a way to do that we'll talk about

in a lot more detail how that can

possibly be done but let's say consensus

is able to keep track

of a this accumulator hash that

represents with you know very very

little storage the UT Exocet and then

it's possible to be able to prove that

something is in there so one way to do

that is to use a Merkel tree where this

the UT x oak commitment is simply the

root of a Merkel tree over all the UT x

OS and the transactions would then

basically provide inclusion proofs which

can be done with a log in size path up

the Merkel tree and and so every

transaction would basically include a

Merkel proof that the reference duty XO

and the transaction is inside this

Merkel tree and miners would say okay

this looks good but they don't actually

need to store the whole UT Exocet so

stepping back and looking more broadly

at accumulators so accumulators like

what we didn't talk about what that

Merkel tree example was also you know

how do how do things get added to the

accumulator how do things get added to

the Merkel tree can can can we do that

in a distributed way so that people who

are not storing the entire state of the

accumulator and they see a new

transaction can all simultaneously

update the accumulator to get a new

state so update the root of the Merkel

tree you can think of

so Merkel trees are examples of

accumulators there's also RSA

accumulators which is the basis of the

work that I'm going to present in this

talk and there's other types of

accumulators they all achieve different

kinds of trade-offs one nice thing about

RSA accumulators and and these pairing

based accumulators or that the the size

of the proof is constant size as opposed

to log size which the Merkel trees have

so let's say we were using Merkel tree

witnesses for this you know four four

if you know let's say we were using

Merkel tree witnesses for these

transaction proofs

well then let's say that we had a

hundred million UTI echoes every Merkel

tree witness

you know while one witness doesn't seem

that large they together they get to be

quite large right and so we require

about eight hundred bytes per UTX oh and

so that's a lot of extra storage to keep

around so even though we've reduced the

storage of the miners in the system who

now only need to store the root of this

Merkel tree every transaction is going

to have this this this this Merkel tree

proof and since many transactions not

only reference one you TXO but many many

you TX OS

whereas before those u TX hos could just

be a like 64-bit index into the minor

storage that they already have

referencing something they already have

now it has to include this large Merkel

waitis so you know the communication in

the system could potentially blow up by

like a factor 100 so that's not good and

the desiderata for you know our design

to sit errata are not only to have short

membership awarenesses better

efficiently updatable etc but also to be

able to aggregate witnesses and even

better to be able to to batch generate

and to verify them you know and

efficiently in a batch so you could

imagine a transaction that references a

hundred u TX OS and just have to have

one short membership witness that

accounts for them all and or miners

would be able to take many different

transactions and verify in a batch all

the membership witnesses so that's our

goal in the in in this current work and

the the starting point for our new

accumulator construction that has these

properties is RSA accumulators so very

briefly what how does an RSA accumulator

work there's there's there is a trusted

set up and I'll talk later about how to

do this without trusted setup

but the RSA accumulator is based on an

RSA modulus with an unknown

factorization so n equals P times Q P

and Q are secret Prime's adding

something to the accumulator is just

taking the hash of that thing and taking

the current state of the accumulator

call it AI and raising it to the power

of the hash of that element so you can

think of after we add an entire set to

the accumulator what the accumulator

looks like is its G to the you G is the

initial state just you know some

generator in n ZN these are numbers

modulo n and you would be a product of

the hashes of all the elements that are

in the set right so adding a cumin

generating this accumulator commitment

to the entire set amounts to multiplying

the hashes of all the elements in the

set together getting basically and and

then and then raising G to the U and so

G to the U is just one integer modulo n

so it's just one constant size integer

and deleting an element from the

accumulator would amount to cancelling

out the element we want to delete from

the exponent so if we have some way of

getting a I to the 1 over H of X then we

can delete from the accumulator and

we'll talk about how that could be done

so what's a membership witness in this

case

well a membership witness is supposed to

prove that you know that your your hash

of your of your element was included and

for now I'm just going to ignore the

hash and just talk about you know the

the element that you're the member the

member of the accumulator that you're

trying to prove is X and X is already

the hash of the actual element that

you're you know that's in the

accumulator so you can think of X as the

hash of your your UT XL so if you can

provide a to the 1 over X

namely a value pi such that pi to the X

is equal to the state of the accumulator

then you've shown that X is in the big

product in the exponent of the

accumulator and in order to prove that

something is not in the accumulator you

want to show that X does not appear in

this big product in the exponent in

other words X is co-prime in fact with

the product of elements in the

accumulator one thing I was on the slide

but I didn't mention it verbally was

that this special hash function Maps

things to primes so the output of every

hash is actually a prime number and and

that guarantees that if we haven't added

an element to the accumulator yet then

it will be co-prime with that big

exponent in the accumulator and so then

we're able to generate these efficient

non-membership witnesses which can be

easily verified because of this this

trick which finds these coefficients a B

such that ax plus B u is equal to 1 and

that can only be done if X is co-prime

with you so there's also other things to

do state those subjects that won't get

into that how can we aggregate

membership witnesses we have one

membership windows pi 1 such that pi 1

to the X is equal to the accumulator

state we have pi 2 such that PI 2 to the

Y is equal to the accumulator state so

then we can use this thing called

Shamir's trick which also generates

these you know fancy coefficients a and

B such that you get this relation ax

will be Y is equal to 1 and if we just

produce the the membership witness PI pi

PI 1 2 which is PI 1 to the B times pi 2

to the a that actually is an aggregate

membership witness and that means that

all membership witnesses per transaction

block can just be represented with like

3,000 bits

right so you'd have a transaction that

references many many many UT EXO's

instead of having their membership proof

blow up / UT EXO as with Merkel tree

proofs with accumulators we can just

give one single size size membership

proof cool so that was one of our goals

and let's talk about deletions so

unfortunately the leading things

requires knowledge of the factorization

of P and Q naively however and we

definitely don't want to do that because

nobody should know the factorization

otherwise you know the system is broken

but a cool thing is that you can observe

that if you have the membership proof

for an item then you can actually delete

the item because the state of the

accumulator after deleting is simply the

membership proof for that thing because

you already had the the one over x route

that was the membership witness so if

you have the membership witness and that

was already generated for your etyek so

then after you spend it then you can

brog broadcast that and say okay this is

the new state of the accumulator in fact

all the miners who saw the membership

witness now know the state of the

accumulator without that element of

course though transactions happen in

parallel so we would want a way of

taking many many many membership

witnesses for different items and

finding a way to combine them in order

to batch delete multiple items and

that's something that we show how to do

so that means that for this blockchain

application the miners who are listening

to the system and I'll talk you know

give a better visualization of this are

able to update the state of the

accumulator when transactions happen to

both add new transaction outputs to the

UT Exocet which is represented by the

accumulator or delete previous now spent

transaction outputs from the accumulator

all without knowing the trapdoor or any

you know trapdoor information so what

about trusted setup we don't like

trusted setup so well one potential

thing to do is just choose a

large unfactored Belen but that would

have to be really huge another thing is

to choose something that hasn't been

broken in a long time so like or choose

some cryptographer like Ron Rivest who

maybe people trust who has you know he

claims he forgot the factorization of

this one particular artists a modulus

maybe you can use that but another thing

you can do is use class groups and class

groups are basically a drop-in

replacement for RSA groups because they

are there they're a group with where the

order is unknown that's a little if you

know what that means that's great

otherwise don't worry about it it's just

the the class groups you know basically

have the key property that you need from

RSA groups to make these accumulators

secure and they're a bit more

complicated to work with but we already

have some open-source implementations

that deal with them so that's pretty

cool so the the verification of

witnesses takes a long time because it

does group exponentiations 2500

exponentiations per second so that would

be pretty slow if you're trying to do a

big full sync of the blockchain so what

can we do to improve that well we'll use

this trick called a proof of

exponentiation it's based on a trick

that was used for these verifiable delay

functions if you've heard of them but

basically it's a it's a way of proving

efficiently that you know X to the to

the alpha is equal to Y without having

the verifier to actually do this

exponentiation themselves what the

verifier ends up doing is just reducing

alpha modulo some small 128-bit prime

that's chosen randomly in the protocol

and so you might say well asymptotically

then that's the same thing reducing

alpha mod L is asymptotically the same

complexity as taking an exponentiation X

to the Alpha is equal to Y but in

practice it's about 5,000 times faster

so what does the security based on it's

based on this complicated thing called

an adaptive Brutus sumption actually

it's not that complicated it's basically

saying that if I have an element of the

group so whether RSA group or a class

group and I choose a random prime then

it's difficult for me to output a 1 over

L root meaning something which raises to

the L power gives me back that thing

that I chose W and adaptive root is

what's needed for this thing to be

secure we have a theorem which says that

holds in generic groups nothing is

actually a generic group so that may not

mean too much but cryptographers like to

do that so what does this look like now

with put together with with our you know

basic block chain system block chain has

a header transactions it has a spend set

things that were things that are being

spent it has a new set and things that

are being created and and bunch of

signatures we have a previous state of

the accumulator which represents the

current unspent set sorry not the spent

set the you TXO set is the unspent set

so we will what we'll want to do is

we'll want to batch delete the spent set

s from the accumulator and batch add the

the new set of newly created utx O's

from into the into the accumulator we

also have batching for adds I didn't

talk about that but it's a nice trick

and then in the end what these two

things produce are just a bunch of

proofs of exponentiation in fact one

proof of exponentiation for the entire

batch delete one proof of exponentiation

for the entire batch add and and this

encompasses the membership witnesses as

well so what the miners end up verifying

are just two proofs of exponentiation

which is basically just like two

reductions module

and 128-bit Prime and and then verifying

the signatures so it's quite light in

terms of verification on the minor take

this with a huge grain of salt since you

know I I mostly do things on paper but

you know back of the envelope

Merkle trees you can do about 100,000

ads or verifies per second ad would be

like adding something adding aut XO to

the accumulator verifying would be

verifying a membership witness they're

about the same complexity in terms of

the operations you're doing your you're

evaluating a bunch of sha-256 hashes for

RSA accumulator ads basically what you

have to do one exponentiation per ad

even with that chat and you know just

just taking numbers on my laptop that

comes to about like 600 per second and

and for verification though because of

these tricks which which which give us

this ammeter zation and and really each

verification is just a few reductions

modulo 128-bit prime that's quite fast

you can do about 20,000 of those per

second how am I on time three minutes

okay

so very briefly we can generalize this

from UT EXO type systems to account

tracking systems so systems designed

more in the in theorem style which

tracked account account balances and

what we would be using there instead of

accumulators our vector commitments

Merkle trees are also vector commitments

in fact but RSA accumulators are not so

for a vector commitment you need to be

able to prove that the item is not only

in the set but it's in the set at a

particular position and that and and for

a key value store what you need is

actually a very a sparse vector

commitment so you need to be able to

prove that you know the vector at this

position keyed by this value which is a

very very long vector is equal to this

particular value and then you would do

all the same kind of tricks you you have

a way of proving that something at a

particular key index of the of the key

value store is equal to some balance v1

and something is equal to b2 and then

you can locally verify the rest of the

transaction so how do we do that well

you could use Merkel trees but they have

kind of the same issues we talked about

before there's other previous things

that were constructed for four-vector

commitments but they have extremely

large set up parameters and so in fact

for the for the key value store it would

just be contou de lis infeasible because

you basically have to have set up

parameters that are linear in the length

of the vector so what we do is we have

built something that has constant size

common parameters and still retains

these short you know proofs but

something is a certain value at a

particular index and we can do that just

by using the same accumulator tricks we

used just basically we start with a bit

vector and we represent each bit as you

know it's 1 or 0 so it's either in the

accumulator or not and because we have

these batching and techniques we can

prove a whole bunch of bits at once in

one single constant size proof and so

that like immediately gives us these

constant you know openings for vector

commitments with basically no large set

up parameters because the RSA cumin

didn't have any large set of parameters

so takeaway points shifting worked from

miners to users we put a little bit more

burden on the users to keep track of

membership witnesses it's a whole big

debate whether that's reasonable to ask

users to do or not but you could imagine

also services which you know and many

you know distributed competing services

which which which which do this for

users so you could also think of this as

basically a more load balanced

diverse sort of system of of

participants who are playing different

roles for the system so ones that are

participating in consensus ones that are

storing the state in the load-balanced

distributed way being able to provide

membership witnesses to users then which

then gets you know passed off to the

consensus layer which can really involve

anyone running on any kind of any kind

of you know set up so that is all I have

to talk about today

a bunch of references and there's a

paper and also an implementation by

Cambrian labs thank you

[Applause]

