# **Cryptography Challenges Writeup**

Welcome to the cryptography challenges! Below are the tasks, their descriptions, and solutions.

---

## **Task 1: "Mysterious Base"**

- **Description**: You’ve intercepted a secret transmission from an unknown source. However, it seems to be encoded in a strange base system. Can you figure out which one?
- **Hint**: Look at the length of the characters for clues about the encoding type.
- **Challenge**: The message is encoded using **Base32**.
- **Encoded Message**: `KNSWG5LSNFXGK5DTPNBGC43FGMZF6RDFMNXWIZLEPU======`
- **Solution**: The flag is: `Securinets{Base32_Decoded}`

---

## **Task 2: "Double Trouble"**

- **Description**: You stumble upon a message hidden in two layers of encoding. Only by decoding both can you reveal the hidden flag.
- **Hint**: Start with one, and see where it leads.
- **Encoded Message**: `NTM2NTYzNzU3MjY5NmU2NTc0NzM3YjQ0NmY3NTYyNmM2NTVmNDU2ZTYzNmY2NDY1NjQ3ZA==`
- **Solution**: After decoding, the flag is: `Securinets{Double_Encoded}`

---

## **Task 3: "Rotating Secrets"**

- **Description**: The message you found appears to have been shifted, but by how much? Rotate the message to unlock the hidden flag.
- **Hint**: What happens if you rotate by 13?
- **Encoded Message**: `Frphevargf{Ebggl_Fgngr}`
- **Solution**: After applying ROT13, the flag is: `Securinets{Rot13_State}`

---

## **Task 4: "Curious Code"**

- **Description**: An encoded message was intercepted, but something about it seems... encoded twice. Decoding it might take more than one step.
- **Hint**: Sometimes you need to decode twice to uncover the truth.
- **Encoded Message**: `%53%65%63%75%72%69%6E%65%74%73%7B%55%52%4C%5F%54%77%69%63%65%7D`
- **Solution**: The flag is: `Securinets{URL_Twice}`

---

## **Task 5: "Lost in Translation"**

- **Description**: The message seems to have been written in dots and dashes. Can you translate this forgotten code to find the flag?
- **Hint**: Look to the stars (or maybe Morse).
- **Challenge**: The message is encoded in **Morse Code**.
- **Encoded Message**: `-- --- .-. ... .`
- **Solution**: After translating Morse code, the flag is: `Securinets{MORSE}`

---

## **Task 6: "Fibonacci Cipher"**

- **Description**: A hidden message has been encoded using a sequence inspired by Fibonacci numbers. Can you figure out the mathematical pattern to unlock the flag?
- **Hint**: The first two numbers in the sequence are crucial. From there, each number is the sum of the previous two.
- **Challenge**: The encoding uses a Fibonacci-based shifting pattern. Each character in the plaintext is shifted by a value in the Fibonacci sequence.
- **Encoded Text**: `Sfdwunvroa{QwabzznmdXhnkd}`
- **Solution**: After reversing the Fibonacci shifts, the flag is: `Securinets{FibonacciShift}`

---

## **Task 7: "Prime Numbers Magic"**

- **Description**: You’ve found a message that seems to be based on a sequence of prime numbers. Use your knowledge of primes to decrypt the flag.
- **Hint**: Prime numbers guide how the letters are encoded. Identify the sequence and decrypt accordingly.
- **Encoded Text**: `Uhhbcvexqv{AgzhfZqxyo}`
- **Solution**: The flag is: `Securinets{PrimeShift}`

---

# **Decryption Scripts**

Here are the Python scripts to decode messages encoded using **Prime Numbers** and **Fibonacci Sequences**.

---

## **Prime Number Decryption Script**

This script decodes a message that was encoded using a sequence of prime numbers.

```python
# Function to generate the first N prime numbers
def generate_primes(n):
    primes = []
    candidate = 2
    while len(primes) < n:
        for p in primes:
            if candidate % p == 0:
                break
        else:
            primes.append(candidate)
        candidate += 1
    return primes

# Function to decode a single character with a backward shift
def decode_prime_character(encoded_char, shift):
    if encoded_char.isupper():
        base = ord('A')
    elif encoded_char.islower():
        base = ord('a')
    else:
        return encoded_char  # Non-alphabetic characters remain unchanged
    # Apply the backward shift and wrap within the alphabet
    shifted_char = (ord(encoded_char) - base - shift) % 26 + base
    return chr(shifted_char)

# Function to decode text using a prime number sequence
def decode_with_primes(encoded_text):
    # Generate enough prime numbers for the length of the text
    primes = generate_primes(len(encoded_text))
    # Decode the text
    decoded_text = ''.join(
        decode_prime_character(char, shift) for char, shift in zip(encoded_text, primes)
    )
    return decoded_text

# Input encoded text
encoded_text = 'Uhhbcvexqv{AgzhfZqxyo}'  # Example encoded text

# Decode the text
decoded_text = decode_with_primes(encoded_text)

# Output the result
print("Decoded Text:", decoded_text)
```

## **Fibonacci Sequence Decryption Script**

This script decodes a message that was encoded using a Fibonacci Sequence.

```python
# Define the Fibonacci sequence
fibonacci_sequence = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]

# Function to decode a single character with a backward shift
def decode_character(encoded_char, shift):
    if encoded_char.isupper():
        base = ord('A')
    elif encoded_char.islower():
        base = ord('a')
    else:
        return encoded_char  # Non-alphabetic characters remain unchanged
    # Apply the backward shift and wrap within the alphabet
    shifted_char = (ord(encoded_char) - base - shift) % 26 + base
    return chr(shifted_char)

# Function to decode text using the Fibonacci sequence
def decode_with_fibonacci(encoded_text):
    # Extend the Fibonacci sequence to match the length of the encoded text
    extended_fib_sequence = fibonacci_sequence[:]
    while len(extended_fib_sequence) < len(encoded_text):
        extended_fib_sequence.append(
            extended_fib_sequence[-1] + extended_fib_sequence[-2]
        )
    # Decode the text
    decoded_text = ''.join(
        decode_character(char, shift)
        for char, shift in zip(encoded_text, extended_fib_sequence)
    )
    return decoded_text

# Input encoded text
encoded_text = 'Sfdwunvroa{QwabzznmdXhnkd}'  # Example encoded text

# Decode the text
decoded_text = decode_with_fibonacci(encoded_text)

# Output the result
print("Decoded Text:", decoded_text)

```

# Python Script to Decode Long Integer Using `long_to_bytes`

This Python script uses `long_to_bytes` from the `Crypto.Util.number` module to convert a long integer into a byte string 

### Python Script:

```python
from Crypto.Util.number import long_to_bytes

# Encoded long number
encoded_long = 841208738393658017880050617361623294037146533629618931162030257875366301740891511056310975897709368607471101321883448701
# Convert the long number to bytes using long_to_bytes
byte_str = long_to_bytes(encoded_long)

# Print the resulting byte string
print("Byte String:", byte_str)
