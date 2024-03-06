# PGP40: Council Incentive Emissions

## Introduction

In our ongoing efforts to incentivize participation and reward our DAO members, we have devised a PHY emission strategy that not only recognises the Councils contributions but also safeguards project liquidity. This proposal outlines the proposed emission parameters for distributing PHY, incorporating a monthly balanced staggered release mechanism.

## Emission Parameters

Each DAO Council Member is entitled to receive an incentive reward of 3,000 PHY monthly. To manage and distribute these rewards effectively, while minimising potential impacts on liquidity, we propose the following structured approach:

- **Total Monthly Distribution:**

Given our current membership count of 8, the total monthly distribution will amount to 24,000 PHY (3,000 PHY per member).

## Token Distribution Schedule for Different Month Lengths

To ensure an even distribution of 3000 PHY tokens monthly to each of 8 members while minimizing liquidity impact, we adjust the distribution schedule based on the month's length. This document outlines the formula and specific adjustments required for months with 30, 31, 28 days, and February in a leap year.

## Given Variables

- \(M = 8\): Total number of members.
- \(D\): Total days in the month (30 for months with 30 days, 31 for months with 31 days, 28 for February in non-leap years, and 29 for February in leap years).
- \(i\): Member's assigned number (1 through 8).

## Distribution Day Formula

The formula to calculate the distribution day (\(D_{dist}\)) for each member is as follows:

$$
D_{dist} = \left\lfloor \frac{D}{M} \right\rfloor \times (i - 1) + 1
$$

Where:
- \(D_{dist}\) is the day of the month each member receives their distribution.
- The floor function \(\left\lfloor \cdot \right\rfloor\) represents the operation of rounding down to the nearest whole number.
- \(D\) is the total number of days in the month.
- \(M\) is the total number of members.
- \(i\) is each member's assigned number.

## Example Adjustments

### For a 30-Day Month

For months with 30 days, using \(D = 30\), members will receive their tokens spread out from the beginning to the end of the month, with each distribution approximately every 3.75 days apart.

### For a 31-Day Month

For months with 31 days, using \(D = 31\), the distribution interval might slightly increase, allowing for a distribution approximately every 3.875 days.

### For February in a Non-Leap Year (28 Days)

For February in non-leap years with \(D = 28\), the distribution interval becomes tighter, with a distribution approximately every 3.5 days.

### For February in a Leap Year (29 Days)

For February in leap years with \(D = 29\), the distribution interval adjusts slightly to accommodate the extra day, with distributions approximately every 3.625 days.

## Practical Application

After calculating the initial \(D_{dist}\) for each member, slight manual adjustments to the specific days may be necessary to ensure that distributions do not overlap and that all distributions fit within the month, especially for February.

This structured approach ensures that regardless of the month's length, the distribution of tokens remains as even as possible, helping to manage liquidity effectively while providing consistent rewards to DAO members.



- **Balanced Staggered Release:**

To mitigate large, instantaneous impacts on liquidity resulting from bulk releases, we will implement a balanced staggered release schedule. This approach ensures a more even distribution into the market over the course of each month.

### Implementation Strategy

- **Monthly Distribution Formula:**

Each member receives a monthly allocation of 3,000 PHY. The distribution is calculated as follows:
`Monthly PHY per Member = 3,000 PHY`

- **24-Month Emission Period:**

The emission strategy is designed to span a 24-month period, a standard Council Members term per Council Protocol, providing full-term incentives. The cumulative distribution per Council Member over this period will be 72,000 PHY, calculated as:
`Total PHY per Council Member over 24 Months = 3,000 PHY/month × 24 months`

### Benefits

- **Liquidity Management:** By spreading out emissions, we reduce the risk of significant liquidity impacts following large, simultaneous releases.
- **Council Member Incentivization:** A clear, structured reward mechanism encourages ongoing participation and contribution to the DAO.
- **Market Stability:** A staggered release helps maintain stability, benefiting both our members and the overall ecosystem.

## Initial Launch: One-Month Lock on Emissions

To ensure a smooth launch and the completion of essential project-related matters, we will implement a one-month lock on emissions following the initial distribution of PHY. This lock period is designed to:

