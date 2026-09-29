# Python for Cybersecurity, Ethical Hacking & Bug Bounty — Full Notes

_A single-file version of the whole course for easy reading, top to bottom._

---

# Python for Cybersecurity, Ethical Hacking & Bug Bounty

Welcome! This repository teaches Python from scratch and connects every skill to real
cybersecurity, ethical hacking, and bug bounty work. It is written for **absolute
beginners** using simple English, short examples, and hands-on assignments.

## Who this is for

- You are new to Python (or need a refresher).
- You are curious about cybersecurity, ethical hacking, or bug bounty hunting.
- You learn best by typing code yourself and solving small challenges.

## ⚠️ A Rule You Must Follow

Every security-related script in this repo is for **learning only**. Only run these
tools against:
1. Systems you personally own, **or**
2. Systems you have **written permission** to test (e.g., a bug bounty program's
   scope, or a lab like TryHackMe / HackTheBox / a local virtual machine).

Scanning, sniffing, or attacking systems you don't own or don't have permission to
test is **illegal** in most countries, even if you don't cause damage. Practice on
safe environments such as:
- Your own home network / your own computer
- Free legal practice platforms: TryHackMe, HackTheBox, OverTheWire, DVWA, Juice Shop
- Bug bounty programs that explicitly list what is "in scope"

## How This Repository Is Organized

```
python-for-cybersecurity/
├── README.md                          <- you are here
├── 01_python_basics/                  <- Module 1: Core Python (beginner)
├── 02_intermediate_python/            <- Module 2: Python tools security folks use daily
├── 03_cybersecurity_python/           <- Module 3: Python applied to security tasks
└── 04_projects/                       <- Module 4: Projects, beginner -> advanced
```

### Module 1 — Python Basics (`01_python_basics/`)
Start here if you are new to Python.

| # | File | Topic |
|---|------|-------|
| 1 | `01_variables_and_datatypes.md` | Variables, data types, type conversion |
| 2 | `02_operators.md` | Arithmetic, comparison, logical operators |
| 3 | `03_control_structures.md` | if/else, for loops, while loops |
| 4 | `04_functions.md` | Writing and using functions |
| 5 | `05_data_structures.md` | Lists, tuples, dictionaries, sets |
| 6 | `06_strings.md` | String manipulation (very important for security!) |
| 7 | `07_file_handling.md` | Reading and writing files |
| 8 | `08_error_handling.md` | try/except, handling failures gracefully |
| 9 | `09_modules_and_packages.md` | Using and installing Python libraries |
| 10 | `10_oop_basics.md` | Classes and objects |

### Module 2 — Intermediate Python (`02_intermediate_python/`)
The tools you need before writing security scripts.

| # | File | Topic |
|---|------|-------|
| 1 | `01_regular_expressions.md` | Pattern matching with `re` |
| 2 | `02_working_with_apis.md` | HTTP requests with the `requests` library |
| 3 | `03_json_and_data_parsing.md` | Reading and writing JSON |
| 4 | `04_sockets_basics.md` | How computers talk over networks |
| 5 | `05_multithreading_basics.md` | Doing many things at once (faster scans) |
| 6 | `06_command_line_tools.md` | `argparse` and building CLI tools |

### Module 3 — Cybersecurity Python (`03_cybersecurity_python/`)
Apply Python directly to ethical hacking and bug bounty tasks.

| # | File | Topic |
|---|------|-------|
| 1 | `01_network_scanning.md` | Building a simple, safe port scanner |
| 2 | `02_web_scraping_for_recon.md` | Gathering public info from websites |
| 3 | `03_password_and_hashing_tools.md` | Password strength checkers, hashing |
| 4 | `04_http_header_security_checker.md` | Checking websites for missing security headers |
| 5 | `05_subdomain_enumeration.md` | Finding subdomains (a core bug bounty skill) |
| 6 | `06_packet_sniffing_basics.md` | Reading network traffic with Scapy (own network only) |

### Module 4 — Projects (`04_projects/`)
Combine everything you learned into real projects, from beginner to advanced.
See `04_projects/README.md` for the full list.

## Suggested Learning Path

1. Go through **Module 1** in order — don't skip, even if a topic looks easy.
2. Do **every assignment**. Typing code yourself is how it sticks.
3. Move to **Module 2** once you're comfortable writing basic scripts on your own.
4. Start **Module 3** — this is where Python starts feeling like a hacking tool.
5. Pick projects from **Module 4** that match your level and build them end to end.

## How Each Topic File Is Structured

Every file in `01_python_basics/`, `02_intermediate_python/`, and
`03_cybersecurity_python/` follows the same format:

1. **What you'll learn** — a one-line summary
2. **Explanation** — simple English, no jargon dumps
3. **Examples** — small, runnable code snippets with comments
4. **Assignments** — practice tasks, roughly easy → medium → hard

## Setting Up Your Environment

```bash
# Check Python is installed (3.9+ recommended)
python3 --version

# Create a virtual environment (keeps your libraries organized)
python3 -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install the libraries used across this repo
pip install requests beautifulsoup4 scapy
```

## Tips for Beginners

- Type the examples yourself. Don't copy-paste — you learn by making small mistakes.
- If an error appears, read it top to bottom. Errors usually tell you exactly what's wrong.
- Keep a "notes.md" file of things you found confusing and revisit them weekly.
- Security tools are just normal code + curiosity about how systems work.

Happy learning, and hack responsibly! 🔐
-e 

---

# MODULE 1: PYTHON BASICS

# 1. Variables and Data Types

## What you'll learn
How to store information in Python, and the basic types of data you'll use constantly
in security scripts (numbers, text, true/false values).

## Explanation

A **variable** is just a labeled box that holds a value. You give it a name, and you
put something inside it.

```python
target_ip = "192.168.1.10"
```

Here, `target_ip` is the label, and `"192.168.1.10"` is the value stored inside.

### Common Data Types

| Type | Example | Used for in security |
|------|---------|------------------------|
| `str` (string) | `"192.168.1.10"` | IP addresses, URLs, usernames, passwords |
| `int` (integer) | `443` | Port numbers, counts |
| `float` | `3.5` | Timeouts, response times |
| `bool` (boolean) | `True` / `False` | "Is this port open?", "Did login succeed?" |
| `list` | `[80, 443, 8080]` | List of ports to scan |
| `dict` | `{"port": 80, "open": True}` | Structured scan results |

Python figures out the type automatically — you don't have to declare it like in
some other languages.

```python
target_ip = "192.168.1.10"   # str
port = 443                    # int
timeout = 2.5                 # float
is_open = True                 # bool
```

### Checking a Variable's Type

```python
print(type(target_ip))   # <class 'str'>
print(type(port))        # <class 'int'>
```

### Converting Between Types

You often need to convert types — for example, a port number entered by a user comes
in as text (`str`) but needs to be a number (`int`) to use in calculations.

```python
port_text = "443"
port_number = int(port_text)     # str -> int
print(port_number + 1)           # 444

count = 10
count_text = str(count)          # int -> str
print("Found " + count_text + " open ports")
```

### Naming Variables Well

Good variable names make your security scripts easier to read months later:

```python
# Bad
x = "10.0.0.5"
y = 22

# Good
target_ip = "10.0.0.5"
ssh_port = 22
```

## Assignments

1. **Easy:** Create variables for a `target_ip` (string), `port` (integer), and
   `is_vulnerable` (boolean). Print all three using `print()`.

2. **Easy:** Ask the user to type a port number using `input()`. Convert it to an
   integer and print `"The port number plus 100 is: <result>"`.

3. **Medium:** Create a variable `scan_result` that is the string `"Open"`. Write code
   that converts it to uppercase and prints it (hint: look up the `.upper()` string
   method).

4. **Medium:** Store the following scan summary in separate variables: target IP
   `"10.0.0.5"`, number of open ports `3`, and scan duration `12.7` seconds. Print a
   sentence that combines all three, e.g.
   `"Scanned 10.0.0.5 in 12.7 seconds, found 3 open ports."`

5. **Hard:** Write a small script that takes a MAC address as a string, e.g.
   `"00:1A:2B:3C:4D:5E"`, and prints how many colons `:` it contains using `.count()`.
   Then explain in a comment why validating input format matters in security tools.
-e 

---

# 2. Operators

## What you'll learn
How to do math, compare values, and combine conditions — the building blocks of every
"if this port is open" or "if this password is weak" decision.

## Explanation

### Arithmetic Operators

```python
a = 10
b = 3

print(a + b)   # 13  addition
print(a - b)   # 7   subtraction
print(a * b)   # 30  multiplication
print(a / b)   # 3.333...  division (always gives a float)
print(a // b)  # 3   floor division (rounds down)
print(a % b)   # 1   modulus (remainder) — used a lot in security math (hashing, loops)
print(a ** b)  # 1000 exponent (a to the power of b)
```

### Comparison Operators

These return `True` or `False` — perfect for security checks.

```python
port = 22
print(port == 22)   # True  (equal to)
print(port != 80)   # True  (not equal to)
print(port > 1024)  # False (greater than)
print(port < 1024)  # True  (less than)
print(port >= 22)   # True  (greater than or equal to)
```

### Logical Operators

Combine multiple conditions — very common in scan logic.

```python
port = 443
is_https = True

# and: both conditions must be True
if port == 443 and is_https:
    print("Likely a secure web server")

# or: at least one condition must be True
if port == 80 or port == 443:
    print("This is a common web port")

# not: flips True/False
password_is_weak = False
if not password_is_weak:
    print("Password looks okay")
```

### A Real Security Example

