import sys
import time


def find_factors(number):
    '''Finds the factors of a number.
    Args:
        number: Input integer.
    Returns:
        A tuple of two factors if the number is not prime.
        None if the number is prime.
    '''
    for i in range(2, int(number ** 0.5) + 1):
        if number % i == 0:
            return (i, number // i)
    return None


if __name__ == "__main__":

    '''Reads the input file.
    '''
    if len(sys.argv) != 2:
        print("Usage: factors <file>")
        exit()

    input_file = sys.argv[1]

    try:
        with open(input_file, 'r') as file:
            lines = file.readlines()
    except FileNotFoundError:
        print("File not found")
        exit()

    start_time = time.time()

    '''Loops over each line (which should contain one natural number per line)
    and calls find_factors on each number.
    If find_factors returns a tuple of factors,
    it prints the factorization in the desired format.
    '''
    for line in lines:
        number = int(line.strip())
        factors = find_factors(number)
        if factors:
            print(f"{number}={factors[0]}*{factors[1]}")

        '''If the elapsed time exceeds 5 seconds,
        the program exits with an error message.
        '''
        if time.time() - start_time > 5:
            print("Time limit exceeded")
            exit()
