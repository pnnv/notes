#### Flag format
In the most common scenario it will look something like "The Flag is: this_is_the_flag", "ctfName{this_is_the_flag}"" or just "this_is_the_flag". Sometimes the organizers will use leetspeak so it will look like "ctfName{th15_15_th3_fl4g}"". Of course not all flags can follow these formats, so always be looking for anything out of place, especially during forensics challenges. Most problems will specify the flag format, but if they do not, you must be on the lookout for any ambiguity.

Always check for:
- Capitalization
- Character encoding
- Trailing whitespaces/newlines
- Date/Time formats
- Hex address formats (0x0042 vs 0042 vs 00000042)

#### Things to keep in mind

Anytime you find yourself trying to do any of these things, Assume that you have gone wrong somewhere along the way.

1. Reverse a hash
	- If nothing comes up when you google for it, move on. This is not what you are supposed to solve.
2. Create a hash collision
	- Possible for `MD5` and `SHA1` in various ways. Refer to [this](https://github.com/corkami/collisions).
3. Crack a password that is longer than 8 characters
	- The math just isn't there. You are missing something.
	- That something might be a wordlist gathered from all words on a website/server/description.
4. [Halting Problem](https://en.wikipedia.org/wiki/Halting_problem)
5. [P versus NP problem](https://en.wikipedia.org/wiki/P_versus_NP_problem)