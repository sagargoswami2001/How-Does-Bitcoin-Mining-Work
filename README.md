<h1 align="center"> How Does Bitcoin Mining Work? </h1>

## **Introduction**
In today's digital world, it is essential for one to be updated with the current trends of the world, and due to its extremely volatile nature and high-profit returns, people are drawn toward bitcoin. bitcoin is arguably the first cryptocurrency and major implementation of blockchain technology, you may or may not know about them so in this article, we will be covering what actually is the bitcoin and how can people earn it, which is done by mining. We have also added a demonstration of how to mine a dummy block of cryptocurrency using Python. Let's get into this.

## **What is Bitcoin?**
Bitcoin(₿) is the first decentralized digital currency created in January 2009. Bitcoin was created by **Satoshi Nakamoto**. The word bitcoin first originated from a white paper published on 31 October 2008. It is a compound of the words "bit" and "coin" Bitcoin uses **peer-to-peer** technology to operate with no central authority or banks. Managing transactions and the issuing of bitcoins is carried out collectively by the whole peer-to-peer network of bitcoin. Its implementation was released as open-source for it can be seen and accessed by anyone.

Bitcoins are created as a reward for a process known as Bitcoin mining. Bitcoin is widely accepted for currencies, products, and services. Bitcoin has been censured for its use in illegal transactions, the large amount of electricity used by mining, and a purely peer-to-peer version of electronic cash would allow online payments to be sent directly from one party to another without going through a central authority or financial institution.

## **What is Bitcoin Mining?**
Bitcoin mining is a highly complex computing process that uses complicated computer code to create a secure cryptographic system, as well as the process by which new bitcoin enters into circulation. mining is a record-keeping service done through the use of a bitcoin mining rig's processing power. It involves very large, decentralized networks of computers connected through peer-to-peer technology throughout the world that verify and secure blockchains. Bitcoin mining takes over the Bitcoin database, which is called the blockchain.

Crypto miners compete to be the first ones to verify Crypto transactions and earn rewards paid in Cryptocurrencies for their efforts. Crypto miners need to first invest in computer equipment that is specialized for mining **(usually high-end GPUs among other powerful PC components)**, and typically require access to a low-cost energy source.

**Things to know:-**
1. Through mining, you can earn cryptocurrency without the need to deposit money for it.
2. Bitcoin miners receive bitcoin as a reward for completing "blocks" of verified transactions, which are added to the then added to Bitcoin's peer-to-peer network.
3. Mining rewards are given to the miner who first discovers a solution to a complex mathematical hash puzzle, and the probability of a participant will be the one to discover the solution is related to the portion of the network's total mining power.
4. You need a graphical processing unit **(GPU)** or an application-specific integrated circuit **(ASIC)** in order to set up a mining facility.

## **The Mining Process**
Mining is the process of guessing a nonce that generates a hash with the first x number of zeros.

Bitcoin mining these miners get the reward in 2009 if you mine a block you will get 50 bitcoins every four years, the reward is halved so in 2020 the reward is 6.25. In 2024, it will be half of that.

As stated earlier, the computer needed for mining must have the tremendous processing power. Bitcoin mining calls for speed. The faster the computer system, the more a person would be able to exploit and increase his or her revenue. If the computer is slow, they may lose to other miners. A robust graphics processor (GPU) or video card is essential for bitcoin mining. Next, the person would need to create a Bitcoin wallet and join a mining pool - a group of miners who combine their resources to increase their mining potential. Minors from the same pool distribute the benefit amongst themselves.

## **What is Bitcoin a Wallet?**
A bitcoin wallet is a digital program to send and receive bitcoins, store Bitcoins, and monitor Bitcoin balances.

Very much like you want an email program like Outlook or Gmail to deal with your messages, you really want a bitcoin wallet to deal with your bitcoins.

Wallets screen bitcoin addresses at the blockchain and replace their very own balance with every transaction.

## Here is a demonstration of mining a dummy block using python:-
Python Program to Bitcoin Mining Process By Sagar Goswami.


```py
from hashlib import sha256  # SHA256 is a Cryptographic Hash Function    
MAX_NONCE = 1000000000000    
#The "nonce" in a bitcoin block is of size 32-bit (4-byte)    
# field whose value is adjusted by cryptocurrencies miners    
# so that the hash of the block remains less than or equal to the current target of the network.    
# Other Fields need not be changed as they have a defined meaning.    
    
def SHA256(text):    
    return sha256(text.encode("ascii")).hexdigest()    
    
def mine(block_number, transactions, previous_hash, prefix_zeros):    
    prefix_str = '0'*prefix_zeros    
    for nonce in range(MAX_NONCE):    
        text = str(block_number) + transactions + previous_hash + str(nonce)    
        new_hash = SHA256(text)    
        if new_hash.startswith(prefix_str):    
            print(f"\nHooray! Successfully Mined Bitcoins with Nonce Value: {nonce}")    
            return new_hash    
    
    raise BaseException(f"Couldn't find Correct has After Trying {MAX_NONCE} Times")    
    
if __name__=='__main__':    
    transactions = '''  
    Dhaval->Bhavin->20  
    Mando->Cara->45  
    '''    
    
    difficulty = 5 # Try Changing This to Higher Number    
                        #and You Will See It Will Take More Time for Mining as Difficulty Increases.    
                        #Beware to not Use a Large no.    
                        #Reference: on NVIDIA GeForce GTX 1050Ti Oc GPU it takes >2 min    
                        # Warning: do not use values Above 7    
    
    import time    
    start = time.time()    
    print("\nStart Mining...")    
    new_hash = mine(5, transactions, '0000000xa036944e29568d0cff17edbe038f81208fecf9a66be9a2b8321c6ec7', difficulty)    
    total_time = str((time.time() - start))    
    print(f"End Mining. Mining Took: {total_time} Seconds")    
    print(new_hash)
```

**OUTPUT**
