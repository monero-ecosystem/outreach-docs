Surae: Next up we have Sarang Noether one of the other paid members of the Monero Research Lab and he is here to speak about
transaction efficiency then and now.

Sarang: Hello everyone, I'm back again. I've been randomly appearing throughout the conference to help out as needed, so I will be talking today about transaction efficiency a little bit then, and a little bit now. And part of the goal is to kind of give a nice kind of look back to how our transactions have evolved in terms of size and time efficiency over time, and kind of what we're doing to improve those. 

So I'm not really going to be talking about kind of like big fancy new scaling solutions but just some things that we've done in the past and just a kind of a nice opportunity to look at where transactions might go in the near future. So Click I see why people hate this, huh? Ha ha. Thank you No Ok, there we go. We're good. All right, first of all my usual disclaimer. I speak only for myself Monero research lab is a work group of the Monero project But everyone in it kind of works on their own according to their own research agendas, so I'm just speaking for myself here and I'm also a financial disclosure that I do receive funding support from the monero community through the CCS. Like Brandon was saying.

So first of all, I'm talking about transaction efficiency What do I mean? So I'm not particularly talking about anything to do with privacy here, although transaction efficiency can open the door to kind of changing parameters in the protocol over time that can affect privacy. Things like ring size is the most common example, but we're going to be looking at three particular aspects of efficiency, the first of which is space That's a rocket which goes into space. The second one is generation time and by generation time I mean if I want to construct a transaction that transfers funds from my wallet to someone else, that obviously is going to take some amount of time to do signatures and different kinds of constructions. There's a whole bunch that goes into that and the third thing is verification time, Which is one that we actually tend to care a lot more about and that is saying for example If I am a device that's coming online and I need to obtain the blockchain over the network and then go through and verify and ensure that all the transactions on it are valid, well Each of those is going to take some verification Time and it's interesting to look at all three of these because there is an interplay between them and there's different use cases for why we might want to care about one over the other for space obviously bandwidth and storage are a big thing You know, we basically have to carry the blockchain around with us forever Unless we come up with some fancy new thing to do with that. So as the chain gets larger with larger transactions Well, that's a problem want to minimize that as well as network bandwidth. The transactions are very large, you know those bandwidth to consider at that time.

For generation time, we're typically a little bit less concerned about that. Some low capacity devices with limited compute capability may care about that and of course an extreme case as well, you know We could you know, tune our network parameters to be, you know, a whole bunch of things We could increase ring size right now to be almost any value we want but that would greatly affect generation time as one example. So if transactions take a full minute to do well that's going to hamper usability so we'd like to minimize that if possible, but transaction generation tends to be kind of a one-off event,like I want to send funds if it takes a couple seconds Well, maybe that's not a big deal for my device. But verification time typically has to do with something that you're going to do over and over again if I'm syncing a node I have a Lot of transactions to synchronize and verify so I need the verification time for each of them to be as small as possible Like something on the order of a second is not acceptable for that We're talking about something on the order of you know, as low as possible millisecond times.

And so there's different levels of things that we can do to optimize these so I Call these different levels because some of them are very low and some of their a bit higher. So one of them is low level cryptographic operations, and we do tend to tweak these from time to time There's a lot of underlying library stuff. That one could do different kinds of hardware acceleration, and that's mostly out of the scope of this talk But we're gonna go a little bit higher and talk about other Constructions which have to do with things like range proofs and signatures and different things that we build out of those low-level cryptographic operations. And then I also talked about protocol parameters Those are things that we can kind of just change at will but that do have an impact on usability. Again, ring size is the most common example, we can change ring size whenever we want according to the protocol But there's reasons why we might want to change it as certain values or not change it to certain values.

So on this talk, I'm going to primarily be talking about constructions, but all these other ones all come into play and just an example, theres our classic chain growth graph. Yay You can see that it was doing pretty well over time I bet you can guess where ring CT was activated when we started hiding amounts and commitments. I'll give you a hint It's where it starts going up and up and up and up and I bet you can maybe tell when bullet proofs was activated which was a huge huge thing and the chain in terms of chain growth and also, Verification time is when it levels out again doesn't quite level out as much but it's still much better. So we'll be talking about these things.

