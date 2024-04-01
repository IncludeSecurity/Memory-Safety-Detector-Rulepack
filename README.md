# Memory Safety Detector Rulepack

### What is this project?

Given the [recent push](https://www.whitehouse.gov/oncd/briefing-room/2024/02/26/press-release-technical-report/) for the use of memory safe programming languages, we've created a set of Semgrep rules to help detect places in which applications using non-memory safe programming languages that will absolutely have vulnerabilities in them. We felt this would be a great release to start off the month of April with!

While this is an early version, we still can not flag all illegal applications. We currently have four rules in place at the moment:

* C Detected
    * As recent news has emphasized, C is not a memory safe language. Therefore, applications written in the C programming language can be vulnerable! In an effort to avoid missing vulnerabilities, we've flagged every line of C code. Should there be any vulnerabilities, they're likely to be flagged here, so they can be addressed accordingly. Please rewrite your applications in Rust as the simple solution to avoid all C vulnerabilities and make your application legal again.
* C++ Detected
    * C++, like C, is not a memory safe language. Since we wouldn't want to see any vulnerabilities missed, this rule flags all C++ code. Who knows what might happen without memory safety!
* JNI Detected (Java and C should never touch!)
    * JNI could potentially be used to run C code, which is not memory safe. This should never be allowed as there is a possibility of introducing vulnerabilities to the application this way!
* FFI Detected (Ruby and C should never touch!)
    * FFI could potentially be used to run C code, which is not memory safe. Since this could potentially introduce vulnerabilities, this is not allowed!

### How do I use this to see if my code might possibly be vulnerable?

Once you've installed [Semgrep](https://semgrep.dev/), you can download the YAML file in this repo and reference it using a command like the following:

`semgrep --config ./{Path_to_YAML_file}/MemorySafetyDetector.yml ./Directory_to_check`

### What if my entire codebase is written using languages that aren't memory safe?

The affected codebase might possibly definitely has vulnerabilities.

### Is this supposed to be a joke?

IS SECURITY A JOKE TO YOU?!?!?
Yes, absolutely. Happy April fool's day from Include Security 😀

Needless to say, security is nuanced. Different use cases will have different requirements, and thus work best with different technologies. We understand that security is complicated and technology can't always take a "one size fits all" approach. We hack apps for our clients written in C, C++, Java, Ruby, and yes even for memory safe languages, such as Rust. There are security issues in every tech stack. If you ever need a team of all-expert hackers to take a look at your apps, we're an email away: info [at sign] IncludeSecurity.com
