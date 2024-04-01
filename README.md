- 👋 Hi, I’m @XPRO3
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
XPRO3/XPRO3 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import hashlib
import time

def mine(block_number, transactions, previous_hash, prefix_zeros):
    prefix_str = '0'*prefix_zeros
    nonce = 0
    while True:
        text = f"{block_number}{transactions}{previous_hash}{nonce}".encode('utf-8')
        new_hash = hashlib.sha256(text).hexdigest()
        if new_hash.startswith(prefix_str):
            print(f"Successfully mined bitcoins with nonce value:{nonce}")
            print(f"Hash is: {new_hash}")
            break
        nonce += 1
    return new_hash

# Example parameters (simplified)
block_number = 1
transactions = 'JohnDoe -> JaneDoe -> 20 BTC'
previous_hash = 'previous_block_hash'
difficulty = 4  # Number of prefix zeros

start_time = time.time()
print("Mining started...")
new_hash = mine(block_number, transactions, previous_hash, difficulty)
end_time = time.time()
print(f"Mining completed in {end_time - start_time} seconds")
