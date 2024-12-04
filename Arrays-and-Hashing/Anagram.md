# [Valid Anagram](https://leetcode.com/problems/valid-anagram/)

## String Operations - Removing characters

### Code
```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())
            return false;
        for(int i=0;i<s.length();i++) {
            char ch = s.charAt(i);
            if(t.contains(String.valueOf(ch)))
                t = t.replaceFirst(String.valueOf(ch), "");
        }
        if(t.length()==0)
            return true;
        return false;
    }
}
```

### Approach
1. Iterate the loop to check for pick on character from the string
2. Check with string operations if the character from the string is present in the other string
3. Remove the character from the other string if present and go on with this process until we scan all the characters of the string
4. The former string should be empty if its a valid Anagram

#### Space Complexity - O(n)
The storage of the input strings and the creation of new strings during replacements

#### Time Complexity - O(n<sup>2</sup>)
Both *contains* and *replaceFirst* can take O(n) time in the worst case. Since there are n iterations of the the string s, O(n) x O(n) = O(n<sup>2</sup>)
<br>
Note: One can remove the condition to check if the string contains the character or not as replaceFirst function will return the string unchanged in case of replacement character not found.

## Negating the frequency

### Code
```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())
            return false;
        int[] count = new int[26];
        for(int i=0;i<s.length();i++){
            count[s.charAt(i) - 'a']++;
            count[t.charAt(i) - 'a']--;
        }
        for(int num: count){
            if(num != 0)
                return false;
        }
        return true;
    }
}
```

### Approach
1. Create an array of 26 resembling the total number of alphabets
2. For string s, increment and place the character based on the alphabet position
3. For string t, decrement and place the character based on the alphabet position
4. For a valid anagram, the array count will contain zero in all the 26 places

#### Space Complexity - O(1)
Since we are using a fixed array it is O(1)

#### Time Complexity - O(n)
* Counting characters: O(n)
* Checking counts: O(26) which is O(1)
* Overall: O(n)
