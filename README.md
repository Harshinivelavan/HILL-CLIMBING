<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name: Harshini V           </h3>
<h3>Register Number:  212224040109           </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>


<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>




<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

<hr>


<h2>Sample Input and Output</h2>


<h2>Sample String:</h2> Artificial Intelligence


<h2>Output:</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>





Program:


~~~
import string
import random

# Generate random initial string
def random_string(length):
    chars = string.printable[:-6]
    return ''.join(random.choice(chars) for _ in range(length))

# Heuristic function
def fitness(current, target):
    return sum(abs(ord(current[i]) - ord(target[i])) for i in range(len(target)))

# Simple Hill Climbing (Ordered)
def hill_climbing(target):
    chars = string.printable[:-6]
    current = random_string(len(target))
    current_score = fitness(current, target)

    print(f"Score: {current_score} Solution : {current}")

    while current_score != 0:
        for i in range(len(target)):
            best = current
            best_score = current_score

            for c in chars:
                if c == current[i]:
                    continue

                temp = current[:i] + c + current[i+1:]
                temp_score = fitness(temp, target)

                if temp_score < best_score:
                    best = temp
                    best_score = temp_score

            if best_score < current_score:
                current = best
                current_score = best_score
                print(f"Score: {current_score} Solution : {current}")

            if current_score == 0:
                break

    print(f"Score: {current_score} Solution : {current}")

target = input("Enter the target string: ")
hill_climbing(target)

~~~



Output:




<img width="567" height="525" alt="Screenshot 2026-02-05 141126" src="https://github.com/user-attachments/assets/20cb9aa1-f5b5-47fe-8d82-506ac54f9cb8" />




Result:



Thus the Hill Climbing Algorithm has been verified successfully.

