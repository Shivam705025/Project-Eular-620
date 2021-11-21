
#include <bits/stdc++.h>
#include <iostream>

using namespace std;

void solve_620() {
	auto start = std::chrono::high_resolution_clock::now();

	unsigned n = 500;
	unsigned c, s, p;
	double z;
	unsigned G = 0;
	for (c = 16; c <= n; ++c) {
		for (s = 5; s <= c - 11; s++) {
			for (p = 5; p <= (c - s - 1) / 2; ++p) {
				z = (std::pow(c - s - 2 * M_PI, 2) - std::pow(c - p, 2) + std::pow(p + s, 2)) / (2 * (c - s - 2 * M_PI)*(p + s));
				G += p + s - 1 - (unsigned)(((p + s)*std::acos(z) - (c - p)*std::asin(std::sqrt(1-z*z)*(p + s) / (c - p))) / M_PI);
			}
		}
	}

	auto end = std::chrono::high_resolution_clock::now();
	std::chrono::duration<double, std::milli> elapsed = end - start;
	std::cout << "G(" << n << ")=" << G << "." << std::endl;
	std::cout << "Computation took " << elapsed.count() << " milliseconds." << std::endl;
}

int main()
{
    
    solve_620();
    return 0;
}