```python
password_length = 6
has_number = False
has_symbol = False

is_strong = password_length >= 12 and has_number and has_symbol
print("Password strong?", is_strong)   # False — too short and missing number/symbol
```

## Assignments

1. **Easy:** Given `attempts = 5` and `max_attempts = 3`, write a comparison that
   checks if `attempts` has exceeded `max_attempts`, and print the result.

2. **Easy:** Use the modulus operator `%` to check whether the number `1024` is even.
   (Hint: a number is even if `number % 2 == 0`.)

3. **Medium:** A port scanner found `open_ports = 2` and the target allows a max of
   `1` open port under its security policy (`allowed_open_ports = 1`). Write a
   condition using `>` that prints `"Policy violation!"` if there are more open ports
   than allowed.

4. **Medium:** Write a condition that checks if a `port` variable is either `21`
   (FTP) or `23` (Telnet) — both are considered insecure legacy protocols. Print
   `"Insecure protocol detected"` if true.

5. **Hard:** A simple password checker needs ALL of these to be true to call a
   password "strong": length >= 10, contains at least one digit, contains at least one
   uppercase letter. Create boolean variables for each condition (you can hardcode
   True/False for now) and combine them with `and` into one `is_strong` variable.
-e 

---

# 3. Control Structures (if/else, for, while)

## What you'll learn
How to make decisions in code and repeat actions — essential for scanning multiple
ports, checking multiple passwords, or looping through a wordlist.

## Explanation

### if / elif / else

```python
port = 443

if port == 80:
    print("HTTP port")
elif port == 443:
    print("HTTPS port")
else:
    print("Some other port")
```

Indentation (the spaces at the start of a line) matters in Python — it defines which
code belongs to which block.

### for loops

Used to go through a list of items one by one — like a list of ports or IPs.

```python
ports_to_scan = [21, 22, 80, 443, 8080]

for port in ports_to_scan:
    print("Checking port:", port)
```

`range()` generates a sequence of numbers, handy for scanning a range of ports:

```python
for port in range(1, 6):     # 1, 2, 3, 4, 5
    print("Scanning port", port)
```

### while loops

Repeats as long as a condition is `True`. Useful for retry logic.

```python
attempts = 0
max_attempts = 3

while attempts < max_attempts:
    print("Login attempt", attempts + 1)
    attempts += 1   # same as attempts = attempts + 1

print("Locked out after", attempts, "attempts")
```

### break and continue

```python
ports = [21, 22, 80, 443]

for port in ports:
    if port == 80:
        continue   # skip this one, go to next
    if port == 443:
        break      # stop the loop entirely
    print("Checking port", port)
```

### A Realistic Mini Example

```python
open_ports = []

for port in range(20, 25):
    # Pretend logic: in real scanning, you'd actually try to connect
    if port in [21, 22]:
        open_ports.append(port)

print("Open ports found:", open_ports)
```

## Assignments

1. **Easy:** Write a `for` loop that prints every port number from 1 to 10.

2. **Easy:** Write an `if/elif/else` block that takes a `port` variable and prints
   `"Web"` for 80 or 443, `"SSH"` for 22, `"FTP"` for 21, and `"Unknown"` for anything
   else.

3. **Medium:** Given a list `common_ports = [21, 22, 23, 25, 53, 80, 110, 443]`, loop
   through it and print only the ports greater than 50, using `if` inside the `for`
   loop.

4. **Medium:** Write a `while` loop that simulates a login system: it should allow
   up to 3 attempts. Use a variable `password_correct = False` (hardcoded) and print
   `"Access denied"` after the loop ends if the password was never correct.

5. **Hard:** Write a `for` loop over `range(1, 1025)` that builds a list of only the
   "well-known" ports (ports below 1024) that are divisible by 100. Print the
   resulting list at the end. This kind of filtering logic is exactly what you'll use
   later when writing a real port scanner.
-e 

---

# 4. Functions

## What you'll learn
How to package reusable pieces of logic — every real security tool is built from
small, well-named functions instead of one giant block of code.

## Explanation

### Defining and Calling a Function

```python
def greet(name):
    print("Hello, " + name)

greet("Ashray")   # Hello, Ashray
```

### Returning Values

```python
def is_common_port(port):
    common_ports = [21, 22, 80, 443]
    return port in common_ports

result = is_common_port(443)
print(result)   # True
```

### Default Parameter Values

```python
def scan_message(port, protocol="TCP"):
    print(f"Scanning port {port} using {protocol}")

scan_message(443)              # Scanning port 443 using TCP
scan_message(53, "UDP")        # Scanning port 53 using UDP
```

### Multiple Return Values

```python
def analyze_password(password):
    length_ok = len(password) >= 10
    has_digit = any(char.isdigit() for char in password)
    return length_ok, has_digit

length_ok, has_digit = analyze_password("hunter2")
print(length_ok, has_digit)   # False True
```

### Why Functions Matter for Security Scripts

Instead of writing scanning logic once per port, you write it once as a function and
call it many times:

```python
def check_port_range(start, end):
    results = []
    for port in range(start, end + 1):
        # Placeholder logic — real scanning comes in Module 3
        is_open = port % 7 == 0
        results.append((port, is_open))
    return results

print(check_port_range(1, 20))
```

## Assignments

1. **Easy:** Write a function `square(number)` that returns the number multiplied by
   itself. Call it with `5` and print the result.

2. **Easy:** Write a function `is_valid_port(port)` that returns `True` if the port
   is between 1 and 65535 (inclusive), and `False` otherwise.

3. **Medium:** Write a function `format_ip_status(ip, is_up)` that returns a string
   like `"192.168.1.1 is UP"` or `"192.168.1.1 is DOWN"` depending on the boolean.

4. **Medium:** Write a function `count_vowels(text)` that counts how many vowels are
   in a given string. (This kind of string analysis is used in password strength
   tools.)

5. **Hard:** Write a function `password_strength(password)` that returns one of
   `"Weak"`, `"Medium"`, or `"Strong"` based on these rules:
   - Weak: length < 8
   - Medium: length >= 8 but no digit
   - Strong: length >= 8 AND contains at least one digit

   Test it with at least 3 different passwords and print the results.
-e 

---

# 5. Data Structures: Lists, Tuples, Dictionaries, Sets

## What you'll learn
How to store groups of data — a list of ports, a dictionary of scan results, a set of
unique subdomains. This is one of the most-used skills in security scripting.

## Explanation

### Lists — ordered, changeable collections

```python
ports = [21, 22, 80, 443]

ports.append(8080)          # add to the end
print(ports)                 # [21, 22, 80, 443, 8080]

ports.remove(21)             # remove a specific value
print(len(ports))            # number of items in the list

for port in ports:
    print(port)
```

### Tuples — ordered, but CANNOT be changed after creation

Good for fixed data, like a single scan result `(ip, port, status)`.

```python
result = ("192.168.1.10", 443, "open")
ip, port, status = result   # unpacking
print(ip, port, status)
```

### Dictionaries — key/value pairs

Perfect for structured data, like storing scan results by port.

```python
scan_results = {
    21: "closed",
    22: "open",
    443: "open"
}

print(scan_results[22])          # open
scan_results[80] = "filtered"    # add a new key
print(scan_results)

for port, status in scan_results.items():
    print(f"Port {port}: {status}")
```

### Sets — unordered collections with NO duplicates

Useful for storing unique subdomains found during recon.

```python
subdomains = {"mail.example.com", "api.example.com", "mail.example.com"}
print(subdomains)          # duplicates are automatically removed
print(len(subdomains))     # 2

subdomains.add("dev.example.com")
```

### Choosing the Right Structure

| Need | Use |
|------|-----|
| Order matters, values may repeat, you may change it | `list` |
| Order matters, values are fixed forever | `tuple` |
| You need to look things up by a name/key | `dict` |
| You just need unique items, order doesn't matter | `set` |

## Assignments

1. **Easy:** Create a list of 5 common ports. Use a `for` loop to print each one with
   the label `"Port: "`.

2. **Easy:** Create a dictionary mapping 3 ports to their common service names, e.g.
   `{22: "SSH", 80: "HTTP", 443: "HTTPS"}`. Print the service name for port `80`.

3. **Medium:** You scraped a list of emails from a website, some duplicated:
   `["a@x.com", "b@x.com", "a@x.com", "c@x.com"]`. Convert this list into a `set` to
   remove duplicates, then print how many unique emails remain.

4. **Medium:** Create a dictionary `scan_summary` with keys `"target"`, `"open_ports"`
   (a list), and `"scan_time"`. Fill it with sample data and print a formatted summary
   sentence using an f-string.

5. **Hard:** You have two lists of subdomains found by two different tools:
   `tool_a = ["mail.x.com", "api.x.com", "dev.x.com"]` and
   `tool_b = ["api.x.com", "shop.x.com"]`.
   Using sets, find:
   (a) subdomains found by BOTH tools (intersection),
   (b) subdomains found by tool_a only (difference),
   (c) all unique subdomains combined (union).
   Print all three results. (Hint: look up `&`, `-`, and `|` operators on sets.)
-e 

---

# 6. String Manipulation

## What you'll learn
How to slice, search, and clean up text — this is the single most-used skill in
security scripting: parsing URLs, log files, HTTP responses, and wordlists.

## Explanation

### Basic String Operations

```python
url = "https://example.com/login"

print(len(url))               # length of the string
print(url.upper())            # HTTPS://EXAMPLE.COM/LOGIN
print(url.lower())            # already lowercase here
print(url.replace("https", "http"))
print(url.startswith("https"))   # True
print(url.endswith("/login"))    # True
```

### Slicing (getting parts of a string)