So when thing we're going to look at in particular when it comes to transaction efficiency is the idea of a ring signature. And we've talked about ring signatures a lot the idea of our ring signature has evolved over time, the confidential transaction protocol that we use which hides amounts and proves balance actually does get worked into the ring signature, so we use kind of this multi-level ring signature Sounds like multi-level marketing� So multi-level ring signature that has to do with Proving key ownership. Of course one out of many keys that you're spending. It also actually helps to demonstrate transaction balance by some cool stuff involving the algebraic properties of commitments that we don't necessarily need to care about and it also helps to Ensure that the key image that we generate and remember key images are produced from the signatures You can think about it that way and they are used to check against double spending and if someone could produce a key image dishonestly, then you'd run into the risk of a double spend attempt. That would be, well it'd be successful, but fortunately as far as we know the ring signature scheme is provably correct, and we don't run into that problem.


So we're gonna particularly look at how the ring signature has evolved over time and what we're going to be doing with it. The second thing that we're gonna look at has to do with what we do with output data So ring signatures, they have to do with both inputs and output outputs. But they scale primarily based on the number of inputs and that of course means like what is our ring size and of course We have a different ring signature if we're spending multiple inputs each of which has its own ring of a true spend and decoys but in terms of output data when I'm generating outputs that are destined for you know, possibly me or possibly some other entity, there's different stuff that has to go along with the output but the two things that we need to be able to successfully communicate, very very well are both the amount and the mask. 

So the amount is pretty obvious every output has associated with it an amount in Monero that I'm going to be spending in that generated output but remember we also hide amounts and we do that in a so called Peterson commitment and a Peterson commitment basically takes the amount and it takes A piece of secret data that ideally no one else knows called the mask, we'll call it R in this case and it smushes them together algebraically in a way that you can't really go and undo very efficiently and we do a couple things with that in one case Move to the left of the diagram and I need to be able to communicate securely Those particular elements the amount V and the mask R to the recipient. The recipient needs to know what the amount is to verify that it was all correct, and the recipient also actually needs to know what the mask was in order for that recipient to be able to do things with those Funds later. Otherwise, they lose effectively lose control over them. So we need to be able to communicate that and we'll talk about why that's been made more efficient. It's why it's in gray It's my little color scheme there.

And what we also do is then we take those Those pieces of data and we put them into this so-called Peterson commitment, commit on the right and that spits up some algebraic object that we can use and what we need to do with that we end up later putting that into the ring signature in order to prove balance of a transaction without revealing what the amount is to the world but we also have to associate with it a so called range proof and the range proof is basically a way to prove in zero Knowledge that the amount is contained within some reasonable range, and the reason we do that is to prevent effectively something akin to a negative value or an overflow if we didn't do this it be possible to cleverly or maybe even not so cleverly construct a transaction that appears to balance but ends up sending absurd amounts of money and the reason with this has to do with the math that we use involving finite fields that were not terribly interested in but suffice it to say it's extremely important that we have a range proof that shows this that is also something that we've been able to highly optimized over time and the answer to that one as you may have guessed if you know about this is bullet proofs.

So let's talk about the ring signature and what we've done with that. So we currently use a scheme called MLSAG and I'm not gonna bother saying what that means It's not important here, but they effectively prove ownership of outputs that we're spending without revealing which output specifically we are spending. So the idea of constructing a group of outputs one of which is the true spend and the other which are decoys that we pull from the chain. But as I said, the type of ring signature actually does show some more though. It shows in particular that you control one output among a given set without revealing which one absent external information, we also need to prove that the key image that's used to detect double spending was generated honestly and correctly so that I can't just generate some random key image that appears to have not been spent before when I'm really double spending, and the third thing Is that the hidden transaction amounts balance and has to do with math on the Peterson commitments that we talked about before.

Now the downside to this and They'll be folks gonna be talking later in the protocol session about ways you might be able to get around this, is that they scale linearly with the ring size in both space, signing time, and verifying time. which means that if we decide to just say I don't know double the ring size, we're effectively mostly going to be doubling the size of the ring signature as well as the time It takes to generate and the time it takes to verify so the scaling on this is not great. So could we use a thousand ring members for every transaction right now? Well, you could but the scaling is going to be make it essentially unusable.
 