- **Stabilize the Ecosystem Economy:** Curb immediate exits, allowing the market to stabilize and value to accrue based on project fundamentals rather than initial speculation.
- **Finalize Project Infrastructure:** Provide the team with the necessary time to finalize any outstanding infrastructure needs, ensuring that all systems are fully operational and secure.
- **Community Engagement and Feedback:** Allow time for initial community engagement and feedback, enabling adjustments to project direction, utility, and distribution mechanisms based on user input.
- **Strategic Partnerships:** Finalize discussions and formalize agreements with strategic partners, ensuring that the project ecosystem is robust and supported by key industry players from the start.

### Implementation Details

- **Lock Period Start:** The lock period will commence immediately following the initial token distribution to DAO Council members.
- **Duration:** The lock will be in place for exactly one month from the start date.
- **Emissions Resume:** Following the conclusion of the one-month lock period, regular emissions as outlined in the [Distribution Day Formula](#distribution-day-formula) section will resume according to the predetermined schedule.

## Escrow Account for 24-Month Allocation

In alignment with our commitment to transparency and security, the allocation of PHY for the 24-month incentive program for all 8 Council members will be placed in escrow at the outset of the program. This approach ensures that:

- **Guaranteed Availability of Funds:** Members have confidence that their future allocations are secured and will be available at the designated distribution times.
- **Enhanced Trust:** By locking the tokens in escrow, we demonstrate our commitment to the long-term success of the project and our trust in its members.
- **Regulatory Compliance:** This method aligns with best practices for digital asset management, ensuring compliance with regulatory standards concerning the secure handling of tokens.
- **Dispute Resolution:** In the unlikely event of disputes or unforeseen circumstances, the escrow account provides a mechanism for resolution, ensuring that tokens are distributed according to the agreed terms.

### Implementation Details

- **Token Allocation:** The total sum of PHY allocated for the 24-month period for all members (calculated as 3,000 PHY per month per member, totaling 576,000 PHY for all Council members over 24 months) will be deposited in escrow from `DAO Treasury: Governance` account before the program's commencement.
- **Release Schedule:** PHY will be released from the escrow account according to the monthly distribution schedule outlined in the [Distribution Day Formula](#distribution-day-formula) section, following the initial one-month lock period.
- **Oversight and Auditing:** The escrow arrangement will include provisions for regular oversight and auditing, ensuring that the release of funds occurs transparently and according to the predefined schedule.

## Optional Emission Lock with Annual Reward

To further align the interests of our members with the long-term success of the project, we are introducing an optional emission lock program. Council Members who choose to participate in this program by locking their emissions will receive an annual reward of 8% on their locked allocation. This initiative is designed to:

- **Encourage Long-Term Holding:** Reward members for their commitment to the project's future by providing a tangible incentive for holding their PHY.
- **Strengthen Project Stability:** Reduce the circulating supply of PHY in the short term, which can help stabilize the token price and reduce volatility.
- **Align Interests:** Ensure that Council Members, especially those deeply involved in the project's development and growth, have aligned incentives with the project's long-term vision.

### Program Details

- **Reward Rate:** Participants in the emission lock program will receive an 8% annual reward on their locked tokens, calculated based on the total amount of PHY they choose to lock.
- **Lock Duration:** The lock period will last for one year from the date of opting into the program. PHY cannot be accessed or transferred during this time.
- **Founders' Participation:** The project founders have elected to have their emissions locked by default, demonstrating confidence in the project's long-term value and their commitment to its success.
- **Opt-In Process:** Members wishing to participate in the emission lock program must opt-in by making a simple request in the Council discussion group, after which their PHY will be locked, and they will become eligible for the annual reward.

### Implementation Considerations

- **Smart Contract:** The emission lock program will be managed through a smart contract, which will automate the locking process, reward distribution, and ensure the integrity and security of the locked tokens.
- **Transparency:** Details of locked emissions, including the total amount locked and rewards distributed, will be added to this proposal when avaialbe to do so.


## Conclusion

The proposed balanced staggered release strategy for PHY emissions represents a thoughtful approach to Council Member incentivization and liquidity management. By implementing this strategy, we aim to foster a healthy, sustainable economic environment for the Physis DAO.
