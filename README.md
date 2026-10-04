# invisiible-primes
# Invisible Primes: Credit Risk Lab

An interactive website that scores borrowers with **traditional credit data** and **alternative data**, built from the research project *"Invisible Primes: FinTech Lending with Alternative Data"*.

**Live website:** [https://cosmolore.github.io/invisiible-primes/]

---

## What are "invisible primes"?

Invisible primes are people who would repay a loan but have a thin or empty credit file, so traditional credit scores cannot see them. Examples are young adults, students, gig workers and the unbanked. Alternative data such as utility bills, rent, mobile payments and employment history can help lenders spot them.

## What the website does

**1. Credit risk lab**
Enter a borrower's details and get:
- A credit score (300 to 900)
- Probability of default (PD)
- Expected loss (PD × loss given default × loan amount)
- Offered interest rate and monthly EMI
- EMI-to-income ratio
- A decision: approve, review or decline
- A comparison of the Traditional, Alternative and Combined scores
- The factors that raised or lowered the score

Two example buttons load a sample "invisible prime" and a sample high-risk borrower.

**2. Survey statistics**
Results of the primary survey (50 respondents, Mumbai, convenience sampling), with:
- Percentage analysis for all 9 survey questions
- 95% Wilson confidence intervals
- Weighted average, standard deviation and confidence interval for the familiarity and comfort questions

**3. How it works**
The weights, formulas and assumptions used by the model.

## How the model works

| Traditional factor (FICO weights) | Weight |
|---|---|
| Payment history | 35% |
| Amounts owed | 30% |
| Length of credit history | 15% |
| Credit mix | 10% |
| New credit | 10% |

| Alternative factor | Weight |
|---|---|
| Utility payments | 30% |
| Rent and mobile payments | 20% |
| Employment stability | 20% |
| Savings buffer | 15% |
| Education | 10% |
| Digital footprint (opt-in) | 5% |

- **Combined index** = share × traditional + (1 − share) × alternative
- The traditional share depends on the customer relationship: 45% for new customers, 60% for weak and 75% for strong. This follows the FICO finding that alternative data adds the most value for new customers.
- **Score** = 300 + 600 × index
- **Default probability** = 1 / (1 + e^(−1.86 + 7.19 × index))
- **Interest rate** = 11% + 40 × PD, capped at 36%
- **Thin-file rule:** with no credit history, the traditional index gets a floor of 0.30. A borrower with no history but strong