So what's the new hotness we have? So this is something we actually have not deployed yet But we've been talking about for a while It's a new scheme called CLSAG C standing for a compact or compressed or whatever were terrible in naming things. So this is something that was actually originally proposed by an anonymous contributor. Random run And there's actually a github issue that talks about it and it was further refined by other monero contributors Including me and including brandon as well, formalized proven correct and eventually developed into code with the collaboration of Moneromoo. The idea with CLSAG is it's basically a drop-in replacement to the existing MLSAG ring signature scheme, in effect that it does the exact same thing and shows the same things mathematically, all those things I listed about balance and ownership and key image But much much much more efficiently and the way it does that is instead of using these different output signing keys and some commitment signing keys that show all the stuff together.


Instead of including those separately in the ring signature Which increases the space and the time we can use this clever like linear combinations smushing technique to very securely smoosh it That's the technical term. We smush it. It turns that you have to smoosh it very carefully Otherwise you can do funky things with it But if you're very careful about how you smoosh things together these output keys in these commitment keys. You can effectively do a full drop-in replacement of what we had before but it's more efficient.

Now this still scales linearly So if I were to double the ring size, I would still double the CLSAG signature size. But the nice thing is overall if I compare them to the corresponding existing MLSAG, they're gonna be both smaller and faster in generation and verification time, so the scaling is the same but like Overall, they are better and in particular security is more formally proven in this than in the old one. 

So How good is it? I have a lot of plots here, red generally means bad and green generally means good So if you don't like math or numbers red is bad Green is good. So in terms of size for a current network enforced ringsize of eleven, so ten decoys and a true spender an MLSAG signature currently takes up 768 bytes. Once we switch, and again This is still being worked out when we'd want to do this. We want to get all this audited properly at this point we essentially have the size of the Ring signature So a CLSAG for the equivalent signature size is only 448 bytes.

Which is fantastic and in effect the larger the ring size gets, the closer. We actually get to dropping it by half... Someone's having a good time out there with a dropping a nice beat. So that's a signature size which is fantastic! What about the timings on those? They're also very good. They're not quite as abruptly great as the size. The size is fantastic if we can like cut the size of something in Monero in half, that's amazing. But in terms of timing, it's still pretty good so on the left I have the signing time, which is part of the Transaction generation and like I said that is typically less important to us in the stuff on the right, which is verification. So again, this is taken just from a representative test machine. It's like a 2.1 gigahertz Opteron or something. So your mileage may vary.


But for this particular case the signing time of an 11 ring existing. MLSAG signature was about 13 milliseconds so not bad. It turns out the CLSAG signing time is going to be about 11.5 milliseconds So, you know not bad and the verification time is right about 13 milliseconds for MLSAG, and in fact for CLSAG gets down to about 10 point 3 Which is about if I remember the numbers on that it's about 20% faster, which is fantastic. Now, unfortunately that speed-up only applies to CLSAG signatures and not with existing sync. But again this means that any CLSAG signatures that we generate going forward are going to be faster to verify I than if we had not deployed this code, there are some speed ups that we can deploy to MLSAG, but they're not nearly as good as this.

So that's ring signatures we have the possibility to make them much better the CLSAG code is essentially ready to go. So we'd like to get it audited and reviewed but at that time we could throw it into Monero pretty pretty easily. But let's also talk about commitments. We're all afraid of commitment, but don't be afraid of commitment, commitments good. Like I said, all amounts are represented by an algebraic structure called a Peterson commitment It happens to have a globally fixed base if you care about this But effectively what I do is I algebraically kind of add together these things in a clever elliptic curve way both the value and the mask and like I said The recipient has to know the value and the mask V&R we called them in order to reconstruct that commitment and later use it in a ring signature to be able to spend that output. But I want no one else to know what those values are. 

So previously what happened was both of the values were essentially encrypted I'm putting this in quotes It was a very very straightforward obfuscation scheme that just involved like modular addition but they were encrypted using a particular transaction shared secret that both the sender and the recipient knew, and if you care it's a hash function that's constructed in that way, and if you don't whatever it's fine. So the way that we effectively obfuscated the value is we took that value and we did some iterated hashes on this thing that only the sender and the recipient know No one else can reconstruct these and that gave like the encrypted value encrypted amount and we did a similar thing with the mask R using a slightly different iterated hash.

