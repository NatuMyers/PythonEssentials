<div class="article__body" data-reactid="40">

## [](#introduction)Introduction

Looking for a Python job? Chances are you will need to prove that you know how to work with Python. Here are a couple of questions that cover a wide base of skills associated with Python. Focus is placed on the language itself, and not any particular package or framework. Each question will be linked to a suitable tutorial if there is one. Some questions will wrap up multiple topics.

I haven't actually been given an interview test quite as hard as this one, if you can get to the answers comfortably then go get yourself a job.

## [](#what-this-tutorial-is-not)What This Tutorial Is Not

This tutorial does not aim to cover every available workplace culture - different employers will ask you different questions in different ways; they will follow different conventions; they will value different things. They will test you in different ways. Some employers will sit you down in from of a computer and ask you to solve simple problems; some will stand you up in front of a white board and do similar; some will give you a take home test to solve; some will just have a conversation with you.

The best test for a programmer is actually programming. This is a difficult thing to test with a simple tutorial. So for bonus points make sure that you can actually use the functionality demonstrated in the questions. If you actually understand how to get to the answers well enough that you can actually make use of the demonstrated concepts then you are winning.

Similarly, the best test for a software engineer is actually engineering. This tutorial is about Python as a language. Being able to design efficient, effective, maintainable class hierarchies for solving niche problems is great and wonderful and a skill set worth pursuing but well beyond the scope of this text.

Another thing this tutorial is not is PEP8 compliant. This is intentional as, as mentioned before, different employers will follow different conventions. You will need to adapt to fit the culture of the workplace. Because practicality beats purity.

Another thing this tutorial isn't is concise. I don't want to just throw questions and answers at you and hope something sticks. I want you to get it, or at least get it well enough that you are in a position to look for further explanations yourself for any problem topics.

* * *

