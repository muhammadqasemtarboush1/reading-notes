# Class 23

Live link: [Hash Tables](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2023/)

## Create a vocabulary/definition list

* Hash:
  * A hash is the result of some algorithm taking an incoming string and converting it int
  o a value that could be used for either security or some other purpose. In the case of a 
  hashtable, it is used to determine the index of the array.
  
* Buckets:
  * A bucket is what is contained in each index of the array of the hashtable. 
  Each index is a bucket. An index could potentially contain multiple key/value pairs if a 
  collision occurs.
* Collisions:
  * A collision is what happens when more than one key gets hashed to the same location 
  of the hashtable.
* Hashtables:
  * data structure that utilize key value pairs. This means every Node or Bucket has both a
  key, and a value.
* Hashing:
  * A hash code turns a key into an integer. It’s very important that hash
  codes are deterministic: their output is determined only by their input. Hash codes
  should never have randomness to them. The same key should always produce the same hash
  code.
* Recognize: 
  * calculating load factors and choosing the optimal number of buckets, and determining 
  the best hash functions is not within the scope of this class. 
  
### Internal Methods
* Add()
  * adding a new key/value pair to a hashtable
* Find()
  * The Find takes in a key, gets the Hash, and goes to the index location specified. 
  Once at the index location is found in the array, it is then the responsibility of
  the algorithm the iterate through the bucket and see if the key exists and return the
  value.
* Contains()
  * The Contains method will accept a key, and return a bool on if that key exists inside 
  the hashtable.
* GetHash()
  * The GetHash will accept a key as a string, conduct the hash, and then return the
  index of the array where the key/value should be placed.
  

--- 
## Sources:
[Basics of Hash Tables](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)
[Hashtables](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)
[Introduction to Hash Tables and Dictionaries](https://www.youtube.com/watch?v=sfWyugl4JWA&ab_channel=CSDojo)

---













