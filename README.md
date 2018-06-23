Running the algorithm $$K$$ times it is clear that it will remove k characters in alphabetic order.
First all 'a' (if existed), then all 'b' (if existed) .. and so on.
Idea is to process the positions of the characters. There are total $$26$$ characters. $$1st$$ one is '$$a$$' and $$26^{th}$$ one is '$$z$$'.
Let the string be $$S$$.
Make an array of vectors $$[V_1, V_2, V_3 ..... V_{26}]$$
$$V_i$$$$$$  will contain the positions of $$i^{th}$$ character in string $$S$$.

If we process the string from start. and make our vectors along the way. notice that all of them will be sorted in ascending order.
for example string "$$aacadccd$$"
$$V_1$$ = $$\{1, 2, 4\}$$  [Positions of 'a']
$$V_3$$ = $$\{3,6,7\}$$ [Positions of 'c']
$$V_4$$ = $$\{5, 8\}$$ [Positions of 'd']
rest of the vectors are empty.

Now.. we need to remove $$K$$ characters.. alphabetically.
More exactly. $$K$$ positions.
More exactly. $$K$$ elements from our vectors. starting from first one (as it's alphabetical).

For above example, let $$K = 5$$.
So, we remove all from $$V_1$$, then $$2$$ from $$V_2$$ .
Result ->
$$V_1$$ = $$\{\}$$ 
$$V_3$$ = $$\{7\}$$ 
$$V_4$$ = $$\{5, 8\}$$

Now, we have the positions which needed to be in the string.
so. we process the string again, now for every character we need to know if that position is in its corresponding vector.
if it is we print that character else we skip to next one.

**Complexity**
The Vector generating part can be done in $$O(N)$$ . [N being the size of string]
position removal part can be done in $$O(K)$$
and then, per character it will take $$O(log ({N}))$$. as, all the vectors are sorted we can safely binary search.
so total complexity **O(Nlog(N))**