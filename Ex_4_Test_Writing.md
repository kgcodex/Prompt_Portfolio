## USer Prompt
write unit tests for the Calculator class using Python's built-in unittest module. Ensure comprehensive test coverage for all methods, including:
Basic functional tests: Verify correct output for typical inputs.
Edge cases: Test scenarios like:
Division by zero.
Factorial of 0 and 1.
Prime number checks for 0, 1, 2, and larger primes/non-primes.
Power with zero, positive, and negative exponents.
Error handling: Test that appropriate exceptions (TypeError, ValueError) are raised for invalid inputs (e.g., non-numeric inputs, negative factorial inputs).
Code:
```py
import math
class Calculator:

    """

    A simple calculator class with basic arithmetic operations and some

    more advanced mathematical functions.

    """

    def add(self, a, b):

        """Adds two numbers and returns the sum."""

        if not (isinstance(a, (int, float)) and isinstance(b, (int, float))):

            raise TypeError("Both inputs must be numbers.")

        return a + b

    def subtract(self, a, b):

        """Subtracts the second number from the first and returns the difference."""

        if not (isinstance(a, (int, float)) and isinstance(b, (int, float))):

            raise TypeError("Both inputs must be numbers.")

        return a - b

    def multiply(self, a, b):

        """Multiplies two numbers and returns the product."""

        if not (isinstance(a, (int, float)) and isinstance(b, (int, float))):

            raise TypeError("Both inputs must be numbers.")

        return a * b

    def divide(self, a, b):

        """

        Divides the first number by the second and returns the quotient.

        Raises ValueError if division by zero is attempted.

        """

        if not (isinstance(a, (int, float)) and isinstance(b, (int, float))):

            raise TypeError("Both inputs must be numbers.")

        if b == 0:

            raise ValueError("Cannot divide by zero.")

        return a / b

    def power(self, base, exponent):

        """

        Raises the base to the power of the exponent.

        Handles positive, negative, and zero exponents.

        """

        if not (isinstance(base, (int, float)) and isinstance(exponent, (int, float))):

            raise TypeError("Base and exponent must be numbers.")

        return base ** exponent

    def factorial(self, n):

        """

        Calculates the factorial of a non-negative integer.

        Raises ValueError for negative inputs or non-integers.

        """

        if not isinstance(n, int):

            raise TypeError("Input must be an integer.")

        if n < 0:

            raise ValueError("Factorial is not defined for negative numbers.")

        if n == 0:

            return 1

        result = 1

        for i in range(1, n + 1):

            result *= i

        return result

    def is_prime(self, num):

        """

        Checks if a given positive integer is a prime number.

        Returns True if prime, False otherwise.

        Handles numbers less than 2.

        """

        if not isinstance(num, int):

            raise TypeError("Input must be an integer.")

        if num < 2:

            return False

        for i in range(2, int(math.sqrt(num)) + 1):

            if num % i == 0:

                return False

        return True
```
## Claude Sonnet Response

