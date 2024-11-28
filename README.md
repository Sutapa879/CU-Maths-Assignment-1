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
    elif dist_name == "uniform":
        a = params.get("a")
        b = params.get("b")
        if a is None or b is None or not (a < b):
            raise ValueError("For uniform distribution, 'a' and 'b' must be provided with 'a' < 'b'.")
        probabilities = [uniform_dist(a, b, x) for x in vals]
