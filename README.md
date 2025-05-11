
---

# User Manual

**Program Name**: Key Exchange Protocol Based on Diffie-Hellman and PAKE

**Author**: AlcyoneusT

**Version**: 2.0

---

## 1. Program Overview

This program implements a basic **Diffie-Hellman key exchange protocol**, enhanced with **Password-Authenticated Key Exchange (PAKE)** functionality.
In Version 2.0, the program further introduces a **cryptographically secure random salt** for password hashing and replaces simple hashing with **HMAC-SHA256** for generating **Message Authentication Codes (MACs)**.
Users can securely establish a shared secret over insecure networks, authenticate it using a password, and protect message integrity against tampering.

---

## 2. System Requirements

* **Python Version**: 3.x
* **Required Libraries**:

  * `hashlib` (standard library)
  * `hmac` (standard library)
  * `os` (standard library)
  * `random` (standard library)

---

## 3. Program Structure

The program consists of the following components:

1. **Diffie-Hellman Key Exchange**: Establishes an initial shared secret between two parties.
2. **Password-Authenticated Key Exchange (PAKE)**: Strengthens the shared secret using a password and a random salt.
3. **Message Authentication Code (MAC)**: Ensures integrity and authenticity of transmitted messages using HMAC-SHA256.

---

## 4. How to Run the Program

### Step 1: Download or Clone the Program

Save the Python script onto your local machine. Ensure your environment is set up with Python 3.x.

### Step 2: Execute the Program

Navigate to the program’s directory and run the script:

```bash
python your_program_name.py
```

(Replace `your_program_name.py` with the actual filename.)

### Step 3: Shared Password Handling

At runtime, the program uses a predefined shared password within the script.
(Optional: You can modify the code to accept user input for the password if needed.)

### Step 4: View the Results

Upon successful execution, the program will output:

1. **Shared Secret**: The Diffie-Hellman derived shared secret.
2. **Random Salt**: A newly generated salt used during PAKE.
3. **Final Authenticated Secret**: A hash derived from the shared secret and password hash.
4. **Generated MAC**: The HMAC-SHA256 MAC for a transmitted message.
5. **Message Verification Result**: Confirming the message has not been tampered with.

Example output:

```plaintext
Shared secret successfully established.
Theo's shared secret: 1
Knew's shared secret: 1

Password-authenticated shared secret successfully established.
Random salt used (hex): 1d88a5b747ee9d515dafea62b0a1d850
Theo's final secret: e7f6c011776e8db7cd330b54174fd76f7d0216b612387a5ffcfb81e6f0919683
Knew's final secret: e7f6c011776e8db7cd330b54174fd76f7d0216b612387a5ffcfb81e6f0919683

Generated MAC: 729a804981a5cd8efebbb437bc4df7c7f33c24d97e990f81ca2197b942cc5038
Message is verified and intact.
```

---

## 5. Result Explanation

* **Shared Secret**: The initial secret calculated via Diffie-Hellman. Both parties should have the same value.
* **Random Salt**: A random value used to salt the password before hashing, preventing precomputed attacks.
* **Final Authenticated Secret**: Combines the shared secret and password hash, finalizing mutual authentication.
* **Generated MAC**: The HMAC-SHA256 signature of the transmitted message using the authenticated secret as the key.
* **Message Verification**: Confirms the received message has not been modified during transmission.

---

## 6. Frequently Asked Questions (FAQ)

### 1. What happens if the shared password is wrong?

The final authenticated secrets will not match, causing message verification to fail.

### 2. Can I provide my own prime number (`p`) and generator (`g`)?

Yes. You can manually edit `p` and `g` values in the script.
For real applications, you must use primes at least 2048 bits long.

### 3. Is the generated salt fixed?

No. A new random salt is generated each time the program runs, enhancing security.

---

## 7. Important Notes

* **Use Strong Passwords**: Weak passwords can compromise security even if key exchange is secure.
* **Randomness Matters**: The random salt adds vital security. Never reuse salts unless absolutely necessary.
* **MAC Protection**: Always verify MACs before trusting any received message.
* **Key Management**: Treat generated keys as sensitive materials. Do not expose them.

---

## 8. Future Enhancements

Potential improvements could include:

* Adopting standard Diffie-Hellman groups from RFC 3526 (e.g., 2048-bit MODP Group).
* Supporting dynamic user input for passwords and messages.
* Adding AES encryption using the authenticated secret as the symmetric key.
* Implementing advanced PAKE protocols like SPAKE2 or OPAQUE for stronger password authentication.

---

## 9. Version History

**Version 1.1**:

* Initial documentation updates.

**Version 1.2**:

* Improved documentation structure and content.

**Version 1.3**:

* Added simple MAC generation and verification using SHA-256 (not HMAC).

**Version 2.0**:

* Introduced random salt generation (`os.urandom`).
* Switched MAC generation to HMAC-SHA256 for robust message authentication.
* Enhanced program security and modularity.

---

## 10. Contact Information

For any questions, feedback, or contributions, please contact the author: **AlcyoneusT**.

---

**Thank you for using this program!**

---