In Bash scripting, you can use the `test` command (or the shorthand `[ ]`) to evaluate expressions, including conditions for comparisons, file checks, and logical operators.

### Common Test Expressions in Bash

1. **String comparisons:**
   - Check if strings are equal or not equal.
     ```bash
     [ "$str1" = "$str2" ]  # Checks if str1 is equal to str2
     [ "$str1" != "$str2" ]  # Checks if str1 is not equal to str2
     ```

2. **Numeric comparisons:**
   - Comparing integers.
     ```bash
     [ "$num1" -eq "$num2" ]  # Checks if num1 is equal to num2
     [ "$num1" -ne "$num2" ]  # Checks if num1 is not equal to num2
     [ "$num1" -lt "$num2" ]  # Checks if num1 is less than num2
     [ "$num1" -gt "$num2" ]  # Checks if num1 is greater than num2
     ```

3. **File checks:**
   - Test for file attributes.
     ```bash
     [ -e "$file" ]  # Checks if file exists
     [ -f "$file" ]  # Checks if it is a regular file
     [ -d "$dir" ]   # Checks if it is a directory
     [ -r "$file" ]  # Checks if file is readable
     [ -w "$file" ]  # Checks if file is writable
     [ -x "$file" ]  # Checks if file is executable
     ```

4. **Logical operators:**
   - Combine conditions using logical AND, OR, and NOT.
     ```bash
     [ "$num1" -eq "$num2" ] && echo "Equal"   # AND
     [ "$num1" -eq "$num2" ] || echo "Not equal"  # OR
     [ ! -e "$file" ]  # NOT, checks if file does not exist
     ```

### Example of using `test` in an `if` statement:
```bash
#!/bin/bash

num=10

if [ "$num" -gt 5 ]; then
  echo "The number is greater than 5"
else
  echo "The number is 5 or less"
fi
```

Let me know if you need further details or examples of specific tests!
