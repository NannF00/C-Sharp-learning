The principle here is do not ask for more than you need.

# IEnumerable<T> , IList<T> , List<T>

IEnumerable<T> communicates "I need to get the elements of this sequence from beginning to end". 

IList<T> communicates "I need to get and set the elements of this sequence in arbitrary order". 

List<T> communicates "I need to get and set the elements of this sequence in arbitrary order and I only accept lists; I do not accept arrays."

By asking for more than you need, you

(1) make the caller do unnecessary work to satisfy your unnecessary demands, and

(2) communicate falsehoods to the reader. 

Ask only for what you're going to use. That way if the caller has a sequence, they don't need to call ToList on it to satisfy your demand.

# Return type:

Same principle as before, reversed. Offer the bare minimum that your caller requires. 

If the caller only requires the ability to enumerate the sequence, only give them an IEnumerable<T>.

