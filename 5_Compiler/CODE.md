Imports :-
# Imports 

Important imports that we are going to need for creating a compiler

```cpp
#include <cctype>               // for checking characters 
#include <iostream>             // for input and output 
#include <stdexcept>            // for managing runtime 
#include <string>               // for storing and manipulating strings
#include <vector>

using namespace std;
```

Creating a enum that will help us create own data type

```cpp
enum TokenType { NUMBER, PLUS, MINUS, MULTIPLY, DIVIDE, END };
```

Struct help us create a array but with different data types

```cpp
struct Token {
  TokenType type;
  string value;
};
```

In This class we are gonna create Lexer which is a part of compiler that tokenize the code to convert the code into into something like this :- 
```
3 = NUMBER
* = MULTIPLY
/ = DIVIDE
```

So for first step in execution in the class we created is we are gonna create two private member of class Lexer which are input and pos , The input have the code it is been provided .

Then we created a constructor which is an explicit flag and in this constructor we are assigning input and pos value to input string and 0 so that it have to start from 0

Then for main step in lexer we created a function getNextToken() it basically do only three things skip he spaces and return END at the end of line and where it provides token to its respective values

```cpp
class Lexer {
  string input;
  size_t pos;

public:
  explicit Lexer(const string &input) : input(input), pos(0) {}

  Token getNextToken() {
    while (pos < input.length() && std::isspace(input[pos])) {
      pos++;
    }

    if (pos >= input.length()) {
      return {END, ""};
    }

    char current = input[pos];

    if (std::isdigit(current)) {
      string number;
      while (pos < input.length() && std::isdigit(input[pos])) {
        number += input[pos++];
      }
      return {NUMBER, number};
    } else if (current == '+') {
      pos++;
      return {PLUS, "+"};
    } else if (current == '-') {
      pos++;
      return {MINUS, "-"};
    } else if (current == '*') {
      pos++;
      return {MULTIPLY, "*"};
    } else if (current == '/') {
      pos++;
      return {DIVIDE, "/"};
    }

    throw std::runtime_error("Unexpected character: " + string(1, current));
  }
};
```

```cpp
class Parser {
  Lexer lexer;
  Token currentToken;

  void eat(TokenType type) {
    if (currentToken.type == type) {
      currentToken = lexer.getNextToken();
    } else {
      throw std::runtime_error("Unexpected token");
    }
  }

  // Parse a factor (a number or a parenthesized expression)
  int factor() {
    Token token = currentToken;
    eat(NUMBER);
    return std::stoi(token.value);
  }

  // Parse multiplication and division
  int term() {
    int result = factor();

    while (currentToken.type == MULTIPLY || currentToken.type == DIVIDE) {
      Token token = currentToken;
      if (token.type == MULTIPLY) {
        eat(MULTIPLY);
        result *= factor();
      } else if (token.type == DIVIDE) {
        eat(DIVIDE);
        int divisor = factor();
        if (divisor == 0) {
          throw std::runtime_error("Division by zero");
        }
        result /= divisor;
      }
    }

    return result;
  }

  // Parse addition and subtraction
  int expr() {
    int result = term();

    while (currentToken.type == PLUS || currentToken.type == MINUS) {
      Token token = currentToken;
      if (token.type == PLUS) {
        eat(PLUS);
        result += term();
      } else if (token.type == MINUS) {
        eat(MINUS);
        result -= term();
      }
    }

    return result;
  }

public:
  explicit Parser(Lexer lexer) : lexer(lexer) {
    currentToken = this->lexer.getNextToken();
  }

  int parse() { return expr(); }
};
```

```cpp

int main() {
  cout << "Enter an arithmetic expression: ";
  string input;
  getline(cin, input);

  try {
    Lexer lexer(input);
    Parser parser(lexer);
    int result = parser.parse();
    cout << "Result: " << result << endl;
  } catch (const std::exception &e) {
    cerr << "Error: " << e.what() << endl;
  }

  return 0;
}

```
