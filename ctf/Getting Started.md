#### Flag format
In the most common scenario it will look something like "The Flag is: this_is_the_flag", "ctfName{this_is_the_flag}"" or just "this_is_the_flag". Sometimes the organizers will use leetspeak so it will look like "ctfName{th15_15_th3_fl4g}"". Of course not all flags can follow these formats, so always be looking for anything out of place, especially during forensics challenges. Most problems will specify the flag format, but if they do not, you must be on the lookout for any ambiguity.

Always check for:
- Capitalization
- Character encoding
- Trailing whitespaces/newlines
- Date/Time formats
- Hex address formats (0x0042 vs 0042 vs 00000042)

