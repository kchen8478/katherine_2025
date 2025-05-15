---
layout: page
title: AP Exam
units: "1,2,3,4,5,6,7,8,9"
search_exclude: true
menu: /nav/tri3.html
---


<a href="{{site.baseurl}}/notebooks/tri_3/ppr/">Personalized Project Reference</a>

<a href="https://docs.google.com/presentation/d/1K_BO23368YVNVn3GzGRkXFDS-DVO_EQ7wO2u_wcZRVM/edit?usp=sharing">Program Code</a>

<a href="">Video</a>

<a href="{{site.baseurl}}/notebooks/tri_3/cpt/">CB CPT</a>

<a href="{{site.baseurl}}/notebooks/tri_3/mcq20/">MCQ 2020</a>

<a href="{{site.baseurl}}/notebooks/tri_3/mcq21/">MCQ 2021</a>

<a href="{{site.baseurl}}/notebooks/tri_3/studyplan/">Study Plan</a>

# Review:

- [Review (YouTube Link)](https://www.youtube.com/watch?v=wb3taZ5bjzw&t=204s)
  - [Data](#data)
  - [Algorithms and Programming](#algorithms-and-programming)
  - [Computer Systems and Networks](#computer-systems-and-networks)
  - [Impacts of Computing](#impacts-of-computing)

- [SONI'S NOTES (Link)](https://sonidhenuva.github.io/SONIDHENUVABLOG/csp%20sprint%20objectives/2025/04/01/studyguide_IPYNB_2_.html) 

## [VIDEO](https://www.youtube.com/watch?v=wb3taZ5bjzw&t=204s) 
### Data
Binary Numbers 
- 2 ^ (0, 1, 2, etc)   10 in base 10 = 1010 in base 2
- Roundoff errors - limited precision 0.00000000001
- Overflow errors - too large to store 219390128931820398129380192830
- Analog data - changes smoothly oer time
- Digital data - represents analog data - ex of abstraction, samples 

Data Compression
- Lossless: reduces bits, guarantees complete restoration (Reconstruct original)
- Lossy: reduces more bits, only allows approximate restoration (Minimizing data size)

Extracting Info from Data
- Metatdata = Data abt data, time, location, etc, changes to metadata will not affect data
- Data needs to be cleansed and completed, cleaning makes it uniform w/o change in the meaning. (e.g. Cal, California, Cali -> CA)
- Bias can be reduced thru thoughtful data collection
- Larger data sets take more time + more complex computing systems

Using Project from Data
- can be merged, filtered, transformed, process, etc

### Algoritms and Programming
Variables, Lists, Strings
- AP exam: 1st index = 1, goes to list's length

Math
- +-/* MOD (Normal PEMDAS)
- AND - both must be true
- OR - one has to be true
- NOT - opposite 

Conditionals and Iteration
- statements control sequence

Binary Search
- sorted list, more efficient than linear search
- starts at middle, elimiates half at a time 

Procedures 
- methods/functions
- division of programs into subprograms is modularity

Libraries
- built in procedures
- simplifies creating complex programs
- API (application program interfaces) specify how procedures in a library behave and how to use them 

Simulations
- abstractions of complex proceses, mimic real world things
- random(a,b) to simulate variability in the real world 

Algorithmic Efficiency
- Decision - yes or no
- Optimization - goal of finding the best solution
- Efficieny = measure of compuataional resources used by an algorithm
    - size of input, # of times a group of states execute, etc
    - polymonial efficient or faster = reason time (constant, linear, square, cube, etc)
    - exponential/factorial algorithms run in unreasonable amounts of time 
- Heuristic Algorithms - solution isn't fully accurate or optimal, but uses a shortcut and will run faster (used when techniques which will be optimal are impractice to use)
- Decidable problems - can be solved by algorithm + correct outputs can be produced for any input
- Undecidable problem - can't be solved by an algorithm for all possible text cases 
-"Polynomial time" describes any run time that does not increase faster than 
\[n^k\], which includes constant time (
\[n^0\]), logarithmic time (
\[\log_2{n}\]), linear time (
\[n^1\]), quadratic time (
\[n^2\]), and other higher degree polynomials (like 
\[n^3\]).
- "Superpolynomial time" describes any run time that does increase faster than 
\[n^k\], and includes exponential time (
\[2^n\]), factorial time (
\[n!\]), and anything else faster.

### Computer Systems and Networks
The Internet
- computing devices = physical artifacts that run a program (computers, tablets, router, etc)
- computer networks = group of interconnected computing devices that can send/recieve data
- paths = route of directly connected computing device w sender to reciever
- routing = process of finding path from sender to reciever, at each router and not at the sender nessecarily 
- Bathwidth of a computer network = max amount of data that can be sent in a fixed time (bits/sec)
- Internet = computernetwork of interconnected networks that use standardized + open communication protocols
    - access depends on ability of computing device to connect to internt connected device
    - protocol = agreed set of rule sthat specify behavior of systm, Internet uses open protocols
    - designed to be scalable - can change in size and scale to meet new demands 
- info is passed as a data stream - chunks of data encapsulated in packets
    - packets can be in order, out of order, or not arrive at all
    - protols will rearange packs in order 
    - IP, TCP, UDP r common protocols used 
        - When communicating using IP, all messages are split into packets and sent through routers. When using TCP over IP, the recipient sends back an acknowledgment of each received packet, which improves the reliability of transmission.
- World Wide Web = sys of linked pages, programs, files
    - uses the internet
    - uses HTTP protocol

Fault Tolerance
- system that can support failure
- Internet is - abstractions for routing and transmitting data
- Reducuncy = inclusion of extra compents to mitigate failure of a sys if other parts fail (1+ paths btwn 2 connected devices)
    - increases reliability + more scalable

Parallel and Distributed COmputing
- Sequential COmputing - operations = 1 at a time, takes as long as the sum of all its steps
- Parallel COmputing -small sequential options that r performed simultaneously
    - takes as long as the sequential steps + longest of the parallel steps
    - speedup = time taken to do tasks sequentially / time taken to do task in parallel 
    - more efficient, but limited by sequential portion
- Distribute COmputing - many devices r used
    - problems can be solved which cant be solved on 1 computer bc of processing time or storage
    - larger problems can be solved qucker

### Impacts of Computing
Beneficial + Harmful Effects
- increased creativity in other fields = med, communication
- idk

Digital Divide
- internet access varying btwn socioeconomic, geographic, demographic places 
- often effect by actions of organizations + government

Computing Bias
- could reflect the programmers inherent bias
- reduced through diverse perspectives 

Crowdsourcing
- input from large numbers of ppl via Internet
- more viewpoints
- more models for collaboration - connecting businesses or social causes w funding
- Citizen Science = scientific research done by a group of regual individuals who contribute relevant data to researching using their own computing devices 

Legal + Ethical Concerns
- intellectual property - raises concern bc of ease of access to digitized info
- using material created by someone else and w/o permission or credit = plagarism, can have legal consequences
- Creative Commons = public copyright licenses that enables free distribution of copyrighted work, creator gives permission to share, use, and build upon the work
- Open Source = programs made freely avaliable and may be redistributed/modified
- Open Access = online research output free of restrictions on access
- Use of materials computed by someone else must always be cited

Safe Computing
- Personally Identifiable Information (Age, Race, SSN)
- Cookies can create knowledge on an individual
- Online info can be difficult to delete
- Authentication can help protect devices from unauth access
    - Multi Factor Authentication
    - Strong passwords
- Encryption: process of encoding data to prevent unathorized access (decryption = process of decoding data)
    - Symmetricc key encryption = 1 key used for both encryption and decryption
    - Public key encryption = pair of keys (1 public key (encryption), 1 private key (decryption))
- Certificate authorities issue digital certificates that validate the ownership of encryption keys
- Viruses r malicious progrms that can gain access to a computer in an unauthorized way
- Malware = software intended to damage a computing system
- Phishing = technique used to trick a user from revealing personal info abt themselves which can then be used to access sensivte information like bank accounts
- Keylogging = a program that records every keystroke made by a computer user
- Rogue access point intercepts data being sent over public networks
- Malicious links can be disguised on a web page or email message 

### [SONI'S NOTES ](https://sonidhenuva.github.io/SONIDHENUVABLOG/csp%20sprint%20objectives/2025/04/01/studyguide_IPYNB_2_.html)

### [2013 MCQ](https://drive.google.com/file/d/1DGahAcM1dqBv8CM4J7HEEzrak7lUaN4v/view)