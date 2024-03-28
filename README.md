[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/OlW38W4k)
# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Answer: The recurrence relation would be T(n) = 3T(n/3) + n^5. The time complexity would be $O$(n^5). 
1. Base Case: 1 if n <= 1
T(n) = 3T(n/3) + n^5 if n < 1
T(n/3) = 3T(n/9) + (n/3)^5
T(n) = 3(3T(n/9) + (n/3)^5) + n^5
T(n) = 3^2T(n/9) + (n^5/3^4)) + n^5
T(n) = 3^2T(n/9) + ((3^4 + 1)n^5/3^4)
T(n/9) = (3T(n/27) + (n/9)^5)
T(n) = 3^2(3T(n/27) + (n^5/9^5)) + (82n^5/81)
T(n) = 3^3T(n/27) + (n^5/9^4) + (82n^5/81)
T(n) = 3^3T(n/27) + ((9^4 + 1)n^5/9^4)
3^iT(n/3^i) + ((3^(i-1) + 1)n^5/(3^i-1)^4)
for i = log n
= nT(1) + n^5(1/1^4)
= n + n^5 belongs to $O$(n^5) 


        
