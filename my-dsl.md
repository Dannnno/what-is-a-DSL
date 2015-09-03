# Language
The [Kivy Language (kv lang)](http://kivy.org/docs/api-kivy.lang.html).


# Domain
User interface/interactions in Kivy applications.


# Computational model
This language can't be executed alone - it requires (at the very least) a small
wrapper of Python code.  When executed it is used to describe an application's
appearance and interactability.  This is similar to HTML/CSS in web 
development, or QML for Qt, or FXML for JavaFX.  Thus the file is parsed, then
used to render the application.


# DSL-ness
This is not a purely domain-specific language.  It is essentially a modified 
version of the Python language spec - in fact a large number of its statements
are valid Python statements.  Thus it can do an awful lot beyond just laying
out the application.  That being said, it would/should rarely be used as
anything more than a DSL.  It is not a particularly friendly format to just
write code in, and is designed to work within the constraints of a Kivy
application.

# Internal or external?
External.  While it is heavily based on the Python language spec and can
contain valid Python code, it is not in and of itself a valid Python program,
and requires its own parser to be used.

_Question: I'm not sure how to actually classify this DSL.  It seems like a bit
of a blend, considering that substantial portions of it are or can be valid
Python code._


# Host language
Kivy is designed to be used from Python, potentially with C/C++ extensions.
The implementation of the Kivy framework is done predominantly using Cython, a
Python/C hybrid.  The Kivy Language itself is heavily based on the Python
language, and is parsed, executed by a Cython parser/interpreter.


# Benefits
This makes it very easy to separate the concerns of an application - the
display of the application can be very easily and cleanly separated from the
business logic.  This makes it easy to change one and not the other.

It also can make it easier for a non-programmer to have some idea of how the
application is/should appear, letting a designer or product manager to have a
better idea of what is going on without having to understand the code or
actually run the code.


# Drawbacks
One drawback is that it separates the concerns of the application.  It can
become difficult to manage breaking changes to either the .py file or the .kv
file.  If something is renamed or removed from one file, but not the other,
this can cause problems.  