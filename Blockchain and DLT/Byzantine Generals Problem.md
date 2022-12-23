- A group of army generals who lead different parts of the Byzantine army are planning to attack or retreat from a city
- The only way of communication is via a messenger
- They need to agree to strike at the same time in order to win
- The issue is that one or more generals might be traitors who could send a misleading message
- Therefore, there is a need for a viable mechanism that allows for agreement among generals so that the attack can still take place at the same time

- As an analogy to distributed systems, the generals can be considered as nodes, the traitors as Byzantine (malicious) modes, and the messenger can be thought as a channel of communication

- The problem was solved by Practical Byzantine Fault Tolerance (PBFT) algorithm, where consensus is reached after a certain number of messages are received containing the same signed content