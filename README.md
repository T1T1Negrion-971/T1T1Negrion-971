# Fonction de cryptage ROT13
def cryptage_rot13(message):
    """
    Crypte le message en utilisant le chiffrement ROT13.

    Args:
        message (str): Le message à crypter.

    Returns:
        str: Le message crypté.
    """
    resultat = ""
    for char in message:
        if char.isalpha():
            decalage = 13
            if char.islower():
                base = ord('a')
            else:
                base = ord('A')
            resultat += chr((ord(char) - base + decalage) % 26 + base)
        else:
            resultat += char
    return resultat

# Fonction de cryptage Code de César
def cryptage_cesar(message, decalage):
    """
    Crypte le message en utilisant le chiffrement par décalage (Code de César).

    Args:
        message (str): Le message à crypter.
        decalage (int): Le nombre de positions à décaler.

    Returns:
        str: Le message crypté.
    """
    resultat = ""
    for char in message:
        if char.isalpha():
            if char.islower():
                base = ord('a')
            else:
                base = ord('A')
            resultat += chr((ord(char) - base + decalage) % 26 + base)
        else:
            resultat += char
    return resultat

# Fonction de cryptage Code de Vigenère
def cryptage_vigenere(message, cle):
    """
    Crypte le message en utilisant le chiffrement de Vigenère.

    Args:
        message (str): Le message à crypter.
        cle (str): La clé de chiffrement.

    Returns:
        str: Le message crypté.
    """
    resultat = ""
    i = 0
    for char in message:
        if char.isalpha():
            decalage = ord(cle[i % len(cle)].lower()) - ord('a')
            resultat += cryptage_cesar(char, decalage)
            i += 1
        else:
            resultat += char
    return resultat

# Fonction de cryptage Carré de Polybe
def cryptage_polybe(message):
    """
    Crypte le message en utilisant le chiffrement de Carré de Polybe.

    Args:
        message (str): Le message à crypter.

    Returns:
        str: Le message crypté.
    """
    carre_polybe = {
        'A': '11', 'B': '12', 'C': '13', 'D': '14', 'E': '15',
        'F': '21', 'G': '22', 'H': '23', 'I': '24', 'J': '24',
        'K': '25', 'L': '31', 'M': '32', 'N': '33', 'O': '34',
        'P': '35', 'Q': '41', 'R': '42', 'S': '43', 'T': '44',
        'U': '45', 'V': '51', 'W': '52', 'X': '53', 'Y': '54', 'Z': '55'
    }
    resultat = ""
    for char in message:
        if char.isalpha():
            char = char.upper()
            resultat += carre_polybe[char] + ' '
        else:
            resultat += char
    return resultat

# Exemple d'utilisation
message = "Hello World!"
cle_vigenere = "KEY"
print("Message original:", message)
print("ROT13:", cryptage_rot13(message))
print("Code de César (décalage de 3):", cryptage_cesar(message, 3))
print("Code de Vigenère (clé 'KEY'):", cryptage_vigenere(message, cle_vigenere))
print("Carré de Polybe:", cryptage_polybe(message))


<!---
T1T1Negrion-971/T1T1Negrion-971 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
