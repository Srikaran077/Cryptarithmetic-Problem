<h1>ExpNo 8 : Solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python</h1> 
<h3>Name:       Srikaran M       </h3>
<h3>Register Number/Staff Id:  212223040206   </h3>

<H3>Aim:</H3>
<p>
    To solve Cryptarithmetic Problem,a CSP(Constraint Satisfaction Problem) using Python
</p>

<h3>Procedure:</h3>
Input and Output
<br>Input:
This algorithm will take three words.
<br> B A S E<br>
    B A L L<br>
           ----------<br>
           G A M E S<br>

Output:
It will show which letter holds which number from 0 – 9.
For this case it is like this.

```
          B A S E                         2 4 6 1
          B A L L                         2 4 5 5
         ---------                       ---------
        G A M E S                       0 4 9 1 6
```

<h3>Algorithm</h3>
For this problem, we will define a node, which contains a letter and its corresponding values.<br>

isValid(nodeList, count, word1, word2, word3)<br>

Input − A list of nodes, the number of elements in the node list and three words.<br>

Output − True if the sum of the value for word1 and word2 is same as word3 value.<br>

Begin<br>
m := 1<br>
for each letter i from right to left of word1, do<br>
ch := word1[i]<br>
for all elements j in the nodeList, do<br>
if nodeList[j].letter = ch, then<br>
break<br>
done<br>
val1 := val1 + (m * nodeList[j].value)<br>
m := m * 10<br>
done<br>

m := 1<br>
for each letter i from right to left of word2, do<br>
ch := word2[i]<br>
for all elements j in the nodeList, do<br>
if nodeList[j].letter = ch, then<br>
break<br>
done<br>

```
  val2 := val2 + (m * nodeList[j].value)<br>
  m := m * 10<br>
```

done<br>

m := 1<br>
for each letter i from right to left of word3, do<br>
ch := word3[i]<br>
for all elements j in the nodeList, do<br>
if nodeList[j].letter = ch, then<br>
break<br>
done<br>

```
  val3 := val3 + (m * nodeList[j].value)<br>
  m := m * 10<br>
```

done<br>

if val3 = (val1 + val2), then<br>
return true<br>
return false<br>
End<br>

<h3>Program:</h3>

<pre>
from itertools import permutations

def solve_cryptarithmetic(word1, word2, word3):

    letters = set(word1 + word2 + word3)

    if len(letters) > 10:
        print("No solution possible")
        return

    leading_letters = set([word1[0], word2[0], word3[0]])

    for values in permutations(range(10), len(letters)):

        mapping = dict(zip(letters, values))

        # Leading letters cannot be zero
        if any(mapping[letter] == 0 for letter in leading_letters):
            continue

        value1 = int(''.join(str(mapping[ch]) for ch in word1))
        value2 = int(''.join(str(mapping[ch]) for ch in word2))
        value3 = int(''.join(str(mapping[ch]) for ch in word3))

        if value1 + value2 == value3:
            print("Solution Found:")

            for letter in sorted(mapping):
                print(letter, "=", mapping[letter])

            print()
            print(word1, "=", value1)
            print(word2, "=", value2)
            print("-" * 15)
            print(word3, "=", value3)

            return

    print("No solution found")


# Main Program
word1 = "SEND"
word2 = "MORE"
word3 = "MONEY"

solve_cryptarithmetic(word1, word2, word3)
</pre>

<h3>Output:</h3>

<p>
<img width="443" height="204" alt="image" src="https://github.com/user-attachments/assets/f7de17c6-f111-4dfe-be8a-dbad5d69700e" />

</p>

<hr>

<h2>Sample Input and Output:</h2>

SEND = 9567<br>
MORE = 1085<br>

<hr>
MONEY = 10652<br>

<hr>

<h2>Result:</h2>
<p>
Thus a Cryptarithmetic Problem was solved using Python successfully
</p>
