Terms to know:
---
Check Digit
---

- Mathematically calculated value that is added to data to ensure that the original data has not been altered.
	Ex: Used by bank to ensure the correctness of bank account numbers assigned to the customer.
	630000241457 - The last digit is the check digit (7)
	- Add the odd number digits: 6 + 0 + 0 + 2 + 1 + 5 = 14
	- Multiply the result by 3: 14 x 3 x 3 = 42
	- Add the even number digits: 3 + 0 + 0 + 4 + 4 = 11
	- Add the two results together: 42 + 11 = 53
		- Take remainder of 53/10 and if not 0, subtract from 10. 
			- The check digit value is (7)
Parity Bits
---
- Method of error detection that requires adding an extra bit on the data. This parity bit determines whther the number of 1 bits is odd or even.
	- In general, the parity bit is 1 if the number of 1 bits is odd and 0 if the sum of the 1 bits is even
- Used to check for completeness of data transmissions
---------------
Checksum
---

- Exactly the same as a parity but able to identify complex errors also by increasing the complexity of the arithmetic
-----------------
Cyclic Redundancy Checksums (CRC) / Redundancy Checksums
---

- More advanced version of checksums by increasing the complexity of the arithmetic
---------------------------------
Forward Error Control (FEC)
---

- Same principle as CRC but FEC also allows the receiver to correct the errors.
---------------------------------
Atomicity
---

- Feature of database systems where a transaction must be all-or-nothing. It must fully completed, or nothing happens.

-------------------------

Good to know:
---

(1)When objective is to identify transcription and transposition error, answer should be check digit.

(2)When objective is to ensure accuracy, answer should be check digit.

(3)When objective is to identify transmission error, answer should be parity bits or checksum (higher version of parity bit) or CRC (higher version of checksum).

(4)When objective is to ensure completeness, answer should be parity bits or checksum (higher version of parity bit) or CRC (higher version of checksum).

(5)When objective is to ensure integrity, answer should be parity bits or checksum (higher version of parity bit) or CRC (higher version of checksum).

(6)For point no. (3), (4) and (5), first preferences to be given as follow:

(i)First preference to CRC

(ii)If CRC is not there as option then preference to be given to Checksum

(iii)If CRC and Checksum both are not there in option then preference to be given to Parity Bits.

(7)When objective is to correct (detect & correct) transmission error, answer should be Forward Error Control (FEC).

(8)When objective is to ensure that a transaction must either fully happen, or not happens at all, answer should be atomicity.

Testing in SDLC
---

(1)ISACA will try to confuse us with three terms i.e. regression testing, sociability testing and interface testing. Please remember difference between the three. Regression (dictionary meaning- ‘to return’) is test to check again that changes/modifications have not introduced any new errors.  Sociability (dictionary meaning- ‘’ability to have companionship with others’) is test to determine adoptability of new system to settle in existing environment. Integration (dictionary meaning-‘to connect’) is test to ensure flow of information between two or more system is correct and accurate.

(2)In any given scenario, for unit testing appropriate strategy is white box approach (as both involve testing of internal logic).

(3)In any given scenario, test data should be designed as per live workload for accurate test result.

(4)In any given scenario, test environment should always be used (i.e. test should not be conducted in live/production environment).

PERT, CPM, Gantt Chart, FPA, EVA, Timebox
---
(1)In any given scenario, when objective is to estimate project duration or timeless, answer should be PERT or CPM. However first preference to be given to PERT.

(2)In any given scenario, when objective is to monitor the project or track any milestone, answer should be Gantt Chart.

*(3) In any given scenario, when objective is to consider earned value by calculating any of the following, answer should be Earned Value Analysis (EVA).
	- Budget to date
	- Actual spending to date
	- Estimate to complete
	- Estimate at completion  
   

*(4) In any given scenario, when objective is to estimate software size, answer should be FPA or SLOC. However first preference to be given to FPA.

(5) In any given scenario, when objective is to prevents project cost overruns and delays from scheduled delivery, answer should be Timebox Management.

(6)Following table summarize the above provisions:

![](http://cisaexamstudy.com/wp-content/uploads/2017/03/Pert-300x149.png)

Decision Support System
---
(1)In any given scenario, DSS supports the semi-structured problem (and not only structured problem).

(2)In any given scenario, DSS should be flexible and adoptable to changing requirements and scenarios.

(3)In any given scenario, Decision tree is used as a questionnaire to lead a user through a series of choices until a conclusion is reached.

Agile System Development Methodology
---

-Dictionary meaning of agile is ‘able to move quickly and easily’.

-Agile allows the programmer to just start writing a program without spending much time on preplanning documentation.

-Less importance is placed on formal paper-based deliverables, with the preference being to produce releasable software in short iterations, typically ranging from 4 to 8 weeks.

-At the end of each iteration, the team considers and documents what worked well and what could have worked better, and identifies improvements to be implemented in subsequent iterations.

-Some programmers prefer agile because they do not want to be involved in tedious planning exercises.