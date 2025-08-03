# Leetcode-1974.-Minimum-Time-to-Type-Word-Using-Special-Typewriter
# Description
There is a special typewriter with lowercase English letters 'a' to 'z' arranged in a circle with a pointer. A character can only be typed if the pointer is pointing to that character. The pointer is initially pointing to the character 'a'.

<img width="530" height="410" alt="image" src="https://github.com/user-attachments/assets/c043f32b-e676-446a-b74c-4afc2e33bdf7" />

Each second, you may perform one of the following operations:

Move the pointer one character counterclockwise or clockwise.
Type the character the pointer is currently on.
Given a string word, return the minimum number of seconds to type out the characters in word.
# Solution
In the given problem we have been given a typewriter with lowercase characters in english ( a to z) . We have also been given a string word which contains the letters and we have to find the minimum time or cost required to type and move from the current character to the next character .

The initial character to which has been pointed is 'a'. 

Example:
word='bza'

Output = 7
Th operations would be :
- Move the pointer clockwise to 'b' = 1 second.
- Type the character 'b'  = 1 second.
- Move the pointer anticlockeise because it will take minimum cost to reach 'z'  = 2 seconds.
- Type the character 'z'  =  1 second.
- Move the pointer clockwise to 'a' =  1 second.
- Type the character 'a' =  1 second.
 Total cost = 7 seconds

Hence one thing is known by this example that we need to find the minimum cost between the clockwise direction answer and anti-clockwise.

# Algorithm
1.  Create a variable time and initialize it to 0 — this will store the total time.
2. Create a variable pointer and set it to 'a' — this represents the starting position of the typewriter.

3. Loop through each character c in the input string word.

4. For each character, calculate the:

Clockwise distance: (c - pointer + 26) % 26

Anticlockwise distance: (pointer - c + 26) % 26

5. Take the minimum of clockwise and anticlockwise distances — this gives the shortest rotation time to reach the character.

6. Add 1 to the result for typing the character.

7. Add the total for this character to time.

8. Update pointer to c, so that it points to the current character for the next iteration.

9. After the loop, return time — this is the minimum total time to type the word.
# Code

 C++
 
 class Solution {
 
public:

    int minTimeToType(string word) {
        int time=0;
        int pointer='a';
        for(char c : word){
            int anticlockwise=(pointer-c+26)%26;
            int clockwise=(c-pointer+26)%26;
            time+=min(anticlockwise,clockwise)+1;
            pointer =c;
        }
        return time;
    }
};
# Complexity
Time Complexity: O(n)

n = length of the input string word.

The loop runs once for each character in the string.

Each operation inside the loop (like arithmetic and min) takes constant time.

Efficient — linear with respect to the size of the input.

Space Complexity: O(1)

Only a fixed number of variables (time, pointer, c, clockwise, anticlockwise) are used.

No extra space is used that grows with input size.

Constant space — independent of input size.
