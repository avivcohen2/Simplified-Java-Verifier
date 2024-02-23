=============================
=      File description     =
=============================
Block - class representing a general block that has a condition
BlockException - class suits for exceptions of blocks
BlockFactory - a factory for blocks
IfBlock - object representing an if block
WhileBlock - object representing a while block
GeneralException - a class for general exceptions
Parser - main class which is responsible for parsing a file
Sjavac - the main file of the program, which uses the parser to check each file
Method - class representing a method object that has a name, list of parameters and variables, and a start
row of the method in the file
MethodException - class suits for exceptions of methods
MethodFactory - factory for method objects
Variable - an object representing a variable, which has a name, value, type and a boolean field if
the variable is final or not
VariableException - class suits for exceptions of variables
VariableFactory - a factory for variables
VariableValidation - class responsible for variable validation - checking type and values


=============================
=          Design           =
=============================
we have created 4 packages - variables, methods, if and while blocks and the main package.

Variable - represents a variable object, contains name, value, type and isFinal fields and 2 different
constructors, in case needed to create a variable without a value. Before each variable is created, its
values go through VariableValidation which contains helper methods to understand if the variable given is
legal. If the variable is legal according to all restrictions, the variable is sent to VariableFactory which
create new variables with all their information. Also there is VariableException, in case an error was
found in a line dealing with variables.

Method - a class representing a method object, contains name, starting row, list of parameters and list of
variables as fields, a constructor, and getters and setters methods. Each line of a method declaration is
sent to the MethodFactory where the parameters are being checked- as local variables of the method.
If all line is legal then a new method is created by using MethodFactory. In case an error was found in the
declaration line a MethodException is being thrown.

If and While block - a class representing a block which has a boolean condition. When a line is being
recognized as a block initiating line, the line is being sent to BlockFactory which check the condition to
be legal - containing only boolean legal expressions. In case an error is found, a BlockException is being
thrown.

Main - contains the main classes that manage the program. Sjavac - which call Parser to go over all fine
lines and check their validity. GeneralException is thrown in case an illegal line is found.
Parser - goes over all linea, checking global scope - all lines should be only variables
assignment, variables declaration, methods declaration. Parser also checks the local scope of a method -
also containing if and while block, method calls and return statements.

Alternatives we ruled out:
We thought about trying to create regex patterns for every possible legal combination of code lines but
we decided to split it to reasonable parts which was easier to modularize. Instead, we used the matches
group and used in few combinations.
Also, we could have create a class for each variable, each one is a sub-class of Variable which is an
abstract class. Instead, we created an enum class which represents the variable type, so we didn't have
to use instance-of.
