# econ5200-lab09-ab-testing
# Diagnosing Experimental Failures in A/B Testing

## Objective
I investigated common sources of failure and bias in A/B testing by debugging variance reduction code, testing experiment validity, and evaluating statistical methods through simulations.

## Methodology
- **CUPED Debugging:** Identified and fixed three bugs in an analyst's CUPED variance reduction code, then evaluated the impact on variance and standard error.
- **Sample Ratio Mismatch (SRM):** Conducted chi-squared tests on two experiments with different sample sizes and user allocation imbalances.
- **Interference Simulation:** Simulated a marketplace where discounted buyers competed for limited inventory with the control group, comparing the naive A/B test ATE against the effect of rolling out the discount to everyone.
- **Bayesian A/B Testing:** Calculated the probability that B outperformed A and the expected loss of shipping B. Compared the Bayesian decision with a permutation test.
- **Bayesian Function Implementation:** Wrote my own function for Bayesian A/B testing and applied it to a test with four times the number of users.
- **Sequential Testing Simulation:** Simulated peeking at 50 points across 1,000 experiments with no actual effect and compared the false positive rate against a single end-of-experiment test.
- **CUPED Challenge (Optional):** Applied CUPED to the LaLonde job training data using re74 and re75 as pre-experiment covariates.

## Key Findings
- **CUPED:** Fixed three bugs that increased the reported variance reduction from 0.0% to 82.7%, with the standard error dropping from 0.1539 to 0.0641.
- **SRM:** A 0.600 pp imbalance among 100,000 users produced a chi-squared statistic of 14.40. A much smaller 0.050 pp imbalance among 20 million users produced a statistic of 20.00, showing that even small allocation imbalances can be statistically significant at large sample sizes.
- **Interference:** The naive A/B test ATE was 0.1861, compared with 0.1428 for a full rollout. The naive estimate overstated the full-rollout effect by 23.3%.
- **Bayesian A/B Testing:** P(B > A) was 0.8866, while the expected loss of shipping B was 0.000473. The decision rule recommended not shipping B (False). The permutation test returned p = 0.2302.
- **Bayesian Scaling:** With four times the users, P(B > A) increased to 0.9951.
- **Peeking:** Across 1,000 experiments with no effect, 32.4% crossed p < 0.05 at least once when checking 50 points, compared with 5.3% when testing only once at the end.
- **CUPED Challenge (Optional):** Applying re74 and re75 reduced variance by 0.79% in the LaLonde job training data.
