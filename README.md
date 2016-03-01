# Python-Style-Guide
List of things I found helpful when developing in Python.

## Pickle Files
* All pickle files must be of type `dict` and have the following 2 keys: "properties" and "data".
* The "data" keys contain the object intended to be pickled.
* The "properties" keys contain metadata about the pickled data such as "date created", etc.
* The "properties" keys will *at least* be used to display logging information regarding the pickle file that has been loaded. More intricate uses will involve code dynamically checking the properties to determine usability.
* Often in scientific computing, pickle files are used to circumvent time-consuming calculations by pickling results from the first execution of a portion of code and subsequently thereafter, loading that pickle file instead of running the code again. The above ensures that the developer is aware of the state of the pickle file she/he is loading.
* Ex: Jenny pickles the results of a 2-hour subroutine in her code and continues development. However, she changes parts of the code that affect the results of the 2-hour pickle file but is unaware and continues seeing the same results when running the code because it's loading the same old pickle file. Looking at the diagnostic, she realizes the pickle file is now outdated and re-runs the 2-hour subroutine.

## Classes
* All class definitions shall contain a set attributes (*instance* or *class*) and it shall be static. No attributes should be added dynamically.
* Python allows the creation of new class attributes via assignment i.e.
```
class Spam:
   def __init__(self):
       self.breakfast = "Eggs"
       
s = Spam
s.brakefast = 'Pastrami'  # 'brakefast' is now a new instance attribute.
s.brakefast
>> Pastrami
```
* If an attribute should exist, it should already be known at the time of class definition.
* Ex: Benny accidently adds a new instance attribute to a class by mistakenly assigning a nonexistent attribute. That attribute is never used because the intended attribute was never updated.
