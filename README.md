# Program Name: math_master_pro_flow_hidden

import math
import re
import sys

# --- Pythagoras Functions ---
def explain_pythagoras(question):
    q = question.lower()
    if "formula" in q:
        return "Formula: a² + b² = c², where c is the hypotenuse."
    elif "example" in q:
        return "Example: If a=3 and b=4, then c²=3²+4²=25 → c=5."
    elif "proof" in q:
        return "One proof: rearranging squares on the sides of a right triangle shows that the area of the hypotenuse square equals the sum of the other two."
    else:
        return "The Pythagoras theorem states: a² + b² = c² in a right-angled triangle."

def solve_triangle(a=None, b=None, c=None):
    if a and b:
        return f"Hypotenuse c = {math.sqrt(a**2 + b**2):.2f}"
    elif a and c and c > a:
        return f"Side b = {math.sqrt(c**2 - a**2):.2f}"
    elif b and c and c > b:
        return f"Side a = {math.sqrt(c**2 - b**2):.2f}"
    else:
        return "Please provide valid sides."

def solve_word_problem_pythagoras(problem):
    q = problem.lower()
    numbers = [float(n) for n in re.findall(r'\d+', q)]

    if "ladder" in q and "wall" in q and len(numbers) >= 2:
        c, b = numbers[0], numbers[1]
        return f"Ladder reaches {math.sqrt(c**2 - b**2):.2f} units high."
    elif "rectangle" in q and "diagonal" in q and len(numbers) >= 2:
        a, b = numbers[0], numbers[1]
        return f"Diagonal = {math.sqrt(a**2 + b**2):.2f}"
    elif "points" in q and "distance" in q and len(numbers) >= 4:
        x1, y1, x2, y2 = numbers
        return f"Distance = {math.sqrt((x2-x1)**2 + (y2-y1)**2):.2f}"
    elif "square" in q and "diagonal" in q and len(numbers) >= 1:
        side = numbers[0]
        return f"Diagonal = {math.sqrt(2)*side:.2f}"
    elif "building" in q and "shadow" in q and len(numbers) >= 2:
        c, b = numbers[0], numbers[1]
        return f"Building height = {math.sqrt(c**2 - b**2):.2f}"
    elif "ship" in q or "navigation" in q and len(numbers) >= 2:
        east, north = numbers[0], numbers[1]
        return f"Distance from start = {math.sqrt(east**2 + north**2):.2f}"
    else:
        return "Word problem not recognized."

# --- Trigonometry Functions ---
def explain_trigonometry(question):
    q = question.lower()
    if "sin" in q: return "sin θ = Opposite / Hypotenuse"
    if "cos" in q: return "cos θ = Adjacent / Hypotenuse"
    if "tan" in q: return "tan θ = Opposite / Adjacent"
    return "Trigonometry studies angles and sides of triangles."

def calculate_trig(a=None, b=None, c=None):
    result = []
    if a and c: result.append(f"sin θ = {a/c:.2f}")
    if b and c: result.append(f"cos θ = {b/c:.2f}")
    if a and b: result.append(f"tan θ = {a/b:.2f}")
    return "\n".join(result) if result else "Provide valid sides."

def solve_word_problem_trig(problem):
    q = problem.lower()
    numbers = [float(n) for n in re.findall(r'\d+', q)]

    if "tower" in q and "angle" in q and len(numbers) >= 2:
        b, angle = numbers[0], numbers[1]
        return f"Tower height = {b*math.tan(math.radians(angle)):.2f}"
    elif "shadow" in q and len(numbers) >= 2:
        h, angle = numbers[0], numbers[1]
        return f"Shadow length = {h/math.tan(math.radians(angle)):.2f}"
    elif "building" in q and "angle" in q and len(numbers) >= 2:
        d, angle = numbers[0], numbers[1]
        return f"Building height = {d*math.tan(math.radians(angle)):.2f}"
    elif "lighthouse" in q or "depression" in q and len(numbers) >= 2:
        h, angle = numbers[0], numbers[1]
        return f"Boat distance = {h/math.tan(math.radians(angle)):.2f}"
    elif "river" in q and "cross" in q and len(numbers) >= 2:
        w, angle = numbers[0], numbers[1]
        return f"Crossing distance = {w/math.sin(math.radians(angle)):.2f}"
    else:
        return "Word problem not recognized."

# --- Main Program Flow ---
def start_program():
    print("Hello, I am Math Master Pro!")

    while True:
        print("\nChoose your topic:")
        print("1. Pythagoras Theorem")
        print("2. Trigonometry")
        print("Type 'exit' to quit")

        choice = input("Enter your choice: ").strip()

        # Hidden options
        if choice == "0":
            print("Program stopped.")
            sys.exit()
        elif choice == "67":
            print("Restarting program...")
            return start_program()

        if choice == "exit":
            print("Goodbye!")
            break

        elif choice == "1":
            while True:
                print("\nPythagoras Section:")
                print("      |\\")
                print("      | \\")
                print("      |  \\ c")
                print("      |   \\")
                print("   a  |    \\")
                print("      |_____\\")
                print("         b")
                print("1. Theory\n2. Calculation\n3. Word Problems\nType 'exit' to go back")
                sub = input("Enter choice: ").strip()
                if sub == "exit": break
                elif sub == "1":
                    q = input("Ask about Pythagoras: ")
                    print(explain_pythagoras(q))
                elif sub == "2":
                    vals = input("Enter sides (a=3,b=4): ")
                    d = {}
                    for part in vals.replace(" ", "").split(","):
                        if "=" in part: k,v = part.split("="); d[k]=float(v)
                    print(solve_triangle(d.get("a"), d.get("b"), d.get("c")))
                elif sub == "3":
                    prob = input("Enter word problem: ")
                    print(solve_word_problem_pythagoras(prob))

        elif choice == "2":
            while True:
                print("\nTrigonometry Section:")
                print("      |\\")
                print("      | \\")
                print("      |  \\ c")
                print("      |   \\")
                print("   a  |    \\")
                print("      |_____\\")
                print("         b")
                print("1. Theory\n2. Calculation\n3. Word Problems\nType 'exit' to go back")
                sub = input("Enter choice: ").strip()
                if sub == "exit": break
                elif sub == "1":
                    q = input("Ask about Trigonometry: ")
                    print(explain_trigonometry(q))
                elif sub == "2":
                    vals = input("Enter sides (a=3,b=4,c=5): ")
                    d = {}
                    for part in vals.replace(" ", "").split(","):
                        if "=" in part: k,v = part.split("="); d[k]=float(v)
                    print(calculate_trig(d.get("a"), d.get("b"), d.get("c")))
                elif sub == "3":
                    prob = input("Enter word problem: ")
                    print(solve_word_problem_trig(prob))

# Run program
start_program()