So the idea is that if you are neither the sender nor the recipient you cannot generate that kind of offset and you cannot reconstruct those amounts. If you are the recipient You can just do a simple subtraction and kind of undo this and then know what the value and mask are and then you can do whatever you want with your Funds, so not bad. But the new hotness for this is called being clever. What we realized was is it turns out that like this construction is a little bit wasteful in particular if they are generated randomly because remember I said this whole Peterson mask thing is just supposed to be some random value Supposed to be some randomly generated value only known to the sender in the recipient, But if it's generated randomly both the mask and this like obfuscated version of the mask They both look random and they're only known to a sender and recipient.

So in that case, why do we bother including this like specially crafted version of the encrypted mask in the transaction at all? So instead what we do is we don't actually send that anymore So instead the sender and recipient both directly compute this random looking Peterson mask thing Just from a hash function Of things that they both know and we include like a little bit of a thick salt in there to kind of shake things up And make sure that it can't be accidentally reused later. It turns out if we do this and don't have to include this data we previously did we can save a fairly small amount, but you know like a not a negligible amount of 32 bytes per output and keep in mind, of course Like most transactions include at least two outputs things like pool payouts could include up to sixteen outputs, so this scales pretty well, so nice little small savings we can get.

But it turns out this is actually still wasteful. So the new hotness is still being more clever. It turns out that the amount can't be larger than eight bytes or 64 bits Remember, we're restricting the amount range using these range proofs, which we'll talk about later but effectively what we're doing is we're still Representing this amount as a fairly large scalar value in the field that we're working with. It turns out 32 bytes like all of our Algebraic quantities are basically represented by 32 bytes so the solution here instead of doing this this kind of obfuscation and sending 32 bytes that really represents an 8 byte amount is Instead to restrict the representation of the amount to its known fixed limited value of 8 bytes and then obfuscate it using an XOR operation to save this kind of padding of 24 bytes per output and if you care That's roughly how we do it mathematically, and what the recipient can do is the recipient can basically undo this with an equivalent XOR operation and recover it into this full 32 byte scalar that you need to do math with it later on.

So if you like math, there it is if you don't like math Here's a graph remember red is old which is bad Green is good, which is new it turns out per output Previously these two values took up 64 bytes not a ton in the grand scheme of things We're talking transactions on the order of kilobytes, but still not negligible. We were able to drop that substantially down to eight It was great. I couldn't even put the label of eight inside the bar It's so low so it's pretty good a fairly small improvement, but an improvement nonetheless to transaction size. This really doesn't have anything to do with efficiency in terms of time, but it does in terms of space pretty great. The last thing I'll talk about is something we have already deployed And by the way, this thing we had back here. This was recently deployed as well So the CLSAG signatures are not deployed yet. This stuff is and the next thing range proofs also is. There was a whole big hullabaloo about this for a fantastic reason and that's because range proofs were very very large. So like I said amounts are represented as commitments That's the motto of my talk here and balance is basically proven using some algebra on these commitments You can add and subtract them in very straightforward ways like I said amounts have to be restricted to avoid this kind of overflow where you could appear to have a transaction that balances as well really pulling some funny business and paying yourself a ton of money So we have to show that the committed value with its random Peterson mask that we talked about we need to show that that value is in some fixed range And like I said that range is 64 bits So I need to prove that that value when expressed as an integer is within the range of 0 and 2 to the 64.

So the overall strategy both with bulletproofs and with the previous version is to show that I can take this value V, decompose it to 64 bits each of which is either a 0 or a 1 so it's an honest-to-goodness bit, that actually sums back up to the correct value but I don't want to actually reveal what the value of those bits is. The point is this needs to be done zero knowledge but I need to be able to show that this statement is true that I can decompose the value into honest-to-goodness bits of the appropriate length. So as an example, if my value was 13 in base 10, that's one one zero one in base two I can basically break it apart into bits. It's just how binary decomposition works and I can use that to reconstruct the value later.

The old way we did it was with this kind of bitwise ring signature and that if you remember back to that graph I had of the chain growth like we had this like gigantic spike where all of A sudden the slope of that graph just got huge. The reason was exactly because of these the previous method was a sort of bitwise, we call them borromean range proof and it actually used like a little bit separate version of a ring signature so we actually had multiple uses of ring signatures and one of them was for this. And an Effect of what you did is for each of these bits you generated effectively a separate kind of sub commitment so you had these extra 64 commitments each of which was to one of these bits and you basically constructed these commitments with masks that did some clever math when you sum them back up again and you basically built a ring signature over each of these bit commitments to show that it was either a zero or a one and it was this whole big Shebang and then to verify it you had to take this big weighted sum of these commitments you were able to show that it recovered the correct amount and also verify the ring signature so that you were Convinced that each of those bits was a zero or one. W