```python
text = "password123"

print(text[0])       # 'p'          (first character)
print(text[-1])      # '3'          (last character)
print(text[0:8])     # 'password'   (characters 0 to 7)
print(text[8:])      # '123'        (from index 8 to the end)
```

### Splitting and Joining

Very common when parsing log lines or CSV-style data.

```python
log_line = "192.168.1.5 - GET /admin - 403"
parts = log_line.split(" - ")
print(parts)   # ['192.168.1.5', 'GET /admin', '403']

ip = parts[0]
path = parts[1]
status = parts[2]
print(f"{ip} tried to access {path} and got status {status}")

# Joining back together
rebuilt = " - ".join(parts)
print(rebuilt)
```

### Searching Inside Strings

```python
response = "Server: Apache/2.4.41 (Ubuntu)"

if "Apache" in response:
    print("Server is running Apache")

position = response.find("Apache")
print(position)   # index where "Apache" starts, or -1 if not found
```

### f-strings (formatted strings) — use these constantly

```python
target = "10.0.0.5"
port = 443
print(f"Connecting to {target} on port {port}...")
```

### Cleaning User Input

```python
raw_input_value = "  admin@example.com  \n"
clean_value = raw_input_value.strip()      # removes whitespace/newlines from ends
print(f"'{clean_value}'")
```

## Assignments

1. **Easy:** Given `url = "http://testsite.local:8080/index.php"`, print it in
   uppercase, then check if it `.startswith("http://")`.

2. **Easy:** Given a raw HTTP header string `"Content-Type: application/json"`, split
   it on `": "` and print the header name and value separately.

3. **Medium:** Given a log line `"2024-05-01 10:22:31 FAILED login for user admin"`,
   use `.split()` to break it into pieces and print just the username (`admin`).
   (Hint: split by spaces and figure out which index has the username.)

4. **Medium:** Write code that checks if the substring `"error"` (case-insensitive)
   appears anywhere in a given server response string. Test it with a response that
   contains `"Error: Access Denied"`.

5. **Hard:** Given a comma-separated string of ports: `"21,22,80,443,8080"`, split it
   into a list of **integers** (not strings!) and print the sum of all the port
   numbers. (Hint: you'll need `.split(",")` plus a loop or list comprehension with
   `int()`.)
-e 

---

# 7. File Handling

## What you'll learn
How to read wordlists, save scan results, and process log files — reading and
writing files is a daily task in security tooling.

## Explanation

### Writing to a File

```python
with open("scan_results.txt", "w") as file:
    file.write("Port 22: open\n")
    file.write("Port 80: open\n")
    file.write("Port 443: open\n")
```

Using `with open(...) as file:` automatically closes the file when you're done —
always prefer this over manually calling `.close()`.

### Reading a File

```python
with open("scan_results.txt", "r") as file:
    content = file.read()
    print(content)
```

### Reading Line by Line (great for wordlists)

```python
with open("wordlist.txt", "r") as file:
    for line in file:
        word = line.strip()   # remove the newline character
        print("Trying password:", word)
```

### Appending to a File (adding without erasing old content)

```python
with open("scan_results.txt", "a") as file:
    file.write("Port 3306: closed\n")
```

### File Modes Cheat Sheet

| Mode | Meaning |
|------|---------|
| `"r"` | Read (file must exist) |
| `"w"` | Write (creates file, **erases existing content**) |
| `"a"` | Append (creates file if missing, adds to the end) |
| `"r+"` | Read and write |

### Handling Missing Files Safely

```python
try:
    with open("does_not_exist.txt", "r") as file:
        print(file.read())
except FileNotFoundError:
    print("That file doesn't exist!")
```

