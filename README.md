# Password Cracker

A simple Python-based password cracking tool that demonstrates three different password attack methodologies: Brute Force, Dictionary Attack, and Hybrid Attack. This tool is designed for educational purposes and cybersecurity research.

## Features

- **Brute Force Attack**: Character-by-character password cracking
- **Dictionary Attack**: Wordlist-based password cracking
- **Hybrid Attack**: Advanced attack combining wordlist with common patterns
- **Performance Metrics**: Timing and attempt counting for each method
- **Comprehensive Character Set**: Supports letters, numbers, and special characters
- **Multiple Password Variants**: Tests capitalization and reversal patterns

## Technologies Used

- **Python 3.11.6**
- **Built-in Libraries**: `time` for performance measurement
- **File I/O**: Text file processing for wordlists

## Prerequisites

- Python 3.11.6 installed on your system
- A wordlist file (`wordlist.txt`) for dictionary and hybrid attacks (You can use your own wordlist or the .txt file provided)
- Basic understanding of password security concepts

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Amaanish/Password-Cracker.git
cd Password-Cracker
```

2. Prepare your wordlist file:
```bash
# Create or download a wordlist file named 'wordlist.txt'
# Popular wordlists: rockyou.txt, common-passwords.txt
```

3. Run the script:
```bash
python3 Password Cracker.py
```

## Attack Methods

### 1. Brute Force Attack (`brutemethod`)

**How it works:**
- Attempts every possible character combination
- Uses a comprehensive character set (94 characters total)
- Character-by-character matching approach

**Character Set:**
- Uppercase letters: A-Z
- Lowercase letters: a-z  
- Numbers: 0-9
- Special characters: !@#$%^&*()-_=+[]{};"'<>,./?\\|`~

**Usage:**
```python
brutemethod("Timothy")
```

**Best for:** Short, simple passwords

### 2. Dictionary Attack (`dictmethod`)

**How it works:**
- Tests passwords from a predefined wordlist
- Fast and efficient for common passwords
- Reads from `wordlist.txt` file

**Usage:**
```python
dictmethod("123456789")
```

**Best for:** Common passwords, dictionary words

### 3. Hybrid Attack (`hybridmethod`)

**How it works:**
- Combines dictionary words with common patterns
- Tests multiple variants of each word:
  - Original word
  - Capitalized version
  - Reversed word
- Appends common suffixes to each variant

**Common Suffixes:**
```
"", "123", "1234", "12345", "2023", "2024", "!", "@", "#", "$",
"111", "1111", "007", "99", "00", "2020", "999", "321", "666", "abc"
```

**Usage:**
```python
hybridmethod("Password123")
```

**Best for:** Modified dictionary words with numbers/symbols

## Performance Metrics

Each method provides detailed performance information:

- **Execution Time**: How long the attack took
- **Attempts Made**: Number of password combinations tried
- **Success Rate**: Whether the password was found

### Example Output:
```
Password found: Password123
Guesses tried : 15847
Time taken     : 0.0234s
```

## Project Structure

```
password-cracker/
├── password_cracker.py          # Main script with all attack methods
├── wordlist.txt                # Dictionary file for attacks
├── README.md                   # This documentation
```

## Configuration

### Character Set Customization
Modify the `dict` array to customize the character set:
```python
dict = [
    "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O",
    "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z",
    # Add or remove characters as needed
]
```

### Wordlist Path
Change the wordlist file location:
```python
path = "your-wordlist.txt"
```

### Hybrid Attack Suffixes
Customize common suffixes for hybrid attacks:
```python
suffixes = [
    "123", "2024", "!", "@", "#", 
    # Add your own common patterns
]
```

## Usage Examples

### Basic Usage
```python
# Test different attack methods
brutemethod("abc")           # Simple brute force
dictmethod("password")       # Dictionary attack  
hybridmethod("Admin123!")    # Hybrid attack
```

### Performance Testing
```python
import time

# Time different methods
start = time.time()
dictmethod("123456")
print(f"Dictionary attack took: {time.time() - start:.4f}s")
```

## Attack Method Comparison

| Method | Speed | Success Rate | Resource Usage | Best For |
|--------|-------|--------------|----------------|----------|
| Brute Force | Slow | High (given time) | Very High | Short passwords |
| Dictionary | Fast | Medium | Low | Common passwords |
| Hybrid | Medium | High | Medium | Modified dictionary words |

## Password Security Lessons

This tool demonstrates why strong passwords should:

1. **Avoid dictionary words** - Dictionary attacks are very fast
2. **Use mixed case, numbers, and symbols** - Increases brute force time
3. **Avoid common patterns** - Hybrid attacks target these
4. **Be sufficiently long** - Exponentially increases crack time
5. **Be unique** - Avoid reusing passwords across sites

## Code Structure

### Main Functions

1. **`brutemethod(password)`**
   - Implements character-by-character brute force attack
   - Iterates through all possible characters for each position
   - Provides timing information

2. **`dictmethod(password)`**
   - Reads passwords from wordlist file
   - Tests each word against target password
   - Handles file encoding and errors gracefully

3. **`hybridmethod(password)`**
   - Combines dictionary words with common modifications
   - Tests original, capitalized, and reversed variants
   - Appends common suffixes to increase success rate

## Testing

The script includes example function calls:
```python
brutemethod("Timothy")        # Tests brute force method
dictmethod("123456789")       # Tests dictionary method
hybridmethod("Password123$")  # Tests hybrid method
```

## Performance Considerations

- **Brute Force**: Exponential time complexity, suitable only for very short passwords
- **Dictionary**: Linear time complexity, limited by wordlist size
- **Hybrid**: Polynomial time complexity, balances effectiveness and efficiency

## Wordlist Requirements

Your `wordlist.txt` should contain:
- One password per line
- Common passwords and dictionary words
- No special formatting required
- UTF-8 encoding recommended

Example wordlist content:
```
password
123456
admin
welcome
letmein
password123
```

## Known Limitations

- Brute force method is not optimized for long passwords
- Dictionary attack depends on wordlist quality
- Hybrid method uses predefined patterns only
- No multi-threading implementation for faster processing

## Future Enhancements

- Multi-threading support for faster processing
- More sophisticated pattern generation
- Support for different hash types
- Advanced statistical analysis of password patterns

