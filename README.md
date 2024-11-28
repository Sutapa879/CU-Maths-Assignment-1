# CU-Maths-Assignment-1
# Choose the appropriate distribution function
    probabilities = []
    if dist_name == "geometric":
        p = params.get("p")
        if p is None or not (0 < p <= 1):
            raise ValueError("For geometric distribution, 'p' must be provided and be in the range (0, 1].")
        probabilities = [geometric(p, x) for x in vals]
    elif dist_name == "binomial":
        n = params.get("n")
        p = params.get("p")
        if n is None or not isinstance(n, int) or n <= 0:
            raise ValueError("For binomial distribution, 'n' must be a positive integer.")
        if p is None or not (0 <= p <= 1):
            raise ValueError("For binomial distribution, 'p' must be provided and be in the range [0, 1].")
        probabilities = [binomial(n, p, x) for x in vals]
    elif dist_name == "poisson":
        mu = params.get("mu")
        if mu is None or mu <= 0:
            raise ValueError("For Poisson distribution, 'mu' must be a positive number.")
        probabilities = [poisson_dist(mu, x) for x in vals]


        def main():
    while True:
        print("\n--- Probability Distribution Calculator ---")
        print("1. Geometric Distribution")
        print("2. Binomial Distribution")
        print("3. Poisson Distribution")
        print("4. Uniform Distribution")
        print("5. Exit")

        choice = input("Enter your choice (1-5): ")

        if choice == '5':
            print("Exiting the program. Goodbye!")
            break

        try:
            if choice == '1':
                vals = list(map(float, input("Enter the values (space-separated): ").split()))
                p = float(input("Enter the probability p (0 < p <= 1): "))
                probabilities = get_probability_distribution("geometric", {"p": p}, vals)

            elif choice == '2':
                vals = list(map(float, input("Enter the values (space-separated): ").split()))
                n = int(input("Enter the number of trials n (positive integer): "))
                p = float(input("Enter the probability p (0 <= p <= 1): "))
                probabilities = get_probability_distribution("binomial", {"n": n, "p": p}, vals)

            elif choice == '3':
                vals = list(map(float, input("Enter the values (space-separated): ").split()))
                mu = float(input("Enter the mean mu (positive value): "))
                probabilities = get_probability_distribution("poisson", {"mu": mu}, vals)

            elif choice == '4':
                vals = list(map(float, input("Enter the values (space-separated): ").split()))
                a = float(input("Enter the lower bound a: "))
                b = float(input("Enter the upper bound b (b > a): "))
                probabilities = get_probability_distribution("uniform", {"a": a, "b": b}, vals)
                
            else:
                print("Invalid choice. Please select a valid option.")

        except ValueError as e:
            print(f"Error: {e}")
        except Exception as e:
            print(f"Unexpected error: {e}")

if __name__ == "__main__":
    main()

    elif dist_name == "uniform":
        a = params.get("a")
        b = params.get("b")
        if a is None or b is None or not (a < b):
            raise ValueError("For uniform distribution, 'a' and 'b' must be provided with 'a' < 'b'.")
        probabilities = [uniform_dist(a, b, x) for x in vals]
