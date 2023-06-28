#!/usr/bin/python3

import sys
import random
import time


def is_prime_number(number, k=20):
    '''
    Checks if a number is prime.
    Args:
        number: Input integer.
        k: Number of iterations for the Miller-Rabin primality test.
    Returns:
        True if the number is prime, False otherwise.
    '''
    if number == 2 or number == 3:
        return True
    if number < 2 or number % 2 == 0:
        return False

    d = number - 1
    r = 0
    while d % 2 == 0:
        d //= 2
        r += 1

    for _ in range(k):
        a = random.randint(2, number - 2)
        x = pow(a, d, number)
        if x == 1 or x == number - 1:
            continue
        for _ in range(r - 1):
            x = pow(x, 2, number)
            if x == number - 1:
                break
        else:
            return False

    return True


if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("Usage: rsa <file>")
        exit()

    input_file = sys.argv[1]

    try:
        with open(input_file, 'r') as file:
            lines = file.readlines()
    except FileNotFoundError:
        print("File not found")
        exit()

    start_time = time.time()

    number = int(lines[0].strip())

    for i in range(2, number // 2):
        if number % i == 0 and is_prime_number(i) and is_prime_number(number // i):
            print(f"{number}={i}*{number // i}")
            break

        if time.time() - start_time > 5:
            print("Time limit exceeded")
            exit()