```py
import unittest
from calculator import Calculator


class TestCalculator(unittest.TestCase):
    """Comprehensive test suite for the Calculator class."""
    
    def setUp(self):
        """Set up test fixtures before each test method."""
        self.calc = Calculator()
    
    # =============================================================================
    # ADD METHOD TESTS
    # =============================================================================
    
    def test_add_positive_numbers(self):
        """Test addition with positive numbers."""
        self.assertEqual(self.calc.add(5, 3), 8)
        self.assertEqual(self.calc.add(10, 15), 25)
    
    def test_add_negative_numbers(self):
        """Test addition with negative numbers."""
        self.assertEqual(self.calc.add(-5, -3), -8)
        self.assertEqual(self.calc.add(-10, 5), -5)
        self.assertEqual(self.calc.add(10, -5), 5)
    
    def test_add_zero(self):
        """Test addition with zero."""
        self.assertEqual(self.calc.add(0, 5), 5)
        self.assertEqual(self.calc.add(5, 0), 5)
        self.assertEqual(self.calc.add(0, 0), 0)
    
    def test_add_floats(self):
        """Test addition with floating-point numbers."""
        self.assertAlmostEqual(self.calc.add(3.5, 2.7), 6.2, places=7)
        self.assertAlmostEqual(self.calc.add(-1.5, 2.3), 0.8, places=7)
    
    def test_add_type_error(self):
        """Test that add raises TypeError for non-numeric inputs."""
        with self.assertRaises(TypeError):
            self.calc.add("5", 3)
        with self.assertRaises(TypeError):
            self.calc.add(5, "3")
        with self.assertRaises(TypeError):
            self.calc.add(None, 5)
        with self.assertRaises(TypeError):
            self.calc.add([], 5)
    
    # =============================================================================
    # SUBTRACT METHOD TESTS
    # =============================================================================
    
    def test_subtract_positive_numbers(self):
        """Test subtraction with positive numbers."""
        self.assertEqual(self.calc.subtract(10, 3), 7)
        self.assertEqual(self.calc.subtract(5, 8), -3)
    
    def test_subtract_negative_numbers(self):
        """Test subtraction with negative numbers."""
        self.assertEqual(self.calc.subtract(-5, -3), -2)
        self.assertEqual(self.calc.subtract(-5, 3), -8)
        self.assertEqual(self.calc.subtract(5, -3), 8)
    
    def test_subtract_zero(self):
        """Test subtraction with zero."""
        self.assertEqual(self.calc.subtract(5, 0), 5)
        self.assertEqual(self.calc.subtract(0, 5), -5)
        self.assertEqual(self.calc.subtract(0, 0), 0)
    
    def test_subtract_floats(self):
        """Test subtraction with floating-point numbers."""
        self.assertAlmostEqual(self.calc.subtract(5.5, 2.3), 3.2, places=7)
        self.assertAlmostEqual(self.calc.subtract(-1.5, -2.7), 1.2, places=7)
    
    def test_subtract_type_error(self):
        """Test that subtract raises TypeError for non-numeric inputs."""
        with self.assertRaises(TypeError):
            self.calc.subtract("10", 3)
        with self.assertRaises(TypeError):
            self.calc.subtract(10, "3")
        with self.assertRaises(TypeError):
            self.calc.subtract(True, 5)
    
    # =============================================================================
    # MULTIPLY METHOD TESTS
    # =============================================================================
    
    def test_multiply_positive_numbers(self):
        """Test multiplication with positive numbers."""
        self.assertEqual(self.calc.multiply(4, 3), 12)
        self.assertEqual(self.calc.multiply(7, 6), 42)
    
    def test_multiply_negative_numbers(self):
        """Test multiplication with negative numbers."""
        self.assertEqual(self.calc.multiply(-4, 3), -12)
        self.assertEqual(self.calc.multiply(4, -3), -12)
        self.assertEqual(self.calc.multiply(-4, -3), 12)
    
    def test_multiply_zero(self):
        """Test multiplication with zero."""
        self.assertEqual(self.calc.multiply(0, 5), 0)
        self.assertEqual(self.calc.multiply(5, 0), 0)
        self.assertEqual(self.calc.multiply(0, 0), 0)
    
    def test_multiply_floats(self):
        """Test multiplication with floating-point numbers."""
        self.assertAlmostEqual(self.calc.multiply(2.5, 4.0), 10.0, places=7)
        self.assertAlmostEqual(self.calc.multiply(-1.5, 2.5), -3.75, places=7)
    
    def test_multiply_type_error(self):
        """Test that multiply raises TypeError for non-numeric inputs."""
        with self.assertRaises(TypeError):
            self.calc.multiply("4", 3)
        with self.assertRaises(TypeError):
            self.calc.multiply(4, "3")
        with self.assertRaises(TypeError):
            self.calc.multiply(4, [])
    
    # =============================================================================
    # DIVIDE METHOD TESTS
    # =============================================================================
    
    def test_divide_positive_numbers(self):
        """Test division with positive numbers."""
        self.assertEqual(self.calc.divide(10, 2), 5.0)
        self.assertEqual(self.calc.divide(15, 3), 5.0)
        self.assertAlmostEqual(self.calc.divide(7, 3), 2.333333333333333, places=7)
    
    def test_divide_negative_numbers(self):
        """Test division with negative numbers."""
        self.assertEqual(self.calc.divide(-10, 2), -5.0)
        self.assertEqual(self.calc.divide(10, -2), -5.0)
        self.assertEqual(self.calc.divide(-10, -2), 5.0)
    
    def test_divide_floats(self):
        """Test division with floating-point numbers."""
        self.assertAlmostEqual(self.calc.divide(7.5, 2.5), 3.0, places=7)
        self.assertAlmostEqual(self.calc.divide(-9.6, 3.2), -3.0, places=7)
    
    def test_divide_by_zero(self):
        """Test that division by zero raises ValueError."""
        with self.assertRaises(ValueError) as context:
            self.calc.divide(10, 0)
        self.assertIn("Cannot divide by zero", str(context.exception))
        
        with self.assertRaises(ValueError):
            self.calc.divide(-5, 0)
    
    def test_divide_type_error(self):
        """Test that divide raises TypeError for non-numeric inputs."""
        with self.assertRaises(TypeError):
            self.calc.divide("10", 2)
        with self.assertRaises(TypeError):
            self.calc.divide(10, "2")
        with self.assertRaises(TypeError):
            self.calc.divide(None, 5)
    
    # =============================================================================
    # POWER METHOD TESTS
    # =============================================================================
    
    def test_power_positive_exponent(self):
        """Test power with positive exponents."""
        self.assertEqual(self.calc.power(2, 3), 8)
        self.assertEqual(self.calc.power(5, 2), 25)
        self.assertEqual(self.calc.power(10, 1), 10)
    
    def test_power_zero_exponent(self):
        """Test power with zero exponent."""
        self.assertEqual(self.calc.power(5, 0), 1)
        self.assertEqual(self.calc.power(100, 0), 1)
        self.assertEqual(self.calc.power(-3, 0), 1)
    
    def test_power_negative_exponent(self):
        """Test power with negative exponents."""
        self.assertEqual(self.calc.power(2, -1), 0.5)
        self.assertEqual(self.calc.power(4, -2), 0.0625)
        self.assertAlmostEqual(self.calc.power(3, -1), 0.3333333333333333, places=7)
    
    def test_power_float_base_and_exponent(self):
        """Test power with floating-point base and exponent."""
        self.assertAlmostEqual(self.calc.power(2.5, 2), 6.25, places=7)
        self.assertAlmostEqual(self.calc.power(4, 0.5), 2.0, places=7)
        self.assertAlmostEqual(self.calc.power(8, 1/3), 2.0, places=7)
    
    def test_power_negative_base(self):
        """Test power with negative base."""
        self.assertEqual(self.calc.power(-2, 2), 4)
        self.assertEqual(self.calc.power(-2, 3), -8)
        self.assertEqual(self.calc.power(-3, 0), 1)
    
    def test_power_type_error(self):
        """Test that power raises TypeError for non-numeric inputs."""
        with self.assertRaises(TypeError):
            self.calc.power("2", 3)
        with self.assertRaises(TypeError):
            self.calc.power(2, "3")
        with self.assertRaises(TypeError):
            self.calc.power([], 2)
        with self.assertRaises(TypeError):
            self.calc.power(2, None)
    
    # =============================================================================
    # FACTORIAL METHOD TESTS
    # =============================================================================
    
    def test_factorial_basic_cases(self):
        """Test factorial for basic cases."""
        self.assertEqual(self.calc.factorial(0), 1)
        self.assertEqual(self.calc.factorial(1), 1)
        self.assertEqual(self.calc.factorial(5), 120)
        self.assertEqual(self.calc.factorial(6), 720)
    
    def test_factorial_larger_numbers(self):
        """Test factorial for larger numbers."""
        self.assertEqual(self.calc.factorial(10), 3628800)
        self.assertEqual(self.calc.factorial(12), 479001600)
    
    def test_factorial_negative_input(self):
        """Test that factorial raises ValueError for negative inputs."""
        with self.assertRaises(ValueError) as context:
            self.calc.factorial(-1)
        self.assertIn("Factorial is not defined for negative numbers", str(context.exception))
        
        with self.assertRaises(ValueError):
            self.calc.factorial(-5)
    
    def test_factorial_non_integer_input(self):
        """Test that factorial raises TypeError for non-integer inputs."""
        with self.assertRaises(TypeError) as context:
            self.calc.factorial(3.5)
        self.assertIn("Input must be an integer", str(context.exception))
        
        with self.assertRaises(TypeError):
            self.calc.factorial("5")
        with self.assertRaises(TypeError):
            self.calc.factorial(None)
        with self.assertRaises(TypeError):
            self.calc.factorial([])
    
    # =============================================================================
    # IS_PRIME METHOD TESTS
    # =============================================================================
    
    def test_is_prime_basic_cases(self):
        """Test prime check for basic cases."""
        self.assertFalse(self.calc.is_prime(0))
        self.assertFalse(self.calc.is_prime(1))
        self.assertTrue(self.calc.is_prime(2))
        self.assertTrue(self.calc.is_prime(3))
    
    def test_is_prime_small_primes(self):
        """Test prime check for small prime numbers."""
        small_primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31]
        for prime in small_primes:
            with self.subTest(prime=prime):
                self.assertTrue(self.calc.is_prime(prime))
    
    def test_is_prime_composite_numbers(self):
        """Test prime check for composite numbers."""
        composite_numbers = [4, 6, 8, 9, 10, 12, 14, 15, 16, 18, 20, 21, 25, 27, 100]
        for composite in composite_numbers:
            with self.subTest(composite=composite):
                self.assertFalse(self.calc.is_prime(composite))
    
    def test_is_prime_larger_numbers(self):
        """Test prime check for larger numbers."""
        self.assertTrue(self.calc.is_prime(97))  # Large prime
        self.assertTrue(self.calc.is_prime(101))  # Large prime
        self.assertFalse(self.calc.is_prime(100))  # Large composite
        self.assertFalse(self.calc.is_prime(99))  # Large composite
    
    def test_is_prime_negative_numbers(self):
        """Test prime check for negative numbers."""
        self.assertFalse(self.calc.is_prime(-1))
        self.assertFalse(self.calc.is_prime(-2))
        self.assertFalse(self.calc.is_prime(-5))
    
    def test_is_prime_type_error(self):
        """Test that is_prime raises TypeError for non-integer inputs."""
        with self.assertRaises(TypeError) as context:
            self.calc.is_prime(3.5)
        self.assertIn("Input must be an integer", str(context.exception))
        
        with self.assertRaises(TypeError):
            self.calc.is_prime("5")
        with self.assertRaises(TypeError):
            self.calc.is_prime(None)
        with self.assertRaises(TypeError):
            self.calc.is_prime([])
        with self.assertRaises(TypeError):
            self.calc.is_prime(5.0)  # Float that looks like int


class TestCalculatorIntegration(unittest.TestCase):
    """Integration tests combining multiple Calculator methods."""
    
    def setUp(self):
        """Set up test fixtures before each test method."""
        self.calc = Calculator()
    
    def test_complex_calculations(self):
        """Test complex calculations using multiple methods."""
        # (5 + 3) * 2 = 16
        result1 = self.calc.multiply(self.calc.add(5, 3), 2)
        self.assertEqual(result1, 16)
        
        # 2^3 + 5! = 8 + 120 = 128
        result2 = self.calc.add(self.calc.power(2, 3), self.calc.factorial(5))
        self.assertEqual(result2, 128)
        
        # (10 - 4) / 2 = 3
        result3 = self.calc.divide(self.calc.subtract(10, 4), 2)
        self.assertEqual(result3, 3.0)
    
    def test_edge_case_combinations(self):
        """Test edge cases when combining methods."""
        # 0! + 1! = 1 + 1 = 2
        result1 = self.calc.add(self.calc.factorial(0), self.calc.factorial(1))
        self.assertEqual(result1, 2)
        
        # 2^0 * 5 = 1 * 5 = 5
        result2 = self.calc.multiply(self.calc.power(2, 0), 5)
        self.assertEqual(result2, 5)


if __name__ == '__main__':
    # Run the tests with verbose output
    unittest.main(verbosity=2)
```
