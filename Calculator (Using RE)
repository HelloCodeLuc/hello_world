import re

def calculate(expression):

    pattern = r'\(([^()]+)\)'


    def evaluate_brackets(expr):
        match = re.search(pattern, expr)
        while match:
            inner_expr = match.group(1)
            inner_result = evaluate_expression(inner_expr)
            expr = expr.replace(match.group(), str(inner_result))
            match = re.search(pattern, expr)
        return evaluate_expression(expr)


    def evaluate_expression(expr):

        expr_pattern = r'\s*([-+]?\d+(?:\.\d+)?)\s*([+\-*/])\s*([-+]?\d+(?:\.\d+)?)\s*$'
        match = re.match(expr_pattern, expr)
        if match:
            num1 = float(match.group(1))
            operator = match.group(2)
            num2 = float(match.group(3))

            if operator == '+':
                return num1 + num2
            elif operator == '-':
                return num1 - num2
            elif operator == '*':
                return num1 * num2
            elif operator == '/':
                if num2 != 0:
                    return num1 / num2
                else:
                    return "Error: Division by zero"
        else:
            return "Error: Invalid expression"


    result = evaluate_brackets(expression)

    return result


while True:
    expression = input("Enter a mathematical expression (or 'q' to quit): ")
    if expression.lower() == 'q':
        break

    result = calculate(expression)
    print("Result:", result)
