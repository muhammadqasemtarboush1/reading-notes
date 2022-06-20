# Class 09

## Dunder (Magic, Special) Methods

### What Are Dunder Methods?

n Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize
because they start and end with double underscores, for example __init__ or __str__.

“dunder methods”, a short form of “double under.”

Magic Methods :by using this terminology can make them seem more complicated than they really are—at the end of the day there’s nothing “magical” about them.

Dunder methods let you emulate the behavior of built-in types.

### Special Methods and the Python Data Model

This elegant design is known as the Python data model and
lets developers tap into rich language features like sequences, iteration, operator overloading, attribute access, etc.

### Enriching a Simple Account Class

* #### Object Initialization: __init__

  *
  *
  * ```python
    class Account:
      def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []
    ```

  * The constructor takes care of setting up the object.

* #### Object Representation: __str__, __repr__

  * provide a string representation of your object for the
  consumer of your class (a bit like API documentation.)
  * There are two ways to do this using dunder methods:
    * __repr__ : The “official” string representation of an object.
    This is how you would make an object of the class. The goal of
    __repr__ is to be unambiguous.
    * ___str___ : The “informal” or nicely printable string representation of an object. This is for the enduser.
  * example:

  ```python
    class Account:
      ... (see above)
      def __repr__(self):
          return 'Account({!r}, {!r})'.format(self.owner, self.amount)

      def __str__(self):
          return 'Account of {} with starting amount: {}'.format(
              self.owner, self.amount)
    ```

* #### Dunder __class__.__name__

  * we can use it to get name for the class

* #### Iteration: __len__, __getitem__, __reversed__

  * In order to iterate over our account object I need to add some transactions
  *
    *
    * ```python
      def add_transaction(self, amount):
        if not isinstance(amount, int):
            raise ValueError('please use int for amount')
        self._transactions.append(amount)  
       ```

* #### Operator Overloading for Comparing Accounts: __eq__, __lt__
  *
    *
    * ```python
      from functools import total_ordering
       @total_ordering
       class Account:
        def __eq__(self, other):
          return self.balance == other.balance
        def __lt__(self, other):
          return self.balance < other.balance  
      ```

* #### Operator Overloading for Merging Accounts: __add__

  * give us the ability to merge two objects together
  * example:

    ```python
      def __add__(self, other):
        owner = '{}&{}'.format(self.owner, other.owner)
        start_amount = self.amount + other.amount
        acc = Account(owner, start_amount)
        for t in list(self) + list(other):
            acc.add_transaction(t)
            return acc         
       ```

  * Callable Python Objects: __call__
    * You can make an object callable like a regular function by adding the __call__ dunder method.
    * example:

    ```python
    class Account:
    # ... (see above)

    def __call__(self):
        print('Start amount: {}'.format(self.amount))
        print('Transactions: ')
        for transaction in self:
            print(transaction)
        print('\nBalance: {}'.format(self.balance))
    ```

  * Context Manager Support and the With Statement: __enter__, __exit__
    * A context manager is a simple “protocol” (or interface) that your object needs to follow so it
    can be used with the with statement. Basically all you need to do is add __enter__ and __exit__ methods
    to an object if you want it to function as a context manager.
    * example:

    ```python
    class Account:
    # ... (see above)

    def __enter__(self):
        print('ENTER WITH: Making backup of transactions for rollback')
        self._copy_transactions = list(self._transactions)
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('EXIT WITH:', end=' ')
        if exc_type:
            self._transactions = self._copy_transactions
            print('Rolling back to previous transactions')
            print('Transaction resulted in {} ({})'.format(
                exc_type.__name__, exc_val))
        else:
            print('Transaction OK') 
    
    ```
  
## Notes

* You can see Python’s data model as a powerful API you can
interface with by implementing one or more dunder methods.

### [Source](https://dbader.org/blog/python-dunder-methods)

## Tutorial: Basic Statistics in Python — Probability

### What is probability?

seeks to answer the question, “What is the chance of an event happening?” An event is some outcome of interest

### From statistics to probability

Thus, given enough data, statistics enables us to calculate
probabilities using real-world observations. Probability
provides the theory, while statistics provides the tools
to test that theory using data. The descriptive statistics,
specifically mean and standard deviation, become the proxies
for the theoretical.

### Revisiting the normal

The normal distribution is significant to probability and statistics thanks to two factors:
the Central Limit Theorem and the Three Sigma Rule.

#### Central Limit Theorem

the Central Limit Theorem suggests that we can hone in on the theoretical ideal given by probability,
even when we don’t know the true probability.
Central Limit Theorem lets us know that the average of many trials means
will approach the true mean, the Three Sigma Rule will tell us how much the data will be spread out around this mean.

#### Three Sigma Rule

The Three Sigma rule, also known as the empirical rule or 68-95-99.7 rule, is an expression of how many of our observations
fall within a certain distance of the mean.

### Z-score

Is a simple calculation that answers the question, “Given a data point, how many standard deviations is it away
 from the mean?” The equation below is the Z-score equation.

### [Source](https://www.dataquest.io/blog/basic-statistics-in-python-probability/)

## statistics — Mathematical statistics functions¶

### Averages and measures of central location¶

These functions calculate an average or typical value from a population or sample.

* mean()
  * Arithmetic mean (“average”) of data.
* fmean()
  * Fast, floating point arithmetic mean.
* geometric_mean()
  * Geometric mean of data.
* harmonic_mean()
  * Harmonic mean of data.
* median()
  * Median (middle value) of data.
* median_low()
  * Low median of data.
* median_high()
  * High median of data.
* median_grouped()
  * Median, or 50th percentile, of grouped data.
* mode()
  * Single mode (most common value) of discrete or nominal data.
* multimode()
  * List of modes (most common values) of discrete or nominal data.
* quantiles()
  * Divide data into intervals with equal probability.

### Measures of spread¶

These functions calculate a measure of how much the population or sample tends to deviate from the typical or average values.

| pstdev()    | Population standard deviation of data. |
|-------------|----------------------------------------|
| pvariance() | Population variance of data.           |
| stdev()     | Sample standard deviation of data.     |
| variance()  | Sample variance of data.               |

### Statistics for relations between two inputs¶

These functions calculate statistics regarding relations between two inputs.

| covariance()        | Sample covariance for two variables.                 |
|---------------------|------------------------------------------------------|
| correlation()       | Pearson’s correlation coefficient for two variables. |
| linear_regression() | Slope and intercept for simple linear regression.    |

## Things I want to know more about

* Statistics how to use it in practical way and deal with it in real world projects
