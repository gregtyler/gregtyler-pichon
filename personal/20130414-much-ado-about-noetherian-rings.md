Published: 2013-04-14T12:59:15.000Z
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: During a lecture series last year, I wanted to spice up the hour-long sessions we had. I spent a lot of time drawing, and tried writing notes in different languages. But during one such lecture I wrote my notes like a play, in rhyming couplets. After some vague interest from others, and for the sake of posterity, I thought I'd put them up here.

Much Ado about Noetherian Rings

During a lecture series last year, I wanted to spice up the hour-long sessions we had. I spent a lot of time drawing, and tried writing notes in different languages. But during one such lecture I wrote my notes like a play, in rhyming couplets. After some vague interest from others, and for the sake of posterity, I thought I'd put them up here.   

It's not a masterpiece. The meter is all over the place, there are a lot of half-rhymes and I'm not certain the maths holds up. But considering that I wrote it in fifty minutes with no preparation, I'm really proud of it. I was tempted to clean up some of the off-bits, but I've chosen to leave it totally unedited. This is very much the "without makeup" version.   

So please enjoy what I've since named **Much Ado about Noetherian Rings**. A play in one Act.   

(Alternative titles: Measure for Zero Measure, The Comedy of Mathematical Misconceptions, The Taming of the Discontinuous Functions)   


## Dramatis personæ


ANTONIO, a merchant   
GAIUS, his brother   
HERMIUS, a nobleman   
SERAFINA, a gentlewoman   


## Prologue


From the next hour we hope you yield,   
Indiscriminate knowledge of the finite field.   
And cyclic codes we hope you know,   
For their properties we're soon to show.   


## Scene 1: A port of Florence


_(Enter ANTONIO and GAIUS)_   

Antonio: Recall, brother, the characteristic of a field.   

Gaius: The smallest positive integer such that as many ones that are summed make nought?   

Antonio: The exact same. Remember thee that it is prime or infinite?   

Gaius: Alas, I missed such a fact.   

Antonio: Now form a field of sums of one, up until they add to none.   
The suppose that n is p times q, both primes I should be telling you.   

Gaius: Then a sum of n is a sum of primes, but these be nought in any time!   
Hence we find a contradiction, and conclude with some conviction.   
That n cannot be p times q, and only if it's prime will do!   

Antonio: Now theorise that in a field, then in it thy fate is sealed.   
There exists a number pn, with p a prime, the other in ℕ.   
I shan't prove this in great detail, but an outline surely cannot fail.   
Note ℤp is a linear subspace, and that it works with an F-basis.   
So any a in F can be written unique, amongst the basis ℤp of which we speak.   

Gaius: I'm afraid brother that I don't get it!   

Antonio: Perhaps t'would help to see it writ.   
Here I show you an example, with f(x) an irreducible polynomial,   
which has as n its degree, and coefficients in ℤp.   
Now let me fall and show to you, the following is certainly true.   
The answer, it is sealed, this ℤp[x] / f(x)ℤp[x] is a field.   

See, brother, that the powers of x can form a basis of cosets.   
[1], [x], [x2], [xn-1] certainly form a linear space on,   
ℤp, our set of coefficients, and to show they span you must be proficient.   
Each element it is in the sum (![sum^n_{i=0}](/sumton.gif) αi[xi], αi ∈ ℤ), so the cosets span everyone.   
Since each αi has options p, there are pn choices we can see.   
Now find a field with elements 9, and waste not any of our time.   

_(Enter HERMIUS, a nobleman)_   

Hermius: What trivial games you merchants play, sitting by the docks all day.   
With 9 elements, take p as 3, and n as 2 so we can see   
that ℤ3[x] / f(x)ℤ3[x] is irreducible, in all f(x) of degree 2.   

Gaius: And we know a polynomial with degree ≤ 3 only displays irreducibility,   
if it has no factor in F, and hence no root but alone, bereft.   

Hermius: Indeed, so after all this fun, take f(x) to be x2 1\.   

Antonio: But can you form me one with eight?   

Gaius: Nay in time, unless we have 'til late.   

Hermius: Foolish boy, this is easy, take p as 2 and n as 3.   
Now form the field shown here (ℤ3[x] / f(x)ℤ3[x]) and let f(x) appear.   
This f(x) is of degree 3 and in ℤ2[x] shows irreducibility.   
Try f(x)=x3 x 1, and see that f(x)=0 gives none.   
In integers of course!   

_(Exit HERMIUS and enter SERAFINA)_   

Serafina: Merchant men, if you'll hear me, let me provide to you a little theory.   
That if n is a number we call natural, then an isomorphism will certainly fall.   
Upon ℤ/nℤ and ℤn where ℤn has modulus addition.   
And that if F in K are both fields, with f(x) irreducible in F[X]'s shield,   
take α in K so that it evaluated gives none, then note again an isomorphism.   
Here of F[x]/f(x)F[x] and the F[α] polynomial set.   

Antonio: May we call F[α] a simple extension?   

Serafina: Yes, of F. I forgot to mention.   
I bid you proof, that much I owe, and with the 1st isomorphism theorem I shall show.   
Form g from F[x] to F[α], and by ker(g) we can solve her.   
Say F were ℝ and K be ℂ, take α=√1 instantly,   
Then ℝ[x] / (x2 1)ℝ[x] to ℂ they will be isomorphics.   

Gaius: Such odd remarks you make today, of field extensions you continue to say.   
But let us return to the matter of codes, and see that cyclic ones can be showed.   
Take a word in a code and if it may be, that that at the end at the start we may see,   
If this be true for any code word, then to a cyclic code we have referred.   
Note too that there are more criteria, a cyclic code it must be linear!   

Antonio: Tell me more of cyclic shift, a concept I've heard is of some thrift.   

Gaius: It's much what it sounds like brother, a smooth connection as that between lovers.   
Take the last digit of a word and add it to the start, a cyclic shift has occurred in such a lover's heart.   

Serafina: Could a polynomial be moved by such a lover?   

Gaius: Aye, my lady, and we'd discover   
the coefficients are what make the code, so 1 x2 x4 is 10101 showed.   
Then a=10101 is a ring, Rn (=F[x]/(xn-1)F[x]) is the notation we bring.   

Serafina: What really can we see from this?   

Gaius: That x*a(x) is a cyclic shift.   

Serafina: You speak with such determination, could you show some explanation?   

Gaius: Alas, time falls but trust my lady, I believe you can see it may be.   

_(A priest gives Serafina a potion, making her appear dead. Gaius flees, wrought with grief, and Serafina awakes cold and alone.)_   


Image: Edwin Landseer - Scene from A Midsummer Night's Dream

[1]: https://gregtyler.co.uk/files/2013/04/sumton.gif
