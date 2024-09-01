python
def encrypt(text, shift):
    encrypted_text = ""
    
    for char in text:
        if char.isalpha():
            shift_amount = shift % 26  # Handle shifts greater than 26
            ascii_offset = 65 if char.isupper() else 97
            encrypted_char = chr((ord(char) - ascii_offset + shift_amount) % 26 + ascii_offset)
            encrypted_text += encrypted_char
        else:
            encrypted_text += char  # Non-alphabet characters are not shifted

    return encrypted_text

def decrypt(text, shift):
    return encrypt(text, -shift)

def main():
    print("Caesar Cipher Encryption/Decryption")
    mode = input("Enter 'E' to encrypt or 'D' to decrypt: ").strip().upper()
    message = input("Enter the message: ")
    shift = int(input("Enter the shift value: "))

    if mode == 'E':
        result = encrypt(message, shift)
        print(f"Encrypted message: {result}")
    elif mode == 'D':
        result = decrypt(message, shift)
        print(f"Decrypted message: {result}")
    else:
        print("Invalid mode selected. Please choose 'E' for encryption or 'D' for decryption.")

if __name__ == "__main__":
    main()
