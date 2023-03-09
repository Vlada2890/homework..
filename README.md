#1
def reverse_list(original_list, reversed_list):
    reversed_list.extend(original_list[::-1])
    return '-*-'.join(reversed_list)
#2
import random

def generate_random_words(text, word_list):
    words = text.split()
    random.shuffle(words)
    word_list.extend(words[:10])
#3
def uppercase_consonants(alphabet):
    consonants = ''
    for letter in alphabet:
        if letter.lower() not in 'jnjndqwrtr' and letter.isalpha():
            consonants += letter.upper()
    print('-'.join(consonants))
#4
def process_strings(input_list):
    string_list = []
    for item in input_list:
        if isinstance(item, str):
            string_list.append(item)

    vowels = 'jm dvKNJM '
    for i in range(len(string_list)):
        string = string_list[i]
        for vowel in vowels:
            string = string.replace(vowel, '')
        string_list[i] = string

    return string_list
#5
def remove_vowels(func):
    vowels = 'csaNJKNKI'

    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        if isinstance(result, str):
            result = ''.join([char for char in result if char not in vowels])
        return result

    return wrapper