What sucked is that It's scaled in space and time linearly with the number of bits which was not good. So bullet proofs are the new hotness. Instead they reduce this range assertion to some clever vector inner product statements and they prove all this in zero knowledge and they like smoosh It all the way down And what's great about this has it achieves exactly the same thing on exactly the same kinds of commitments, but it scales logarithmically Which is much much slower than linearly and in particular a prover can include multiple output commitment range proofs in the exact same proof which makes things even smaller, it turns out generation and verification while they are still linear in the bit length We have some tricks we can use to speed that up and I can also verify a set of proofs in a large batch For almost no additional cost which is great because when we verify these if I'm syncing a new node We have to do this a lot. 

So what happens? Well, in the standard two output time verification time at least in this case The proving time actually increases from the old style to the new style by about, you know, 50 percent or so But the verification time that we care about drops in my case for about 95 milliseconds down to 21 Which is fantastic and this extends out for a 16 output, which is common in things like pool payouts again we increase the proving time, but the verification time drops substantially. That's the green stuff and Batch verification is even better. So if I wanted to verify in batch 128 different proofs from maybe different transactions with two outputs each the overall total cost in the old way would have been 12 seconds Which is nuts the total time here is 420 milliseconds, which means we save 97% on verification time.


It's fantastic. And the size is even better the red borromean in proofs with the number of outputs increases linearly, so it's a line whereas the bulletproofs you almost can't see how it's increasing. The scaling is fantastic. It's almost nothing. So What does this all actually mean? so put this stuff all together what do typical transactions look like then and now? 

Well Transaction size on the left an average to two transaction two ins two outs used to be about 13 kilobytes with all of these Optimizations once they're in place. We drop that down to 1.9. That's fantastic That's an 85% savings on space overall from where we were and in terms of verification time if we do this batched verification Which we absolutely can do, we end up dropping the verification time for about 121 milliseconds per transaction all the way down to about 23 and that's another 81% savings on verification time. So these all look fantastic I love graphs that go down like that. It's fantastic. But keep in mind. These are not complete scaling solutions These are very incremental, bullet proofs while you know, it's still good. It's still kind of an incremental improvement on verification They are useful but there's still just incremental improvements to basically slow the blockchain growth which still increases with the number of Transactions and outputs and we want to basically slow down the speed oh sorry,  speed up the new node sync time by lowering the verification cost as much as possible We have other options We have some that are like these sub linear fixed decoy transaction protocols like Omni ring was discussed yesterday, Lelantis is going to be discussed later today, we could try to move to something that's more of a full anonymity transaction protocol, you can actually do this with bulletproofs. but you get a very poor verification scaling you can do some of the older style snarks which as we know are toxic because they include a certain element of trust, although that you get excellent space and time scaling and compared to what we have now.

There's some newer style approaches that may be non-toxic They have better scaling than we have now, but not or a better scaling than bullet proofs. For example but not quite where we want them to be or we can try to work on things like off chain transaction layers involving things like atomic swaps and payment channels, but we don't quite have the plumbing in place for those just yet. So this is where transactions were This is where they are now Um, if you're interested, I have stuff up on github where my research ends up living in some stuff on git lab as well. So thank you for your time. I'll be glad to answer questions. Tall graphs bad small graphs good. That's the motto.

Audience member: Just a quick question on the atomic swaps. Do you see that being feasible? And do you mind it might you know when? 

Sarang: If and when right? So atomic swaps are fairly tricky you need certain kinds of plumbing in place like non-interactive refund transactions and you need to make sure that the math basically plays well and is interoperable across the different curves that might be used Monero uses a particular elliptic curve that is not common to things like Bitcoin And there's also some structures that Bitcoin has in place. I'm like being able to prove Knowledge of things using like hash preimages that our protocol doesn't support so we have some ideas in mind. There's gonna be one option That's gonna be talked about later today. So stick around, But so we have ideas It's not quite there yet as you will learn so I don't have a good answer for that um It turns out that it's very tricky Because the Monero protocol is not as expressive as things like Bitcoin and a lot of the plumbing is different It's very unsatisfactory answer but it's best I can do.


ArticMine: Got a quick question. Yeah, if I was going to keep overall verification constant from the current situation right now what's your estimate of how much we could increase the mixing by?

