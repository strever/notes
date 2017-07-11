# Unicode“字符集”和UTF-8“编码”

UTF-8 and Unicode cannot be compared. UTF-8 is an encoding used to translate binary data into numbers. Unicode is a character set used to translate numbers into characters.

首先来说，Unicode和UTF-8是没有可比性的！

Unicode characters set， 顾名思义它是一个字符集，不存在任何的编码，一个字符对应一个code point，’A‘就是U+0041（65），‘平’就是U+5E73（24179），’安‘就是U+5B89（23433），如此而已。

而为了方便计算机存储和表示Unicode code point，我们需要对Unicode code point进行编码，而UTF-8就是其中一种。

如果不使用UTF-8，可能会让老美不爽，因为他们觉得01000001就够了， 为啥要弄成0000000001000001（U+0041），要这么多0干什么。

UTF-8解决了这个问题，也节省了空间, code point在 0-127 UTF-8会只用一个字节. code points在128或更大时UTF-8会使用2-6个字节.

现在上例子

平安的Unicode code point

平                                    
U+5E73                               
24179  

||||
|---:|---:|---:|
|0101|111001|110011|
|11100101|10111001|10110011|
|E5|B9|B3|


	 
可能你已经发现了一些规律，是的没错，3字节时，我们将UTF-8编码的二进制按照格式「1110XXXX 10XXXXXX 10XXXXXX」除掉标志位，即得到了真实的Unicode code point

附UTF-8的编码规则