_Want to ace your technical interview? Schedule a [Technical Interview Practice Session](https://www.codementor.io/gigs/interview-prep-services) with an expert now!_

* * *

## [](#question-1)Question 1

What is Python really? You can (and are encouraged) make comparisons to other technologies in your answer

### [](#answer)Answer

Here are a few key points:

*   Python is an interpreted language. That means that, unlike languages like _C_ and its variants, Python does not need to be compiled before it is run. Other interpreted languages include _PHP_ and _Ruby_.

*   Python is dynamically typed, this means that you don't need to state the types of variables when you declare them or anything like that. You can do things like `x=111` and then `x="I'm a string"` without error

*   Python is well suited to object orientated programming in that it allows the definition of classes along with composition and inheritance. Python does not have access specifiers (like C++'s `public`, `private`), the justification for this point is given as "we are all adults here"

*   In Python, functions are first-class objects. This means that they can be assigned to variables, returned from other functions and passed into functions. Classes are also first class objects

*   Writing Python code is quick but running it is often slower than compiled languages. Fortunately， Python allows the inclusion of C based extensions so bottlenecks can be optimised away and often are. The `numpy` package is a good example of this, it's really quite quick because a lot of the number crunching it does isn't actually done by Python

*   Python finds use in many spheres - web applications, automation, scientific modelling, big data applications and many more. It's also often used as "glue" code to get other languages and components to play nice.

*   [Python makes difficult things easy](https://xkcd.com/353/) so programmers can focus on overriding algorithms and structures rather than nitty-gritty low level details.

### [](#why-this-matters)Why This Matters:

If you are applying for a Python position, you should know what it is and why it is so gosh-darn cool. And why it isn't o.O

## [](#question-2)Question 2

Fill in the missing code:

```
def print_directory_contents(sPath):
    """
    This function takes the name of a directory
    and prints out the paths files within that
    directory as well as any files contained in
    contained directories.

    This function is similar to os.walk. Please don't
    use os.walk in your answer. We are interested in your
    ability to work with nested structures.
    """
    fill_this_in

```

### [](#answer-2)Answer

```
def print_directory_contents(sPath):
    import os                                       
    for sChild in os.listdir(sPath):                
        sChildPath = os.path.join(sPath,sChild)
        if os.path.isdir(sChildPath):
            print_directory_contents(sChildPath)
        else:
            print(sChildPath)

```

### [](#pay-special-attention)Pay Special Attention

*   Be consistent with your naming conventions. If there is a naming convention evident in any sample code, stick to it. Even if it is not the naming convention you usually use
*   Recursive functions need to recurse _and_ terminate. Make sure you understand how this happens so that you avoid bottomless callstacks
*   We use the `os` module for interacting with the operating system in a way that is cross platform. You could say `sChildPath = sPath + '/' + sChild` but that wouldn't work on windows
*   Familiarity with base packages is really worthwhile, but don't break your head trying to memorize everything, Google is your friend in the workplace!
*   Ask questions if you don't understand what the code is supposed to do
*   KISS! Keep it Simple, Stupid!

### [](#why-this-matters-2)Why This Matters:

*   Displays knowledge of basic operating system interaction stuff
*   Recursion is hella useful

## [](#question-3)Question 3

Looking at the below code, write down the final values of A0, A1, ...An.

```
A0 = dict(zip(('a','b','c','d','e'),(1,2,3,4,5)))
A1 = range(10)
A2 = sorted([i for i in A1 if i in A0])
A3 = sorted([A0[s] for s in A0])
A4 = [i for i in A1 if i in A3]
A5 = {i:i*i for i in A1}
A6 = [[i,i*i] for i in A1]

```

If you dont know what `zip` is don't stress out. No sane employer will expect you to memorize the standard library. Here is the output of `help(zip)`.

```
zip(...)
    zip(seq1 [, seq2 [...]]) -> [(seq1[0], seq2[0] ...), (...)]

    Return a list of tuples, where each tuple contains the i-th element
    from each of the argument sequences.  The returned list is truncated
    in length to the length of the shortest argument sequence.

```

If that doesn't make sense then take a few minutes to figure it out however you choose to.

### [](#answer-3)Answer

```
A0 = {'a': 1, 'c': 3, 'b': 2, 'e': 5, 'd': 4}  # the order may vary
A1 = range(0, 10) # or [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] in python 2
A2 = []
A3 = [1, 2, 3, 4, 5]
A4 = [1, 2, 3, 4, 5]
A5 = {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
A6 = [[0, 0], [1, 1], [2, 4], [3, 9], [4, 16], [5, 25], [6, 36], [7, 49], [8, 64], [9, 81]]

```

### [](#why-this-matters-3)Why This Matters

1.  List comprehension is a wonderful time saver and a big stumbling block for a lot of people
2.  If you can read them, you can probably write them down
3.  Some of this code was made to be deliberately weird. You may need to work with some weird people

<em style="font-family: georgia"><a href="https://www.codementor.io/gig/un54k1r0/level-up-your-python?utm_source=tutorial&utm_medium=article&utm_term=gigs&utm_content=tutorial_python&utm_campaign=cm_internal_ad">Get Your Python Code Reviewed</a></em>

## [](#question-4)Question 4

Python and multi-threading. Is it a good idea? List some ways to get some Python code to run in a parallel way.

### [](#answer-4)Answer

Python doesn't allow multi-threading in the truest sense of the word. It has a [multi-threading package](https://docs.python.org/2/library/threading.html) but if you want to multi-thread to speed your code up, then it's usually not a good idea to use it. Python has a construct called the Global Interpreter Lock (GIL). The GIL makes sure that only one of your 'threads' can execute at any one time. A thread acquires the GIL, does a little work, then passes the GIL onto the next thread. This happens very quickly so to the human eye it may seem like your threads are executing in parallel, but they are really just taking turns using the same CPU core. All this GIL passing adds overhead to execution. This means that if you want to make your code run faster then using the threading package often isn't a good idea.

There are reasons to use Python's threading package. If you want to run some things simultaneously, and efficiency is not a concern, then it's totally fine and convenient. Or if you are running code that needs to wait for something (like some IO) then it could make a lot of sense. But the threading library won't let you use extra CPU cores.

Multi-threading can be outsourced to the operating system (by doing multi-processing), some external application that calls your Python code (eg, Spark or Hadoop), or some code that your Python code calls (eg: you could have your Python code call a C function that does the expensive multi-threaded stuff).

### [](#why-this-matters-4)Why This Matters

Because the GIL is an A-hole. Lots of people spend a lot of time trying to find bottlenecks in their fancy Python multi-threaded code before they learn what the GIL is.

## [](#question-5)Question 5

How do you keep track of different versions of your code?

### [](#answer-5)Answer:

Version control! At this point, you should act excited and tell them how you even use [Git](https://git-scm.com/) (or whatever is your favorite) to keep track of correspondence with Granny. Git is my preferred version control system, but there are others, for example subversion.

### [](#why-this-matters-5)Why This Matters:

Because code without version control is like coffee without a cup. Sometimes we need to write once-off throw away scripts and that's ok, but if you are dealing with any significant amount of code, a version control system will be a benefit. Version Control helps with keeping track of who made what change to the code base; finding out when bugs were introduced to the code; keeping track of versions and releases of your software; distributing the source code amongst team members; deployment and certain automations. It allows you to roll your code back to before you broke it which is great on its own. Lots of stuff. It's just great.

## [](#question-6)Question 6

What does this code output:

```
def f(x,l=[]):
    for i in range(x):
        l.append(i*i)
    print(l)

f(2)
f(3,[3,2,1])
f(3)

```

### [](#answer-6)Answer

```
[0, 1]
[3, 2, 1, 0, 1, 4]
[0, 1, 0, 1, 4]

```

### [](#hu)Hu?

The first function call should be fairly obvious, the loop appends 0 and then 1 to the empty list, `l`. `l` is a name for a variable that points to a list stored in memory. The second call starts off by creating a new list in a new block of memory. `l` then refers to this new list. It then appends 0, 1 and 4 to this new list. So that's great. The third function call is the weird one. It uses the original list stored in the original memory block. That is why it starts off with 0 and 1.

Try this out if you don't understand:

```
l_mem = []

l = l_mem           # the first call
for i in range(2):
    l.append(i*i)

print(l)            # [0, 1]

l = [3,2,1]         # the second call
for i in range(3):
    l.append(i*i)

print(l)            # [3, 2, 1, 0, 1, 4]

l = l_mem           # the third call
for i in range(3):
    l.append(i*i)

print(l)            # [0, 1, 0, 1, 4]

```

## [](#question-7)Question 7

What is monkey patching and is it ever a good idea?

### [](#answer-7)Answer

Monkey patching is changing the behaviour of a function or object after it has already been defined. For example:

```
import datetime
datetime.datetime.now = lambda: datetime.datetime(2012, 12, 12)

```

Most of the time it's a pretty terrible idea - it is usually best if things act in a well-defined way. One reason to monkey patch would be in testing. The [mock](https://pypi.python.org/pypi/mock) package is very useful to this end.

### [](#why-this-matters-6)Why This Matters

It shows that you understand a bit about methodologies in unit testing. Your mention of monkey avoidance will show that you aren't one of those coders who favor fancy code over maintainable code (they are out there, and they suck to work with). Remember the principle of KISS? And it shows that you know a little bit about how Python works on a lower level, how functions are actually stored and called and suchlike.

_PS_: it's really worth reading a little bit about [mock](https://pypi.python.org/pypi/mock) if you haven't yet. It's pretty useful.

## [](#question-8)Question 8

What does this stuff mean: `*args`, `**kwargs`? And why would we use it?

### [](#answer-8)Answer

Use `*args` when we aren't sure how many arguments are going to be passed to a function, or if we want to pass a stored list or tuple of arguments to a function. `**kwargs` is used when we dont know how many keyword arguments will be passed to a function, or it can be used to pass the values of a dictionary as keyword arguments. The identifiers `args` and `kwargs` are a convention, you could also use `*bob` and `**billy` but that would not be wise.

Here is a little illustration:

```

def f(*args,**kwargs): print(args, kwargs)

l = [1,2,3]
t = (4,5,6)
d = {'a':7,'b':8,'c':9}

f()
f(1,2,3)                    # (1, 2, 3) {}
f(1,2,3,"groovy")           # (1, 2, 3, 'groovy') {}
f(a=1,b=2,c=3)              # () {'a': 1, 'c': 3, 'b': 2}
f(a=1,b=2,c=3,zzz="hi")     # () {'a': 1, 'c': 3, 'b': 2, 'zzz': 'hi'}
f(1,2,3,a=1,b=2,c=3)        # (1, 2, 3) {'a': 1, 'c': 3, 'b': 2}

f(*l,**d)                   # (1, 2, 3) {'a': 7, 'c': 9, 'b': 8}
f(*t,**d)                   # (4, 5, 6) {'a': 7, 'c': 9, 'b': 8}
f(1,2,*t)                   # (1, 2, 4, 5, 6) {}
f(q="winning",**d)          # () {'a': 7, 'q': 'winning', 'c': 9, 'b': 8}
f(1,2,*t,q="winning",**d)   # (1, 2, 4, 5, 6) {'a': 7, 'q': 'winning', 'c': 9, 'b': 8}

def f2(arg1,arg2,*args,**kwargs): print(arg1,arg2, args, kwargs)

f2(1,2,3)                       # 1 2 (3,) {}
f2(1,2,3,"groovy")              # 1 2 (3, 'groovy') {}
f2(arg1=1,arg2=2,c=3)           # 1 2 () {'c': 3}
f2(arg1=1,arg2=2,c=3,zzz="hi")  # 1 2 () {'c': 3, 'zzz': 'hi'}
f2(1,2,3,a=1,b=2,c=3)           # 1 2 (3,) {'a': 1, 'c': 3, 'b': 2}

f2(*l,**d)                   # 1 2 (3,) {'a': 7, 'c': 9, 'b': 8}
f2(*t,**d)                   # 4 5 (6,) {'a': 7, 'c': 9, 'b': 8}
f2(1,2,*t)                   # 1 2 (4, 5, 6) {}
f2(1,1,q="winning",**d)      # 1 1 () {'a': 7, 'q': 'winning', 'c': 9, 'b': 8}
f2(1,2,*t,q="winning",**d)   # 1 2 (4, 5, 6) {'a': 7, 'q': 'winning', 'c': 9, 'b': 8}

```

### [](#why-care)Why Care?

Sometimes we will need to pass an unknown number of arguments or keyword arguments into a function. Sometimes we will want to store arguments or keyword arguments for later use. Sometimes it's just a time saver.

## [](#question-9)Question 9

What do these mean to you: `@classmethod`, `@staticmethod`, `@property`?

### [](#answer-background-knowledge)Answer Background Knowledge

These are decorators. A decorator is a special kind of function that either takes a function and returns a function, or takes a class and returns a class. The `@` symbol is just syntactic sugar that allows you to decorate something in a way that's easy to read.

```
@my_decorator
def my_func(stuff):
    do_things

```

Is equivalent to

```
def my_func(stuff):
    do_things

my_func = my_decorator(my_func)

```

You can find a tutorial on how decorators in general work [here](https://www.codementor.io/python/tutorial/advanced-use-python-decorators-class-function).

### [](#actual-answer)Actual Answer

The decorators `@classmethod`, `@staticmethod` and `@property` are used on functions defined within classes. Here is how they behave:

```
class MyClass(object):
    def __init__(self):
        self._some_property = "properties are nice"
        self._some_other_property = "VERY nice"
    def normal_method(*args,**kwargs):
        print("calling normal_method({0},{1})".format(args,kwargs))
    @classmethod
    def class_method(*args,**kwargs):
        print("calling class_method({0},{1})".format(args,kwargs))
    @staticmethod
    def static_method(*args,**kwargs):
        print("calling static_method({0},{1})".format(args,kwargs))
    @property
    def some_property(self,*args,**kwargs):
        print("calling some_property getter({0},{1},{2})".format(self,args,kwargs))
        return self._some_property
    @some_property.setter
    def some_property(self,*args,**kwargs):
        print("calling some_property setter({0},{1},{2})".format(self,args,kwargs))
        self._some_property = args[0]
    @property
    def some_other_property(self,*args,**kwargs):
        print("calling some_other_property getter({0},{1},{2})".format(self,args,kwargs))
        return self._some_other_property

o = MyClass()
# undecorated methods work like normal, they get the current instance (self) as the first argument

o.normal_method
# <bound method MyClass.normal_method of <__main__.MyClass instance at 0x7fdd2537ea28>>

o.normal_method()
# normal_method((<__main__.MyClass instance at 0x7fdd2537ea28>,),{})

o.normal_method(1,2,x=3,y=4)
# normal_method((<__main__.MyClass instance at 0x7fdd2537ea28>, 1, 2),{'y': 4, 'x': 3})

# class methods always get the class as the first argument

o.class_method
# <bound method classobj.class_method of <class __main__.MyClass at 0x7fdd2536a390>>

o.class_method()
# class_method((<class __main__.MyClass at 0x7fdd2536a390>,),{})

o.class_method(1,2,x=3,y=4)
# class_method((<class __main__.MyClass at 0x7fdd2536a390>, 1, 2),{'y': 4, 'x': 3})

# static methods have no arguments except the ones you pass in when you call them

o.static_method
# <function static_method at 0x7fdd25375848>

o.static_method()
# static_method((),{})

o.static_method(1,2,x=3,y=4)
# static_method((1, 2),{'y': 4, 'x': 3})

# properties are a way of implementing getters and setters. It's an error to explicitly call them
# "read only" attributes can be specified by creating a getter without a setter (as in some_other_property)

o.some_property
# calling some_property getter(<__main__.MyClass instance at 0x7fb2b70877e8>,(),{})
# 'properties are nice'

o.some_property()
# calling some_property getter(<__main__.MyClass instance at 0x7fb2b70877e8>,(),{})
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# TypeError: 'str' object is not callable

o.some_other_property
# calling some_other_property getter(<__main__.MyClass instance at 0x7fb2b70877e8>,(),{})
# 'VERY nice'

# o.some_other_property()
# calling some_other_property getter(<__main__.MyClass instance at 0x7fb2b70877e8>,(),{})
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# TypeError: 'str' object is not callable

o.some_property = "groovy"
# calling some_property setter(<__main__.MyClass object at 0x7fb2b7077890>,('groovy',),{})

o.some_property
# calling some_property getter(<__main__.MyClass object at 0x7fb2b7077890>,(),{})
# 'groovy'

o.some_other_property = "very groovy"
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# AttributeError: can't set attribute

o.some_other_property
# calling some_other_property getter(<__main__.MyClass object at 0x7fb2b7077890>,(),{})
# 'VERY nice'

```

## [](#question-10)Question 10

Consider the following code, what will it output?

```
class A(object):
    def go(self):
        print("go A go!")
    def stop(self):
        print("stop A stop!")
    def pause(self):
        raise Exception("Not Implemented")

class B(A):
    def go(self):
        super(B, self).go()
        print("go B go!")

class C(A):
    def go(self):
        super(C, self).go()
        print("go C go!")
    def stop(self):
        super(C, self).stop()
        print("stop C stop!")

class D(B,C):
    def go(self):
        super(D, self).go()
        print("go D go!")
    def stop(self):
        super(D, self).stop()
        print("stop D stop!")
    def pause(self):
        print("wait D wait!")

class E(B,C): pass

a = A()
b = B()
c = C()
d = D()
e = E()

# specify output from here onwards

a.go()
b.go()
c.go()
d.go()
e.go()

a.stop()
b.stop()
c.stop()
d.stop()
e.stop()

a.pause()
b.pause()
c.pause()
d.pause()
e.pause()

```

### [](#answer-9)Answer

The output is specified in the comments in the segment below:

```
a.go()
# go A go!

b.go()
# go A go!
# go B go!

c.go()
# go A go!
# go C go!

d.go()
# go A go!
# go C go!
# go B go!
# go D go!

e.go()
# go A go!
# go C go!
# go B go!

a.stop()
# stop A stop!

b.stop()
# stop A stop!

c.stop()
# stop A stop!
# stop C stop!

d.stop()
# stop A stop!
# stop C stop!
# stop D stop!

e.stop()
# stop A stop!

a.pause()
# ... Exception: Not Implemented

b.pause()
# ... Exception: Not Implemented

c.pause()
# ... Exception: Not Implemented

d.pause()
# wait D wait!

e.pause()
# ...Exception: Not Implemented

```

### [](#why-do-we-care)Why do we care?

Because OO programming is really, really important. Really. Answering this question shows your understanding of inheritance and the use of Python's `super` function. Most of the time the order of resolution doesn't matter. Sometimes it does, it depends on your application.

## [](#question-11)Question 11

Consider the following code, what will it output?

```

class Node(object):
    def __init__(self,sName):
        self._lChildren = []
        self.sName = sName
    def __repr__(self):
        return "<Node '{}'>".format(self.sName)
    def append(self,*args,**kwargs):
        self._lChildren.append(*args,**kwargs)
    def print_all_1(self):
        print(self)
        for oChild in self._lChildren:
            oChild.print_all_1()
    def print_all_2(self):
        def gen(o):
            lAll = [o,]
            while lAll:
                oNext = lAll.pop(0)
                lAll.extend(oNext._lChildren)
                yield oNext
        for oNode in gen(self):
            print(oNode)

oRoot = Node("root")
oChild1 = Node("child1")
oChild2 = Node("child2")
oChild3 = Node("child3")
oChild4 = Node("child4")
oChild5 = Node("child5")
oChild6 = Node("child6")
oChild7 = Node("child7")
oChild8 = Node("child8")
oChild9 = Node("child9")
oChild10 = Node("child10")

oRoot.append(oChild1)
oRoot.append(oChild2)
oRoot.append(oChild3)
oChild1.append(oChild4)
oChild1.append(oChild5)
oChild2.append(oChild6)
oChild4.append(oChild7)
oChild3.append(oChild8)
oChild3.append(oChild9)
oChild6.append(oChild10)

# specify output from here onwards

oRoot.print_all_1()
oRoot.print_all_2()

```

### [](#answer-10)Answer

`oRoot.print_all_1()` prints:

```
<Node 'root'>
<Node 'child1'>
<Node 'child4'>
<Node 'child7'>
<Node 'child5'>
<Node 'child2'>
<Node 'child6'>
<Node 'child10'>
<Node 'child3'>
<Node 'child8'>
<Node 'child9'>

```

`oRoot.print_all_2()` prints:

```
<Node 'root'>
<Node 'child1'>
<Node 'child2'>
<Node 'child3'>
<Node 'child4'>
<Node 'child5'>
<Node 'child6'>
<Node 'child8'>
<Node 'child9'>
<Node 'child7'>
<Node 'child10'>

```

### [](#why-do-we-care-2)Why do we care?

Because composition and object construction is what objects are all about. Objects are composed of stuff and they need to be initialised somehow. This also ties up some stuff about recursion and use of generators.

Generators are great. You could have achieved similar functionality to `print_all_2` by just constructing a big long list and then printing it's contents. One of the nice things about generators is that they don't need to take up much space in memory.

It is also worth pointing out that `print_all_1` traverses the tree in a depth-first manner, while `print_all_2` is width-first. Make sure you understand those terms. Sometimes one kind of traversal is more appropriate than the other. But that depends very much on your application.

## [](#question-12)Question 12

Describe Python's garbage collection mechanism in brief.

### [](#answer-11)Answer

A lot can be said here. There are a few main points that you should mention:

*   Python maintains a count of the number of references to each object in memory. If a reference count goes to zero then the associated object is no longer live and the memory allocated to that object can be freed up for something else
*   occasionally things called "reference cycles" happen. The garbage collector periodically looks for these and cleans them up. An example would be if you have two objects `o1` and `o2` such that `o1.x == o2` and `o2.x == o1`. If `o1` and `o2` are not referenced by anything else then they shouldn't be live. But each of them has a reference count of 1.
*   Certain heuristics are used to speed up garbage collection. For example, recently created objects are more likely to be dead. As objects are created, the garbage collector assigns them to generations. Each object gets one generation, and younger generations are dealt with first.

This explanation is CPython specific.

## [](#question-13)Question 13

Place the following functions below in order of their efficiency. They all take in a list of numbers between 0 and 1\. The list can be quite long. An example input list would be `[random.random() for i in range(100000)]`. How would you prove that your answer is correct?

```

def f1(lIn):
    l1 = sorted(lIn)
    l2 = [i for i in l1 if i<0.5]
    return [i*i for i in l2]

def f2(lIn):
    l1 = [i for i in lIn if i<0.5]
    l2 = sorted(l1)
    return [i*i for i in l2]

def f3(lIn):
    l1 = [i*i for i in lIn]
    l2 = sorted(l1)
    return [i for i in l1 if i<(0.5*0.5)]

```

### [](#answer-12)Answer

Most to least efficient: `f2`, `f1`, `f3`. To prove that this is the case, you would want to profile your code. Python has a lovely [profiling package](https://docs.python.org/2/library/profile.html) that should do the trick.

```
import cProfile
lIn = [random.random() for i in range(100000)]
cProfile.run('f1(lIn)')
cProfile.run('f2(lIn)')
cProfile.run('f3(lIn)')

```

For completion's sake, here is what the above profile outputs:

```
>>> cProfile.run('f1(lIn)')
         4 function calls in 0.045 seconds

   Ordered by: standard name

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        1    0.009    0.009    0.044    0.044 <stdin>:1(f1)
        1    0.001    0.001    0.045    0.045 <string>:1(<module>)
        1    0.000    0.000    0.000    0.000 {method 'disable' of '_lsprof.Profiler' objects}
        1    0.035    0.035    0.035    0.035 {sorted}

>>> cProfile.run('f2(lIn)')
         4 function calls in 0.024 seconds

   Ordered by: standard name

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        1    0.008    0.008    0.023    0.023 <stdin>:1(f2)
        1    0.001    0.001    0.024    0.024 <string>:1(<module>)
        1    0.000    0.000    0.000    0.000 {method 'disable' of '_lsprof.Profiler' objects}
        1    0.016    0.016    0.016    0.016 {sorted}

>>> cProfile.run('f3(lIn)')
         4 function calls in 0.055 seconds

   Ordered by: standard name

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        1    0.016    0.016    0.054    0.054 <stdin>:1(f3)
        1    0.001    0.001    0.055    0.055 <string>:1(<module>)
        1    0.000    0.000    0.000    0.000 {method 'disable' of '_lsprof.Profiler' objects}
        1    0.038    0.038    0.038    0.038 {sorted}

```

### [](#why-care-2)Why Care?

Locating and avoiding bottlenecks is often pretty worthwhile. A lot of coding for efficiency comes down to common sense - in the example above it's obviously quicker to sort a list if it's a smaller list, so if you have the choice of filtering before a sort it's often a good idea. The less obvious stuff can still be located through use of the proper tools. It's good to know about these tools.

## [](#question-14)Question 14

Something you failed at?

### [](#wrong-answer)Wrong answer

I never fail!

### [](#why-this-is-important)Why This Is Important:

Shows that you are capable of admitting errors, taking responsibility for your mistakes, and learning from your mistakes. All of these things are pretty darn important if you are going to be useful. If you are actually perfect then too bad, you might need to get creative here.

## [](#question-15)Question 15

Do you have any personal projects?

### [](#really)Really?

This shows that you are willing to do more than the bare minimum in terms of keeping your skillset up to date. If you work on personal projects and code outside of the workplace then employers are more likely to see you as an asset that will grow. Even if they don't ask this question I find it's useful to broach the subject.

## [](#conclusion)Conclusion

These questions intentionally touched on many topics. And the answers were intentionally verbose. In a programming interview, you will need to demonstrate your understanding and if you can do it in a concise way then by all means do that. I tried to give enough information in the answers that you could glean some meaning from them even if you had never heard of some of these topics before. I hope you find this useful in your job hunt.

Go get 'em tiger.

</div>
