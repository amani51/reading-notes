# Class-16
## Cryptography
### Reading
##### Encryption, Decryption & Hacking
- **Encryption** is the method by which information is converted into secret code that hides the information's true meaning. The science of encrypting and decrypting information is called cryptography.
![](https://www.cisco.com/c/en/us/products/security/encryption-explained/jcr:content/Grid/category_atl/layout-category-atl/blade_493679486/bladeContents/quarterhalfquarter/QHQ-Half-2/image/image.img.png/1634629737483.png)
- **Decryption** is the process of transforming data that has been rendered unreadable through encryption back to its unencrypted form.
![](https://usemynotes.com/wp-content/uploads/2021/03/what-is-decryption.jpg)
- **Hacking** is the act of identifying and then exploiting weaknesses in a computer system or network, usually to gain unauthorized access to personal or organizational data.
![](https://media.tenor.com/-SV9TjUGabMAAAAC/hacker-python.gif)
- **Caesar cipher** it is one of the simplest and most widely known encryption techniques. It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet. For example, with a left shift of 3, D would be replaced by A, E would become B, and so on. The method is named after Julius Caesar, who used it in his private correspondence.
![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/Caesar_cipher_left_shift_of_3.svg/1200px-Caesar_cipher_left_shift_of_3.svg.png)
- **Cryptography** is technique of securing information and communications through use of codes so that only those person for whom the information is intended can understand it and process it. Thus preventing unauthorized access to information. The prefix “crypt” means “hidden” and suffix graphy means “writing”.
![](https://cms-media.bartleby.com/wp-content/uploads/sites/2/2021/09/24172245/Cryptography-1-1.png)

- **Substitution Cipher** encrypt the plaintext by swapping each letter or symbol in the plaintext by a different symbol as directed by the key.
- **PYTHON Example**:
    ```python  
    import string
    # A list containing all characters
    all_letters= string.ascii_letters 
    dict1 = {}
    key = 4
    for i in range(len(all_letters)):
        dict1[all_letters[i]] = all_letters[(i+key)%len(all_letters)]
    plain_txt= "I am studying Data Encryption"
    cipher_txt=[]
    # loop to generate ciphertext
    for char in plain_txt:
        if char in all_letters:
            temp = dict1[char]
            cipher_txt.append(temp)
        else:
            temp =char
            cipher_txt.append(temp)         
    cipher_txt= "".join(cipher_txt)
    print("Cipher Text is: ",cipher_txt)

    dict2 = {}    
    for i in range(len(all_letters)):
        dict2[all_letters[i]] = all_letters[(i-key)%(len(all_letters))]     
    # loop to recover plain text
    decrypt_txt = []
    for char in cipher_txt:
        if char in all_letters:
            temp = dict2[char]
            decrypt_txt.append(temp)
        else:
            temp = char
            decrypt_txt.append(temp)        
    decrypt_txt = "".join(decrypt_txt)
    print("Recovered plain text :", decrypt_txt)
    #output
    #Cipher Text is:  M eq wxyhCmrk Hexe IrgvCtxmsr
    #Recovered plain text : I am studying Data Encryption
    ```