(We'll cover `try/except` properly in the next topic.)

## Assignments

1. **Easy:** Write a script that creates a file `notes.txt` and writes three lines
   of text to it, each on its own line.

2. **Easy:** Read `notes.txt` back and print its contents.

3. **Medium:** Create a small text file `ports.txt` containing one port number per
   line (e.g., 21, 22, 80, 443). Write a script that reads the file, converts each
   line to an integer, and prints the sum of all ports.

4. **Medium:** Write a function `save_scan_result(filename, ip, port, status)` that
   appends a line like `"192.168.1.5,443,open"` to the given file, so you can call it
   repeatedly during a scan without erasing previous results.

5. **Hard:** Create a small "log file" (`login_attempts.log`) with a few lines like:
   ```
   admin,10.0.0.5,FAILED
   admin,10.0.0.5,FAILED
   root,10.0.0.9,SUCCESS
   admin,10.0.0.5,FAILED
   ```
   Write a script that reads this file and prints how many `FAILED` attempts came
   from each unique IP address (hint: combine file reading with a dictionary to count
   occurrences — this is exactly how brute-force detection tools work).
-e 

---

# 8. Error Handling (try/except)

## What you'll learn
How to keep your scripts running smoothly even when things go wrong — a closed port,
a timeout, a bad file path. Security scripts run against unpredictable targets, so
error handling is essential, not optional.

## Explanation

### Basic try/except

```python
try:
    port = int("not_a_number")
except ValueError:
    print("That wasn't a valid number!")
```

Without `try/except`, that line would crash your whole program.

### Catching Specific Errors

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Can't divide by zero!")
except ValueError:
    print("Invalid value!")
```

### Catching Any Error (use sparingly)

```python
try:
    risky_operation()
except Exception as error:
    print(f"Something went wrong: {error}")
```

Catching every possible error with a generic `Exception` is convenient, but try to
catch specific errors when you know what could go wrong — it makes debugging easier.

### try / except / else / finally

```python
try:
    file = open("data.txt", "r")
except FileNotFoundError:
    print("File not found.")
else:
    print("File opened successfully.")
    file.close()
finally:
    print("This always runs, error or not.")
```

### A Realistic Security Example

Connecting to a port that might be closed, filtered, or the host might be down:

```python
import socket

def check_port(ip, port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        sock.connect((ip, port))
        print(f"Port {port} is OPEN")
        sock.close()
    except socket.timeout:
        print(f"Port {port} TIMED OUT (likely filtered)")
    except ConnectionRefusedError:
        print(f"Port {port} is CLOSED")
    except Exception as error:
        print(f"Unexpected error on port {port}: {error}")

# check_port("127.0.0.1", 80)   # try this on your OWN machine
```

We'll build this into a full scanner in Module 3 — for now, just understand the
error-handling pattern.

## Assignments

1. **Easy:** Write code that tries to convert the string `"abc"` into an integer
   using `int()`, and catches the `ValueError` with a friendly message.

2. **Easy:** Write code that tries to access index `10` of a list with only 3 items,
   and catches the `IndexError`.

3. **Medium:** Write a function `safe_divide(a, b)` that returns the result of `a / b`
   but returns `None` and prints a warning if `b` is `0`, instead of crashing.

4. **Medium:** Write code that tries to open a file that doesn't exist, catches
   `FileNotFoundError`, and instead creates the file with some default content.

5. **Hard:** Write a function `parse_port(value)` that tries to convert `value` to an
   integer AND checks it's between 1–65535. If conversion fails, catch the error and
   return `None`. If it's out of range, print a warning and also return `None`. Test
   it with `"443"`, `"abc"`, and `"99999"`.
-e 

---

# 9. Modules and Packages

## What you'll learn
How to use Python's built-in tools and install third-party libraries — nearly every
security script depends on modules like `socket`, `requests`, or `scapy`.

## Explanation

### Importing Built-in Modules

Python comes with many modules ready to use, no installation needed.

```python
import socket
import random
import datetime

print(socket.gethostname())        # your computer's network name
print(random.randint(1, 100))       # random number between 1 and 100
print(datetime.datetime.now())      # current date and time
```

### Importing Specific Things From a Module

```python
from random import randint
print(randint(1, 10))   # no need to write random.randint anymore
```

### Giving a Module a Shorter Name (alias)

```python
import datetime as dt
print(dt.datetime.now())
```

### Installing Third-Party Packages with pip

Some tools aren't built into Python — you install them separately:

```bash
pip install requests
pip install beautifulsoup4
pip install scapy
```

Then use them like any other module:

```python
import requests

response = requests.get("https://example.com")
print(response.status_code)
```

### Useful Built-in Modules for Security Work

| Module | What it's for |
|--------|----------------|
| `socket` | Low-level networking (ports, connections) |
| `re` | Pattern matching / regular expressions |
| `hashlib` | Hashing (MD5, SHA-256, etc.) for passwords/checksums |
| `os` | Working with files, directories, environment variables |
| `subprocess` | Running other command-line tools from Python |
| `json` | Reading/writing JSON data (common in APIs) |
| `time` | Delays, timestamps, measuring how long something takes |

### Organizing Your Own Code Into Modules

Any `.py` file can be imported into another.

```python
# file: helpers.py
def is_valid_ip(ip):
    parts = ip.split(".")
    return len(parts) == 4

# file: main.py
from helpers import is_valid_ip

print(is_valid_ip("192.168.1.1"))   # True
```

## Assignments

1. **Easy:** Import the `random` module and print 5 random numbers between 1 and 50.

2. **Easy:** Import the `datetime` module and print today's date only (not the time).

3. **Medium:** Import `hashlib` and use `hashlib.sha256()` to hash the string
   `"password123"`. Print the resulting hex digest. (This is the foundation of how
   passwords are stored securely — never in plain text!)

4. **Medium:** Create a file `network_helpers.py` with a function
   `is_private_ip(ip)` that returns `True` if the IP starts with `"192.168."` or
   `"10."`. Import and use it from a separate script.

5. **Hard:** Install the `requests` library, then write a script that sends a GET
   request to `"https://httpbin.org/get"` and prints the response's status code and
   the first 200 characters of the response text. Wrap the request in a
   `try/except` to handle connection errors gracefully.
-e 

---

# 10. Object-Oriented Programming (OOP) Basics

## What you'll learn
How to organize related data and behavior together using classes — useful once your
security tools grow beyond a handful of functions (e.g., a `Scanner` class, a
`Target` class).

## Explanation

### Why OOP?

Imagine tracking many scan targets, each with an IP, a list of open ports, and a
status. Instead of juggling separate variables for each target, you bundle them into
one object.

### Defining a Class

```python
class Target:
    def __init__(self, ip):
        self.ip = ip
        self.open_ports = []

    def add_open_port(self, port):
        self.open_ports.append(port)

    def summary(self):
        return f"{self.ip} has {len(self.open_ports)} open port(s): {self.open_ports}"
```

`__init__` is the constructor — it runs automatically when you create a new object.
`self` refers to "this specific object."

### Creating and Using Objects

```python
target1 = Target("192.168.1.10")
target1.add_open_port(22)
target1.add_open_port(443)

print(target1.summary())
# 192.168.1.10 has 2 open port(s): [22, 443]

target2 = Target("192.168.1.20")
target2.add_open_port(80)
print(target2.summary())
```

Each object (`target1`, `target2`) keeps its own separate data.

### A Slightly Bigger Example

```python
class PasswordChecker:
    def __init__(self, password):
        self.password = password

    def has_min_length(self, min_length=8):
        return len(self.password) >= min_length

    def has_digit(self):
        return any(char.isdigit() for char in self.password)

    def rating(self):
        if self.has_min_length() and self.has_digit():
            return "Strong"
        elif self.has_min_length():
            return "Medium"
        else:
            return "Weak"

checker = PasswordChecker("hunter22")
print(checker.rating())   # Strong
```

### Inheritance (a brief look)

```python
class ScanResult:
    def __init__(self, target):
        self.target = target

class PortScanResult(ScanResult):
    def __init__(self, target, port, is_open):
        super().__init__(target)
        self.port = port
        self.is_open = is_open

result = PortScanResult("192.168.1.10", 443, True)
print(result.target, result.port, result.is_open)
```

You don't need to master inheritance yet — just recognize the pattern when you see
it in security libraries like `scapy`.

## Assignments

1. **Easy:** Create a class `Website` with an `__init__` that stores a `url`. Add a
   method `display()` that prints `"Website: <url>"`.

2. **Easy:** Create two `Website` objects with different URLs and call `.display()`
   on each.

3. **Medium:** Extend the `Target` class from the explanation above with a method
   `is_high_value()` that returns `True` if the target has more than 3 open ports.

4. **Medium:** Create a class `LoginAttempt` that stores `username`, `ip_address`,
   and `success` (boolean). Add a method `describe()` that returns a readable
   sentence describing the attempt.

5. **Hard:** Create a class `Scanner` that stores a list of `Target` objects
   (from earlier in this file). Add a method `add_target(ip)` that creates a new
   `Target` and stores it, and a method `report()` that prints a summary line for
   every target the scanner has tracked so far.
-e 

---

# MODULE 2: INTERMEDIATE PYTHON

# 1. Regular Expressions (Pattern Matching)

## What you'll learn
How to search for patterns in text — extracting IP addresses, emails, or URLs from
logs and web pages is a daily task in security work, and regex is the tool for it.

## Explanation

Python's `re` module handles regular expressions (regex).

### Basic Searching

```python
import re

text = "Failed login from 192.168.1.5 at 10:32am"

match = re.search(r"\d+\.\d+\.\d+\.\d+", text)
if match:
    print("Found IP:", match.group())   # Found IP: 192.168.1.5
```

### Common Regex Building Blocks

| Pattern | Meaning |
|---------|---------|
| `\d` | any digit (0-9) |
| `\w` | any letter, digit, or underscore |
| `\s` | any whitespace |
| `+` | one or more of the previous thing |
| `*` | zero or more of the previous thing |
| `.` | any character (except newline) |
| `[abc]` | any one of a, b, or c |
| `^` | start of string |
| `$` | end of string |

### Finding All Matches

```python
import re

log = """
Login from 192.168.1.5
Login from 10.0.0.9
Login from 172.16.0.3
"""

ips = re.findall(r"\d+\.\d+\.\d+\.\d+", log)
print(ips)   # ['192.168.1.5', '10.0.0.9', '172.16.0.3']
```

### Extracting Emails

```python
import re

page_text = "Contact us at admin@example.com or support@example.org"

emails = re.findall(r"[\w\.-]+@[\w\.-]+\.\w+", page_text)
print(emails)   # ['admin@example.com', 'support@example.org']
```

### Validating Format (e.g., basic IP shape check)

```python
import re

def looks_like_ip(text):
    pattern = r"^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}$"
    return re.match(pattern, text) is not None

print(looks_like_ip("192.168.1.1"))   # True
print(looks_like_ip("hello"))          # False
```

### Replacing Text

```python
import re

log_line = "User password=hunter2 logged in"
masked = re.sub(r"password=\S+", "password=****", log_line)
print(masked)   # User password=**** logged in
```

## Assignments

1. **Easy:** Write a regex that finds all numbers in the string
   `"Ports open: 22, 80, 443"` and print them as a list of strings.

2. **Easy:** Write a regex to check if a string matches a simple username pattern:
   letters, digits, and underscores only, 3–16 characters long.

3. **Medium:** Given a chunk of text with multiple URLs, e.g.
   `"Visit http://example.com or https://test.org/page"`, extract all URLs using
   `re.findall`.

4. **Medium:** Write a function `extract_domains(text)` that finds all email
   addresses in `text` and returns just the domain part (the part after `@`) as a
   list, with duplicates removed (use a set).

5. **Hard:** You have a server log with lines like:
   ```
   [2024-05-01 10:22:31] FAILED login attempt from 192.168.1.5 for user 'admin'
   [2024-05-01 10:22:45] SUCCESS login from 192.168.1.9 for user 'root'
   ```
   Write a regex with **groups** (using parentheses) that captures the timestamp,
   status (FAILED/SUCCESS), IP address, and username from each line in one match.
   Print all four captured pieces for each line. (Hint: `match.group(1)`,
   `match.group(2)`, etc.)
-e 

---

# 2. Working with APIs and HTTP Requests

## What you'll learn
How to talk to websites and APIs using Python — the foundation of web recon, bug
bounty automation, and checking security headers.

## Explanation

Install the `requests` library first:

```bash
pip install requests
```

### Making a Basic GET Request

```python
import requests

response = requests.get("https://httpbin.org/get")
print(response.status_code)   # 200 means success
print(response.text[:200])    # first 200 characters of the response
```

### Common Status Codes to Know

| Code | Meaning |
|------|---------|
| 200 | OK — success |
| 301/302 | Redirect |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Server Error |

### Reading Response Headers (important for security checks!)

```python
import requests

response = requests.get("https://example.com")
print(response.headers)

# Check for a specific security header
if "Content-Security-Policy" in response.headers:
    print("CSP header is present")
else:
    print("Missing Content-Security-Policy header!")
```

### Sending Data with a POST Request

```python
import requests

data = {"username": "test", "password": "test123"}
response = requests.post("https://httpbin.org/post", data=data)
print(response.status_code)
```

### Adding Custom Headers (e.g., a User-Agent)

```python
import requests

headers = {"User-Agent": "MyLearningTool/1.0"}
response = requests.get("https://httpbin.org/headers", headers=headers)
print(response.json())
```

### Setting a Timeout (always do this!)

Without a timeout, your script can hang forever on a slow or unresponsive server.

```python
import requests

try:
    response = requests.get("https://example.com", timeout=5)
    print(response.status_code)
except requests.exceptions.Timeout:
    print("Request timed out")
except requests.exceptions.RequestException as error:
    print(f"Request failed: {error}")
```

### Working with JSON APIs

```python
import requests

response = requests.get("https://api.github.com")
data = response.json()          # parses JSON into a Python dict
print(data.get("current_user_url"))
```

## Assignments

1. **Easy:** Send a GET request to `"https://httpbin.org/get"` and print the status
   code and the `Content-Type` header.

2. **Easy:** Send a GET request with a custom `User-Agent` header to
   `"https://httpbin.org/headers"` and print the JSON response.

3. **Medium:** Write a function `get_status(url)` that sends a GET request (with a
   5-second timeout) and returns the status code, or `None` if the request fails.
   Test it against 2–3 different real URLs.

4. **Medium:** Write a function `check_security_headers(url)` that requests a URL
   and checks whether `"X-Frame-Options"`, `"Strict-Transport-Security"`, and
   `"Content-Security-Policy"` are present in the response headers. Print which ones
   are missing.

5. **Hard:** Write a script that requests a public JSON API of your choice (e.g.,
   `"https://api.github.com/users/octocat"`), parses the JSON, and prints 3 specific
   fields from it nicely formatted. Wrap all network calls in proper
   `try/except` blocks.
-e 

---

# 3. JSON and Data Parsing

## What you'll learn
How to read and write JSON — nearly every security API (Shodan, VirusTotal, bug
bounty platforms) returns data in JSON format.

## Explanation

JSON looks a lot like a Python dictionary:

```json
{
  "ip": "192.168.1.10",
  "open_ports": [22, 80, 443],
  "is_vulnerable": false
}
```

### Parsing a JSON String Into Python

```python
import json

json_text = '{"ip": "192.168.1.10", "open_ports": [22, 80, 443]}'
data = json.loads(json_text)

print(data["ip"])           # 192.168.1.10
print(data["open_ports"])   # [22, 80, 443]
print(type(data))           # <class 'dict'>
```

### Converting Python Data Into JSON

```python
import json

scan_result = {
    "ip": "192.168.1.10",
    "open_ports": [22, 443],
    "is_vulnerable": False
}

json_text = json.dumps(scan_result, indent=2)
print(json_text)
```

### Reading and Writing JSON Files

```python
import json

# Save results to a file
with open("scan_results.json", "w") as file:
    json.dump(scan_result, file, indent=2)

# Load results back
with open("scan_results.json", "r") as file:
    loaded_data = json.load(file)
    print(loaded_data)
```

### Working with JSON from an API

```python
import requests

response = requests.get("https://api.github.com/users/octocat")
data = response.json()   # requests parses JSON for you automatically

print(data["login"])
print(data["public_repos"])
```

### Safely Accessing Keys That Might Not Exist

```python
# This crashes if "email" is missing:
# print(data["email"])

# This is safer:
print(data.get("email", "No email provided"))
```

## Assignments

1. **Easy:** Create a Python dictionary representing a scan result (ip, port, status)
   and convert it to a JSON string using `json.dumps()`. Print it.

2. **Easy:** Take a JSON string of your choice and parse it back into a Python
   dictionary using `json.loads()`. Print one of its values.

3. **Medium:** Write a list of 3 dictionaries, each representing a different scan
   result. Save the whole list to a file `results.json` using `json.dump()`, with
   `indent=2` for readability.

4. **Medium:** Read `results.json` back, loop through the list, and print a
   formatted summary line for each entry using an f-string.

5. **Hard:** Call a real public JSON API (e.g.
   `"https://api.github.com/repos/psf/requests"`), parse the response, and safely
   extract `"stargazers_count"`, `"open_issues_count"`, and `"license"` (which is a
   nested dictionary — use `.get()` carefully in case it's `None`). Print a short
   report.
-e 

---

# 4. Sockets Basics

## What you'll learn
How computers actually talk to each other over a network at a low level — this is
the foundation of every port scanner and network tool you'll build.

## ⚠️ Reminder
Only connect to hosts you own or have permission to test. Use `127.0.0.1`
(your own machine, "localhost") or a lab VM for practice.

## Explanation

### What Is a Socket?

A **socket** is an endpoint for sending/receiving data over a network. Think of it
like a phone: you need an IP address (the "phone number") and a port (the
"extension") to reach a specific service on a machine.

### Creating a Basic TCP Socket

```python
import socket

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# AF_INET  = we're using IPv4 addresses
# SOCK_STREAM = we're using TCP (reliable, connection-based)
```

### Checking If a Port Is Open

```python
import socket

def is_port_open(ip, port, timeout=1):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(timeout)
    try:
        sock.connect((ip, port))
        return True
    except (socket.timeout, ConnectionRefusedError, OSError):
        return False
    finally:
        sock.close()

# Try this on your OWN machine only
print(is_port_open("127.0.0.1", 80))
```

### Getting Your Own Hostname and IP

```python
import socket

hostname = socket.gethostname()
local_ip = socket.gethostbyname(hostname)
print(f"Hostname: {hostname}, Local IP: {local_ip}")
```

### Resolving a Domain Name to an IP

```python
import socket

try:
    ip = socket.gethostbyname("example.com")
    print(f"example.com resolves to {ip}")
except socket.gaierror:
    print("Could not resolve that domain")
```

### A Tiny Local Server + Client (great for learning)

**Server (run this first, in one terminal):**

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(("127.0.0.1", 9999))
server.listen(1)
print("Waiting for a connection...")

conn, addr = server.accept()
print(f"Connected by {addr}")
data = conn.recv(1024)
print("Received:", data.decode())
conn.close()
```

**Client (run this in a second terminal, while the server is running):**

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(("127.0.0.1", 9999))
client.send(b"Hello from the client!")
client.close()
```

This mini exercise shows exactly what a "connection" really is — the exact same
mechanism a port scanner uses, just checking whether the `connect()` call succeeds.

## Assignments

1. **Easy:** Use `socket.gethostname()` and `socket.gethostbyname()` to print your
   own machine's hostname and local IP address.

2. **Easy:** Use `socket.gethostbyname()` to resolve 3 different well-known domain
   names (e.g., `google.com`, `github.com`) and print their IPs, handling errors with
   `try/except`.

3. **Medium:** Write the `is_port_open()` function from above and use it to check
   ports `22, 80, 443, 3306` on `127.0.0.1` (your own machine). Print which ones are
   open.

4. **Medium:** Run the tiny server/client example above. Modify the server to send a
   reply back to the client (`conn.send(b"Message received!")`) and have the client
   print it.

5. **Hard:** Combine what you've learned: write a function
   `scan_localhost(ports)` that takes a list of ports, checks each with
   `is_port_open()`, and returns a dictionary like `{22: True, 80: False, ...}`.
   Print a clean report at the end. This is essentially a mini port scanner — you'll
   build the full version in Module 3.
-e 

---

# 5. Multithreading Basics

## What you'll learn
How to do many things at once — checking hundreds of ports one-by-one is painfully
slow, so real scanners check many at the same time using threads.

## Explanation

### The Slow Way (Sequential)

```python
import time

def check_port(port):
    time.sleep(0.5)   # pretend this simulates network delay
    print(f"Checked port {port}")

ports = [21, 22, 80, 443, 8080]

start = time.time()
for port in ports:
    check_port(port)
end = time.time()

print(f"Took {end - start:.2f} seconds")   # ~2.5 seconds
```

### The Fast Way (Using Threads)

```python
import threading
import time

def check_port(port):
    time.sleep(0.5)
    print(f"Checked port {port}")

ports = [21, 22, 80, 443, 8080]
threads = []

start = time.time()
for port in ports:
    thread = threading.Thread(target=check_port, args=(port,))
    threads.append(thread)
    thread.start()

for thread in threads:
    thread.join()   # wait for all threads to finish

end = time.time()
print(f"Took {end - start:.2f} seconds")   # ~0.5 seconds!
```

### Using ThreadPoolExecutor (a cleaner, modern approach)

```python
from concurrent.futures import ThreadPoolExecutor
import time

def check_port(port):
    time.sleep(0.5)
    return f"Port {port} checked"

ports = [21, 22, 80, 443, 8080]

with ThreadPoolExecutor(max_workers=5) as executor:
    results = list(executor.map(check_port, ports))

for result in results:
    print(result)
```

### Why This Matters for Scanning

Checking 1000 ports one at a time (even at a fast 0.1 seconds each) takes 100
seconds. With 50 threads running at once, it can take roughly 2 seconds. This is why
almost every real scanning tool uses threading or async programming.

### A Word of Caution

- Too many threads can overwhelm your own machine or the target — this can look like
  a Denial of Service (DoS) attack, which is illegal without permission.
- Always use a reasonable `max_workers` limit, and only scan systems you're
  authorized to test.

## Assignments

1. **Easy:** Write a function `slow_task(n)` that sleeps for 1 second and then
   prints `"Task n done"`. Run it sequentially for `n` in `[1, 2, 3]` and time how
   long it takes.

2. **Easy:** Run the same 3 tasks using `threading.Thread` instead, and compare the
   total time.

3. **Medium:** Using `ThreadPoolExecutor`, write a function that checks whether 10
   different ports are open on `127.0.0.1` (reuse `is_port_open()` from the sockets
   topic) and prints results as they complete.

4. **Medium:** Add a `max_workers=3` limit to your ThreadPoolExecutor from the
   previous assignment and explain, in a comment, why limiting worker count matters
   when scanning a real target.

5. **Hard:** Build a small multithreaded port scanner: given a target IP and a list
   of 50 ports, scan them all concurrently (max 20 workers) and print a sorted list
   of which ports were open. Time the total scan and compare it (in a comment) to
   how long it would take sequentially.
-e 

---

# 6. Command-Line Tools with argparse

## What you'll learn
How to turn your scripts into real command-line tools that accept arguments — every
professional security tool (nmap, sqlmap, etc.) works this way.

## Explanation

### The Problem With Hardcoded Values

```python
# Bad: you have to edit the code every time you want to scan a new target
target_ip = "192.168.1.10"
```

### The Solution: argparse

```python
import argparse

parser = argparse.ArgumentParser(description="A simple port checker")
parser.add_argument("ip", help="Target IP address")
parser.add_argument("port", type=int, help="Port number to check")

args = parser.parse_args()

print(f"Checking {args.ip} on port {args.port}")
```

Run it from the terminal like this:

```bash
python3 port_checker.py 127.0.0.1 443
```

### Optional Arguments (Flags)

```python
import argparse

parser = argparse.ArgumentParser(description="A simple port scanner")
parser.add_argument("ip", help="Target IP address")
parser.add_argument("--start", type=int, default=1, help="Start port (default: 1)")
parser.add_argument("--end", type=int, default=1024, help="End port (default: 1024)")
parser.add_argument("--verbose", action="store_true", help="Show detailed output")

args = parser.parse_args()

print(f"Scanning {args.ip} from port {args.start} to {args.end}")
if args.verbose:
    print("Verbose mode is ON")
```

Run it like:

```bash
python3 scanner.py 192.168.1.10 --start 20 --end 100 --verbose
```

### Handling a List of Values

```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument("--ports", nargs="+", type=int, help="List of ports to scan")

args = parser.parse_args()
print(args.ports)   # e.g., [22, 80, 443]
```

```bash
python3 scanner.py --ports 22 80 443
```

### Auto-Generated Help Text

argparse automatically creates a `--help` flag for you:

```bash
python3 scanner.py --help
```

## Assignments

1. **Easy:** Write a script that accepts a single required argument, `url`, and
   prints `"Checking <url>..."`.

2. **Easy:** Add an optional `--timeout` argument (integer, default `5`) to the
   script above, and print the timeout value being used.

3. **Medium:** Write a script `port_check.py` that takes a required `ip` argument
   and a required `port` argument, then uses the `is_port_open()` function from the
   sockets topic to check and print the result.

4. **Medium:** Extend the script to accept `--ports` as a list of integers (using
   `nargs="+"`) instead of a single port, and check all of them.

5. **Hard:** Build a small CLI tool `mini_scanner.py` that accepts:
   - a required `target` (IP address)
   - an optional `--start` and `--end` for a port range (defaults 1 and 1024)
   - an optional `--threads` (default 20) controlling how many `ThreadPoolExecutor`
     workers to use

   It should scan the given range using threading and print all open ports found,
   along with the total time taken.
-e 

---

# MODULE 3: CYBERSECURITY PYTHON APPLICATIONS

# 1. Building a Simple, Safe Port Scanner

## What you'll learn
How to build a real (basic) port scanner from scratch, combining sockets, loops,
functions, error handling, and threading from earlier modules.

## ⚠️ Legal Reminder
Only scan:
- `127.0.0.1` / `localhost` (your own machine)
- A lab VM you set up yourself (e.g., Metasploitable, DVWA)
- A target explicitly listed as in-scope in a bug bounty program

Port scanning systems without permission is illegal in most countries.

## Explanation

### Step 1: Check a Single Port

```python
import socket

def scan_port(ip, port, timeout=1):
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(timeout)
    try:
        result = sock.connect_ex((ip, port))   # returns 0 if the port is open
        return result == 0
    finally:
        sock.close()

print(scan_port("127.0.0.1", 80))
```

`connect_ex()` is often preferred over `connect()` for scanning because it returns an
error code instead of raising an exception, which is a bit cleaner for looping over
many ports.

### Step 2: Scan a Range of Ports

```python
def scan_range(ip, start_port, end_port):
    open_ports = []
    for port in range(start_port, end_port + 1):
        if scan_port(ip, port):
            open_ports.append(port)
            print(f"Port {port}: OPEN")
    return open_ports

open_ports = scan_range("127.0.0.1", 1, 100)
print("Open ports:", open_ports)
```

### Step 3: Speed It Up with Threading

```python
from concurrent.futures import ThreadPoolExecutor

def scan_ports_threaded(ip, ports, max_workers=20):
    open_ports = []

    def check(port):
        if scan_port(ip, port):
            open_ports.append(port)

    with ThreadPoolExecutor(max_workers=max_workers) as executor:
        executor.map(check, ports)

    return sorted(open_ports)

ports_to_check = list(range(1, 1025))
result = scan_ports_threaded("127.0.0.1", ports_to_check)
print("Open ports:", result)
```

### Step 4: Try to Identify the Service (Banner Grabbing)

Some services announce themselves when you connect — this is called "banner
grabbing" and is a real recon technique.

```python
import socket

def grab_banner(ip, port, timeout=2):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(timeout)
        sock.connect((ip, port))
        banner = sock.recv(1024).decode(errors="ignore").strip()
        sock.close()
        return banner
    except Exception:
        return None

banner = grab_banner("127.0.0.1", 22)
print("Banner:", banner)
```

### Putting It All Together

```python
def full_scan(ip, start_port, end_port):
    ports = list(range(start_port, end_port + 1))
    open_ports = scan_ports_threaded(ip, ports)

    print(f"\nScan results for {ip}:")
    for port in open_ports:
        banner = grab_banner(ip, port)
        banner_text = f" — {banner}" if banner else ""
        print(f"  Port {port}: OPEN{banner_text}")

    return open_ports

# full_scan("127.0.0.1", 1, 1024)
```

## Assignments

1. **Easy:** Write the `scan_port()` function and test it against 3 ports on
   `127.0.0.1` — one you expect to be open, two you expect to be closed.

2. **Easy:** Write `scan_range()` and run it on `127.0.0.1` for ports 1–50. Print how
   many were open.

3. **Medium:** Add threading to your scanner using `ThreadPoolExecutor` and compare
   the time taken for scanning ports 1–1024 with and without threading (use the
   `time` module).

4. **Medium:** Add banner grabbing to your scanner so that for every open port, it
   also tries to print the service banner (if any).

5. **Hard:** Turn your scanner into a command-line tool using `argparse` (from
   Module 2) that accepts `target`, `--start`, `--end`, and `--threads`. Save the
   results to a JSON file using the `json` module, with each entry containing the
   port number, whether it's open, and the banner (if found).
-e 

---

# 2. Web Scraping for Recon

## What you'll learn
How to automatically pull useful information out of web pages — emails, links,
comments, hidden form fields — a core part of the reconnaissance phase in ethical
hacking and bug bounty hunting.

## ⚠️ Legal Reminder
Only scrape sites you own, or sites that explicitly allow it in their
`robots.txt` / terms of service / bug bounty scope. Aggressive scraping can also
overload a server — always add delays between requests.

## Explanation

Install the tools:

```bash
pip install requests beautifulsoup4
```

### Step 1: Fetch a Page

```python
import requests

response = requests.get("https://example.com", timeout=5)
html = response.text
print(html[:300])
```

### Step 2: Parse HTML with BeautifulSoup

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html, "html.parser")
print(soup.title.text)   # the page's <title>
```

### Step 3: Extract All Links (Great for Mapping a Site)

```python
links = soup.find_all("a")
for link in links:
    href = link.get("href")
    if href:
        print(href)
```

### Step 4: Extract All Emails on a Page

Combine web scraping with regex (from Module 2):

```python
import re

emails = re.findall(r"[\w\.-]+@[\w\.-]+\.\w+", html)
unique_emails = set(emails)
print(unique_emails)
```

### Step 5: Look for Interesting Comments or Hidden Fields

Developers sometimes leave debug info, API keys, or notes in HTML comments — a
classic (and simple) bug bounty finding.

```python
comments = soup.find_all(string=lambda text: isinstance(text, str) and "<!--" in str(text))
# A more reliable way using html.parser internals:
from bs4 import Comment
comments = soup.find_all(string=lambda text: isinstance(text, Comment))
for comment in comments:
    print("Comment found:", comment)
```

### Step 6: Check Hidden Form Fields

```python
forms = soup.find_all("form")
for form in forms:
    hidden_inputs = form.find_all("input", type="hidden")
    for hidden in hidden_inputs:
        print("Hidden field:", hidden.get("name"), "=", hidden.get("value"))
```

### Being a Good, Careful Scraper

```python
import time
import requests

pages = ["https://example.com/page1", "https://example.com/page2"]

for page in pages:
    response = requests.get(page, timeout=5)
    print(page, response.status_code)
    time.sleep(1)   # be polite — don't hammer the server with requests
```

### Checking robots.txt First

```python
import requests

robots = requests.get("https://example.com/robots.txt", timeout=5)
print(robots.text)
```

## Assignments

1. **Easy:** Fetch a public page of your choice and print its `<title>` using
   BeautifulSoup.

2. **Easy:** Extract and print all the links (`<a href="...">`) from that same page.

3. **Medium:** Write a function `find_emails_on_page(url)` that fetches a page and
   returns a set of unique emails found on it, using regex.

4. **Medium:** Write a function `find_hidden_inputs(url)` that fetches a page and
   prints the name and value of every hidden form field it finds.

5. **Hard:** Write a simple crawler that starts at one URL, extracts all links on
   that page that point to the SAME domain, visits each of them (with a 1-second
   delay between requests), and builds a set of all unique pages visited. Print the
   final list. Add a safety limit (e.g., stop after visiting 10 pages) so it can't
   run forever.
-e 

---

# 3. Password Strength Checkers and Hashing

## What you'll learn
How passwords are stored securely (hashing), how to check password strength, and why
this matters for both defenders and ethical hackers.

## Explanation

### What Is Hashing?

Hashing turns any input into a fixed-length string of characters. It's **one-way** —
you can't reverse a hash back into the original text. This is why websites store
password *hashes*, not the actual passwords.

```python
import hashlib

password = "hunter2"
hashed = hashlib.sha256(password.encode()).hexdigest()
print(hashed)
# always the same output for the same input:
# c2a91d1c... (example)
```

### Why Not MD5?

```python
import hashlib

# MD5 is fast but considered BROKEN for security purposes (collisions exist)
weak_hash = hashlib.md5(b"hunter2").hexdigest()
print(weak_hash)

# SHA-256 is much stronger
strong_hash = hashlib.sha256(b"hunter2").hexdigest()
print(strong_hash)
```

Never use MD5 or plain SHA-256 alone for storing real passwords in production —
proper systems use algorithms designed for passwords specifically, like `bcrypt` or
`argon2`, which add "salt" and deliberate slowness. We mention this so you understand
*why* those tools exist.

### A Simple Password Strength Checker

```python
def check_password_strength(password):
    score = 0
    feedback = []

    if len(password) >= 12:
        score += 2
    elif len(password) >= 8:
        score += 1
    else:
        feedback.append("Too short — use at least 8 characters")

    if any(char.isdigit() for char in password):
        score += 1
    else:
        feedback.append("Add at least one number")

    if any(char.isupper() for char in password):
        score += 1
    else:
        feedback.append("Add at least one uppercase letter")

    if any(char in "!@#$%^&*()_+-=" for char in password):
        score += 1
    else:
        feedback.append("Add at least one special character")

    if score >= 4:
        rating = "Strong"
    elif score >= 2:
        rating = "Medium"
    else:
        rating = "Weak"

    return rating, feedback

rating, feedback = check_password_strength("hunter2")
print(rating, feedback)
```

### Checking Against a Common Password List

Bug bounty and pentesting work often involves checking if a password appears in a
list of known-leaked/common passwords.

```python
common_passwords = {"123456", "password", "qwerty", "letmein", "hunter2"}

def is_common_password(password):
    return password.lower() in common_passwords

print(is_common_password("hunter2"))   # True
```

### Verifying a Password Against a Stored Hash

```python
import hashlib

def verify_password(password, stored_hash):
    return hashlib.sha256(password.encode()).hexdigest() == stored_hash

stored_hash = hashlib.sha256("hunter2".encode()).hexdigest()
print(verify_password("hunter2", stored_hash))   # True
print(verify_password("wrongpass", stored_hash)) # False
```

## Assignments

1. **Easy:** Hash the string `"mypassword"` using both MD5 and SHA-256. Print both
   hashes and note how different (and longer) the SHA-256 output is.

2. **Easy:** Write `check_password_strength()` and test it with 3 different
   passwords: a weak one, a medium one, and a strong one.

3. **Medium:** Write a function `hash_wordlist(words)` that takes a list of plain
   passwords and returns a dictionary mapping each password to its SHA-256 hash.
   This simulates how a defender might prepare known-hash lookups for detection.

4. **Medium:** Given a small list of common passwords (create your own list of 10),
   write a function that checks whether a user-supplied password appears in that
   list, case-insensitively, and warns the user if so.

5. **Hard:** Write a small educational tool that:
   - Takes a plain password from the user.
   - Hashes it with SHA-256 and "stores" it in a Python dictionary keyed by a
     username.
   - Later takes a login attempt (username + password) and checks it against the
     stored hash to simulate a login system.

   Add a comment explaining why real systems also use "salting" (adding random data
   before hashing) to prevent attackers from using precomputed hash tables (called
   "rainbow tables").
-e 

---

# 4. HTTP Header Security Checker

## What you'll learn
How to check a website's HTTP response headers for common security misconfigurations
— a real, everyday task in bug bounty hunting and web security audits.

## ⚠️ Legal Reminder
Only run this against sites you own or that are explicitly in scope for testing
(most bug bounty programs allow passive checks like this, but always read the
program's rules first).

## Explanation

### Important Security Headers to Know

| Header | What it protects against |
|--------|---------------------------|
| `Strict-Transport-Security` (HSTS) | Forces browsers to use HTTPS |
| `Content-Security-Policy` (CSP) | Reduces XSS (cross-site scripting) risk |
| `X-Frame-Options` | Prevents clickjacking |
| `X-Content-Type-Options` | Stops browsers from "guessing" file types (MIME sniffing) |
| `Referrer-Policy` | Controls what URL info is leaked to other sites |
| `Permissions-Policy` | Controls which browser features a page can use |

### Fetching and Inspecting Headers

```python
import requests

def get_headers(url):
    response = requests.get(url, timeout=5)
    return response.headers

headers = get_headers("https://example.com")
for name, value in headers.items():
    print(f"{name}: {value}")
```

### Checking for Missing Security Headers

```python
import requests

IMPORTANT_HEADERS = [
    "Strict-Transport-Security",
    "Content-Security-Policy",
    "X-Frame-Options",
    "X-Content-Type-Options",
    "Referrer-Policy",
]

def check_security_headers(url):
    response = requests.get(url, timeout=5)
    missing = []

    for header in IMPORTANT_HEADERS:
        if header not in response.headers:
            missing.append(header)

    return missing

missing = check_security_headers("https://example.com")
if missing:
    print("Missing security headers:")
    for header in missing:
        print(f"  - {header}")
else:
    print("All checked security headers are present!")
```

### Checking Server Version Disclosure

Sometimes servers reveal software versions, which attackers can use to look up known
vulnerabilities.

```python
import requests

response = requests.get("https://example.com", timeout=5)
server_header = response.headers.get("Server")

if server_header:
    print(f"Server header reveals: {server_header}")
    print("Consider hiding version info in production.")
else:
    print("No Server header disclosed — good practice.")
```

### Checking for a Secure Cookie Configuration

```python
import requests

response = requests.get("https://example.com", timeout=5)
for cookie in response.cookies:
    print(f"Cookie: {cookie.name}")
    print(f"  Secure flag: {cookie.secure}")
    print(f"  HttpOnly flag: {'httponly' in [k.lower() for k in cookie._rest.keys()]}")
```

### Building a Small Report

```python
def generate_report(url):
    print(f"\n=== Security Header Report for {url} ===")
    missing = check_security_headers(url)

    if not missing:
        print("✅ All key security headers are present.")
    else:
        print("⚠️  Missing headers:")
        for header in missing:
            print(f"   - {header}")

generate_report("https://example.com")
```

## Assignments

1. **Easy:** Fetch the headers of a real website (with permission — e.g., your own
   site or a public test site like `https://httpbin.org`) and print all headers.

2. **Easy:** Write `check_security_headers()` and test it against 2 different
   websites. Compare the results.

3. **Medium:** Extend the checker to also report the `Server` header value if
   present, and note it as an "informational" finding rather than a pass/fail.

4. **Medium:** Write a function `check_cookie_security(url)` that inspects cookies
   set by a response and flags any cookie that's missing the `Secure` or `HttpOnly`
   attribute.

5. **Hard:** Build a full command-line tool (using `argparse`) called
   `header_checker.py` that accepts a `url` argument, runs all the checks above
   (missing headers, server disclosure, cookie security), and prints a clean,
   organized report. Save the report as a JSON file as well, so it could be attached
   to a bug bounty submission.
-e 

---

# 5. Subdomain Enumeration

## What you'll learn
How to find subdomains of a target — one of the very first steps in almost every
bug bounty engagement, since more subdomains = more potential attack surface.

## ⚠️ Legal Reminder
Only enumerate subdomains for domains you own, or that are explicitly in scope for a
bug bounty program you're participating in.

## Explanation

There are two common beginner-friendly approaches: using a **public data source**
(passive, safe, no direct contact with the target) and using a **wordlist + DNS
lookups** (semi-active).

### Method 1: Passive — Using crt.sh (Certificate Transparency Logs)

Every time an HTTPS certificate is issued for a domain, it's logged publicly. This
means we can find subdomains just by reading public certificate records — without
ever sending traffic to the target itself.

```python
import requests

def get_subdomains_from_crtsh(domain):
    url = f"https://crt.sh/?q=%25.{domain}&output=json"
    try:
        response = requests.get(url, timeout=10)
        data = response.json()
    except (requests.exceptions.RequestException, ValueError):
        return set()

    subdomains = set()
    for entry in data:
        name_value = entry.get("name_value", "")
        for name in name_value.split("\n"):
            if domain in name:
                subdomains.add(name.strip().lower())

    return subdomains

subdomains = get_subdomains_from_crtsh("example.com")
for sub in sorted(subdomains):
    print(sub)
```

### Method 2: Semi-Active — DNS Resolution with a Wordlist

This method guesses common subdomain names and checks if they resolve to an IP.
This DOES send DNS queries, so only use it on domains you're authorized to test.

```python
import socket

common_words = ["www", "mail", "api", "dev", "staging", "admin", "test", "shop"]

def find_subdomains_by_wordlist(domain, wordlist):
    found = []
    for word in wordlist:
        candidate = f"{word}.{domain}"
        try:
            ip = socket.gethostbyname(candidate)
            found.append((candidate, ip))
            print(f"Found: {candidate} -> {ip}")
        except socket.gaierror:
            pass   # doesn't exist, that's fine
    return found

results = find_subdomains_by_wordlist("example.com", common_words)
```

### Combining Both Methods and Removing Duplicates

```python
def full_subdomain_recon(domain, wordlist):
    passive_results = get_subdomains_from_crtsh(domain)
    active_results = {sub for sub, ip in find_subdomains_by_wordlist(domain, wordlist)}

    all_subdomains = passive_results | active_results   # set union
    return sorted(all_subdomains)

results = full_subdomain_recon("example.com", common_words)
print(f"\nTotal unique subdomains found: {len(results)}")
for sub in results:
    print(sub)
```

### Saving Results for a Report

```python
import json

def save_results(domain, subdomains, filename="subdomains.json"):
    report = {"domain": domain, "subdomains": subdomains, "count": len(subdomains)}
    with open(filename, "w") as file:
        json.dump(report, file, indent=2)

save_results("example.com", results)
```

## Assignments

1. **Easy:** Write `get_subdomains_from_crtsh()` and run it against a real domain of
   your choice (e.g., a company with a public bug bounty program). Print all
   subdomains found.

2. **Easy:** Write a wordlist of 10 common subdomain prefixes and use
   `find_subdomains_by_wordlist()` to test them against a domain you're allowed to
   query.

3. **Medium:** Combine passive and active results into one clean, deduplicated,
   sorted list using sets (as shown above), and print the total count.

4. **Medium:** Extend the crt.sh function to filter out wildcard entries (ones that
   start with `*.`) since those aren't real hostnames you can visit directly.

5. **Hard:** Build a small tool that takes a `domain` as a command-line argument
   (using `argparse`), runs the passive crt.sh lookup, then for each discovered
   subdomain, uses `requests` (with a timeout) to check if it responds on port 80/443
   and what HTTP status code it returns. Save a full JSON report including domain,
   HTTP status, and whether HTTPS is available.
-e 

---

# 6. Packet Sniffing Basics (Scapy)

## What you'll learn
How network traffic actually looks at the packet level, and how to inspect it using
Python — a core skill for understanding attacks and defenses at the network layer.

## ⚠️ Very Important Legal Reminder
Packet sniffing captures **real network traffic**, potentially including other
people's data. Only sniff:
- Your **own** home network, with devices you own
- A traffic capture file (`.pcap`) that is publicly available for learning, or one
  you created yourself
- An isolated lab network you built (e.g., a VirtualBox lab)

Sniffing other people's traffic without consent is illegal in most countries, even on
shared networks (like a coffee shop Wi-Fi). This topic is for **understanding your
own systems and consented lab environments only**.

## Explanation

Install Scapy:

```bash
pip install scapy
```

On Linux/macOS, sniffing usually requires running Python with elevated permissions
(e.g., `sudo python3 script.py`) because reading raw network packets needs special
access.

### Sniffing a Few Packets

```python
from scapy.all import sniff

def show_packet(packet):
    print(packet.summary())

# Capture 5 packets on your own network interface, then stop
sniff(count=5, prn=show_packet)
```

### Filtering by Protocol (e.g., only look at DNS traffic)

```python
from scapy.all import sniff

def show_dns(packet):
    if packet.haslayer("DNS"):
        print(packet.summary())

sniff(filter="udp port 53", prn=show_dns, count=5)
```

The `filter` argument uses BPF (Berkeley Packet Filter) syntax, the same syntax
tools like Wireshark and tcpdump use.

### Inspecting Packet Layers

```python
from scapy.all import sniff, IP, TCP

def inspect_packet(packet):
    if packet.haslayer(IP):
        src_ip = packet[IP].src
        dst_ip = packet[IP].dst
        print(f"{src_ip} -> {dst_ip}")

        if packet.haslayer(TCP):
            print(f"  TCP port: {packet[TCP].dport}")

sniff(count=5, prn=inspect_packet)
```

### Reading From a Saved Capture File (.pcap) — Safer for Practice

Instead of live-sniffing, you can practice on a `.pcap` file (many free sample
captures exist online for learning purposes).

```python
from scapy.all import rdpcap

packets = rdpcap("sample_capture.pcap")
print(f"Total packets: {len(packets)}")

for packet in packets[:5]:
    print(packet.summary())
```

### Building a Simple Traffic Counter

```python
from scapy.all import sniff, IP

traffic_count = {}

def count_traffic(packet):
    if packet.haslayer(IP):
        src = packet[IP].src
        traffic_count[src] = traffic_count.get(src, 0) + 1

sniff(count=20, prn=count_traffic)

print("\nPackets seen per source IP:")
for ip, count in sorted(traffic_count.items(), key=lambda item: -item[1]):
    print(f"{ip}: {count} packets")
```

This same technique (counting packets per source) is the basic idea behind simple
DoS/flood detection.

## Assignments

1. **Easy:** Install Scapy and run the basic sniff example on your own network,
   capturing 5 packets. Print a summary of each.

2. **Easy:** Modify the sniff filter to capture only traffic on port 80 (HTTP) and
   run it while browsing a non-HTTPS site in another window (or use
   `filter="tcp"` more broadly if you don't have one handy).

3. **Medium:** Write a function that sniffs 10 packets and prints, for each one that
   has an IP layer, the source IP, destination IP, and protocol name (hint: check
   `packet[IP].proto` or use `packet.haslayer(TCP)` / `packet.haslayer(UDP)`).

4. **Medium:** Find a small public `.pcap` sample file made for learning purposes,
   read it with `rdpcap()`, and print how many packets involve TCP versus UDP.

5. **Hard:** Build the "traffic counter" from above into a small monitoring script
   that sniffs for 30 seconds (hint: look up the `timeout` parameter of `sniff()`)
   and then prints a sorted report of which source IPs sent the most packets —
   explain in a comment how this basic idea scales up into real intrusion detection
   systems (IDS).
-e 

---

# MODULE 4: PROJECTS

# Projects: Beginner to Advanced

Now that you've worked through the topic files, it's time to build complete, working
tools. Each project lists its goal, the skills it uses, and suggestions to extend it
further. Build them in order — each one reuses skills from the last.

## ⚠️ Reminder
Every project below must only be run against systems you own, a personal lab
(virtual machines, `127.0.0.1`), or targets explicitly in scope for a bug bounty
program. Never test systems without permission.

---

## 🟢 Beginner Projects

### 1. Password Strength Analyzer
**Goal:** Build a command-line tool that takes a password and rates it Weak /
Medium / Strong, explaining what's missing.
**Skills used:** strings, functions, control structures, `argparse`
**Stretch goal:** Check the password against a small list of common leaked
passwords and warn the user if it's found.

### 2. Simple Port Checker
**Goal:** Given an IP and a single port, report whether it's open or closed.
**Skills used:** sockets, error handling, functions
**Stretch goal:** Accept a comma-separated list of ports instead of just one.

### 3. IP and Domain Info Tool
**Goal:** Given a domain name, resolve it to an IP address and print basic info
(hostname, resolved IP, whether it responds on port 80/443).
**Skills used:** sockets, `requests`, error handling
**Stretch goal:** Add a `--whois` style lookup using a public WHOIS API.

### 4. Log File Analyzer (Failed Logins)
**Goal:** Read a sample log file of login attempts and report the number of
failed attempts per IP address, flagging any IP with more than 3 failures as
"suspicious."
**Skills used:** file handling, dictionaries, string parsing
**Stretch goal:** Add a `--top N` flag to show only the top N most suspicious IPs.

---

## 🟡 Intermediate Projects

### 5. Multithreaded Port Scanner
**Goal:** Build a full port scanner: accepts a target and a port range via
`argparse`, scans using threads, and prints all open ports with optional banner
grabbing.
**Skills used:** sockets, threading, `argparse`, error handling
**Stretch goal:** Save results to a JSON report file.

### 6. HTTP Security Header Auditor
**Goal:** Given a URL, fetch it and report which important security headers
(CSP, HSTS, X-Frame-Options, etc.) are missing, plus any version-disclosing
headers.
**Skills used:** `requests`, dictionaries, functions
**Stretch goal:** Accept a list of URLs from a file and audit all of them, saving
one combined report.

### 7. Basic Web Recon Tool (Emails + Links + Comments)
**Goal:** Given a URL, extract all email addresses, all links, and any HTML
comments found on the page.
**Skills used:** `requests`, BeautifulSoup, regular expressions
**Stretch goal:** Follow links on the same domain (up to a safe limit) and combine
results across pages.

### 8. Subdomain Finder
**Goal:** Given a domain, use the crt.sh passive method to find subdomains, then
check which ones respond over HTTP/HTTPS, printing status codes.
**Skills used:** `requests`, JSON parsing, sets, sockets
**Stretch goal:** Add a wordlist-based active check as a second method and merge
both result sets.

---

## 🔴 Advanced Projects

### 9. Full Recon Automation Tool
**Goal:** Combine subdomain enumeration + port scanning + HTTP header auditing
into one tool: given a root domain, it should (1) find subdomains, (2) scan common
ports on each live subdomain, and (3) audit HTTP security headers on any that
serve a web page. Output one combined JSON/HTML report.
**Skills used:** everything from Modules 1–3, OOP (organize results as classes),
threading, `argparse`
**Stretch goal:** Add colorized terminal output (using a library like `rich`) and
a simple HTML report generator.

### 10. Brute-Force Login Simulator (Defensive Learning Tool)
**Goal:** Build a **local, self-contained** simulator: a tiny fake login "server"
(just a Python function comparing against a hardcoded hash) and a client that
tries passwords from a wordlist against it, timing how long a real brute-force
would take. Use this to understand WHY rate limiting and account lockouts exist —
this is a defensive learning exercise, not a tool for attacking real accounts.
**Skills used:** hashing, file handling, loops, timing, OOP
**Stretch goal:** Add a lockout mechanism after N failed attempts and show how it
stops the brute-force attempt.

### 11. Network Traffic Analyzer
**Goal:** Using Scapy on your own network (or a sample `.pcap` file), build a tool
that summarizes traffic: top source IPs, protocol breakdown (TCP/UDP/DNS), and
flags any single IP that sends an unusually high number of packets in a short
time window (a simple flood/DoS detector).
**Skills used:** Scapy, dictionaries, OOP, threading (optional)
**Stretch goal:** Export findings to a CSV file and generate a simple chart of
traffic over time (using `matplotlib`, if available).

### 12. Capstone: Mini Bug Bounty Toolkit
**Goal:** Package several of the tools above into ONE command-line toolkit with
subcommands, e.g.:
```bash
python3 toolkit.py subdomains example.com
python3 toolkit.py scan 127.0.0.1 --start 1 --end 1024
python3 toolkit.py headers https://example.com
python3 toolkit.py recon example.com --full
```
**Skills used:** OOP, `argparse` subparsers, everything from this repository
**Stretch goal:** Add a config file (JSON or `.env`) for default settings like
timeout values and thread counts, and write a short `README.md` for your toolkit
explaining how to use it — you're now writing documentation like a real open-source
project maintainer!

---

## How to Approach Each Project

1. Write down the project's steps in plain English first (pseudocode).
2. Build the smallest working version first (even if it's ugly).
3. Test it against `127.0.0.1` or a safe target before anything else.
4. Refactor: break it into functions (and later classes), add error handling.
5. Add the "stretch goal" once the base version works reliably.

Good luck — building these projects is what turns "I learned Python" into
"I can build my own security tools."
