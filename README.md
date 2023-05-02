Download Link: https://assignmentchef.com/product/solved-comp3220-building-a-lexical-analyser-with-ruby
<br>
The grammar rules for the language “TINY” are listed below. In this assignment we will identify the tokens in this language and build a lexical analyser (lexer) for recognizing and outputting TINY tokens.




# <a href="http://www.cs.rochester.edu/%7Ebrown/173/readings/05_grammars.txt">https://www.cs.rochester.edu/~brown/173/readings/05_grammars.txt</a>

#

#  “TINY” Grammar

#

# PGM        –&gt;   STMT


# STMT       –&gt;   ASSIGN   |   “print”  EXP

# ASSIGN     –&gt;   ID  “=”  EXP

# EXP        –&gt;   TERM   ETAIL

# ETAIL      –&gt;   “+” TERM   ETAIL  | “-” TERM   ETAIL | EPSILON

# TERM       –&gt;   FACTOR  TTAIL

# TTAIL      –&gt;   “*” FACTOR TTAIL  | “/” FACTOR TTAIL | EPSILON

# FACTOR     –&gt;   “(” EXP “)” | INT  | ID

#

# ID         –&gt;   ALPHA


# ALPHA      –&gt;   a  |  b  | … | z  or

#                  A  |  B  | … | Z

# INT        –&gt;   DIGIT


# DIGIT      –&gt;   0  |  1  | …  |  9

# WHITESPACE –&gt;   Ruby Whitespace




Whenever a token is identified, we encapsulate it using the Token class below. Each token has a type and text. For example, if DOG was identified as a variable in this language, it could have type “id” and

text “DOG”. The add operator might have type “addOp” and text “+” or type “+” and text “+”.  These values are somewhat arbitrary – choose values that make sense to you.




<h2>Token Class</h2>

I have given you a partially complete Token class that you should modify for this assignment called “<strong>TinyToken.rb</strong>”. It has a few constants already defined. You will need to build constants for all the tokens.




It is important to test all the code you write. At the very least, use “puts” to test the class methods. You can build the tests in separate files and load them as needed: load “mytest.rb”.  The code below tests the Token class methods.




# Test the Token class




tok = Token.new(“atype”,”atext”) puts “Token type: #{tok.type}” puts “Token text: #{tok.text}” tok.type = “btype”

tok.text = “btext”

puts “Token type: #{tok.type}” puts “Token text: #{tok.text}” puts “Token: #{tok}”




<h2>The “Lexer”</h2>

The first goal is to build a Scanner (or Lexer) for TINY. I have sketched the basic structure in file named “<strong>TinyScanner.rb</strong>”. Here are a few points to consider:




<ul>

 <li>The constructor is passed a file name which contains the source code for a TINY program. The constructor opens the file and reads the first character, storing it in class variable @c (which acts as a one-character look ahead).</li>

 <li>Currently, the Scanner abends if it is passed a file that doesn’t exist. Modify the code so that it fails gracefully in this</li>

 <li>Method nextCh() updates @c with the next character and returns it, unless it has reached the end of the file, in which case it will return “<strong>!eof!</strong>”.</li>

 <li>Method nextToken() returns the next token identified by the It is not complete, as it does not identify all Tokens in your grammar yet. You should complete this method.</li>

 <li>Contiguous whitespace should be combined and emitted as a single (I already did this for you).</li>

 <li>An end of file (EOF) token should be emitted when the file has been completely (I already did this for you).</li>

 <li>There are several helper methods defined at the bottom of “TinyScanner.rb” that you can use to help you to identify different types of characters (like numbers, letters, and whitespace).</li>

</ul>




<h2>Display and Print Tokens</h2>

I’ve included a 3<sup>rd</sup> file called “<strong>TestTinyLexer.rb</strong>” that will use your lexer (previous section) and display each token it encounters as it lexes your source code file. I would like for you to modify this file so that in addition to displaying the tokens to the console, it will also write them to a file (that we could potentially pass to a parser).




I’ve also included a sample input file (input.txt)that adheres to our TINY programming language. You should experiment with different inputs that both adhere to and don’t adhere to the grammar to verify the correctness of your lexer.




<h2>Sample Program Output</h2>

Below is a screenshot of sample output that would result from using the included sample input file.































Below is a screenshot of the token file that was generated as a result of lexing the same input file (TINY source code file).




<h2>Deliverables (THIS IS WHAT YOU SHOULD TURN IN)</h2>

<ol>

 <li>rb</li>

 <li>rb</li>

 <li>rb</li>

</ol>