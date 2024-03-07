Weak passwords are likely to be hacked and misused. Due to this, developers at Amazon regularly come up with new algorithms to check the health of user passwords. A new algorithm estimates the variability of a password as the number of distinct password strings that can be obtained by reversing any one substring of the original password. Given the original password that consists of lowercase English characters, find its variability.

Note: A substring is a contiguous sequence of characters within a string. For example 'bcd', 'a', 'abcd' are substrings of the string 'abcd' whereas the strings 'bd', 'acd' are not.

Example

The following strings can be formed from password = 'abc':

Reversing any substring of length 1 gives the original string "abc".
Reversing the substring "ab" gives a new string "bac". • Reversing the substring "bc" gives a new string "acb".
Reversing the substring "abc" gives a new string "cba".
There are 4 distinct password strings that can be obtained from password. Return 4.

Function Description

Write a function countDistinctPasswords that has the following parameters:

string password: the original password
Returns

long_int: the number of distinct password strings that can be formed
Constraints

# MaangSubstring
MAANG substring problem
public class DistinctSubStrings {
    public static int countDistnctPassword(String password){
        Set<String> distinctPassword=new HashSet<>();
        int length=password.length();
        //Iterate through all possible substrings
        for(int i=0;i<length;i++){
            for(int j=i+1;j<=length;j++){
                String substring=password.substring(i,j);
                String reversedSubstring =new StringBuilder(substring).reverse().toString();
                String newPassword=password.substring(0,i) + reversedSubstring + password.substring(j);
                distinctPassword.add(newPassword);
            }
        }
        return distinctPassword.size();
    }
    public static void main(String[] args) {
        String password = "abc";
        System.out.println(countDistnctPassword(password)); // Output: 4
    }
}