Sarang: Oh That's very interesting so we ran the numbers for the CLSAG signature verification only and it turns out you can maybe add like one or two to the anonymity set and still have the verification time be the same is with an 11 ring MLSAG. So I don't know a little bit Yeah, so effectively you have a ring size a 13 if you were just to say what can we do to maintain the verification time we have now on that. So it's it's not a lot because again that the savings you get in time is not as good as the savings you get in space 

Audience member: I Just stepped out for a second so sorry if I missed this but with CLSAG, it sounds like I mean like you mentioned that's pretty much ready to go. Do you foresee moving to that? No matter what limits anonymity rings look like as we learn more about them Do you envision just like going to CLSAG and then switching to something else later on if they are promising? 

Sarang: Yes I absolutely think that we should do that. And again, this is all contingent on passing both audits of the math and of the code. So everything is ready We just need to make sure that it's absolutely correct. Yes I think it's a no-brainer to go and move to CLSAG in the grand scheme of things It's a lot less work than overhauling the entire transaction protocol So we might as well do it to you know do what we can for our users now and then see what the future can hold because it's kind of uncertain. You know, we have something now. We may have something in the future too.

Audience member: Hi Sarang, right I've got a kind of a double loaded question. So refund transactions, I know that's something that Nak spend a bit time on I seem to remember. 

Sarang: Yes 

Audience member: I just wondered like how they might play into this as well.

Sarang: Um, so yeah So it's it's important to differentiate between interactive and non interactive refund transactions. The idea behind interactive refund transactions is can I efficiently encode a refund address in some safe way, into a transaction? And Nak had an idea for this there were a couple ideas for possibly how to do it but In terms of kind of the plumbing you'd need for other things like payment channels and atomic swaps. You need non-interactive refunds. Which does not require the sender to you know accurately and honestly include this information. And that's much much harder to do from a protocol level and we're actually gonna hear a talk later on about you know What it would take to actually do that. I don't know if that answers what you're getting at?

Audience member: It does my question was sort of double loaded because I also wanted to hear for me like what's your initial... What's your initial view on the recent like Omni ring and there's been a couple of papers recently that thought about basically improving our kind of ring signatures. Just wondered what work you've been up to. 

Sarang: Oh, yeah. Yeah. So a few papers came out Omni ring which you heard about, Lelantus, which you're going to hear about and there's another one called rct3 ring CT 3.0. Which was also mentioned in the Omni ring paper They're all very interesting and all slightly different approaches. The problem is like I don't see any one as being a clear absolute winner so with with the Lelantis there is an issue with a self spend problem that you need to overcome and with Omni ring the scaling is it's good. But it's a question of whether or not you know We can take advantage of some things like batching which aren't quite there yet in order to get the absolute time down a bit further and ring ct3 I need to I had some questions about batching that I haven't fully answered yet So I like them all and I can't wait for one of them to be the clear winner, but I don't think they're quite there yet So we'll do what we can right now and then work really hard toward getting something better in the future. 

Sarae: We have one more.

Sarang: So popular, or I did a terrible job. 


Audience member: Yeah, you did a great job those Lots were awesome seeing all those... 

Sarang: I love plots man 

Audience member: Yeah, seeing you you've done so well, I guess what�

Sarang: No, no we've done so well this was this is not me this Yes, a lot of people.

Audience member: Indeed. So looking far in the future. Do you imagine

Sarang: I do not look far in the future But okay,,, 

Audience member: Fair enough, the next stage. Can we do this again? Can this get that much more efficient ever? And what do you imagine could do that I mean I think you know subject to kind of like the limitations of the universe that are in place So for example, like there's certain verification asymptotic limits that you're always going to hit But if you're asking, you know, like is the state of the art gonna improve? Probably, you know before a bulletproofs came out everyone thought ah range proofs, they'll always be terrible and then all of a sudden they got fantastic. And with MLSAG we didn't see a way to improve that and then you know random runs idea came out and we saw how to compress these things. So, you know, I'm never gonna say never um, but you know, There are some kind of fundamental asymptotic limits of the universe in place, so the best we can do is kind of try to reduce some of the constants associated with them to have the same scaling, like I said MLSAG and CLSAG have the same scaling but one is just absolutely better than the other for our use case So hope so.

Surae: Alright everybody lets give Sarang another hand!