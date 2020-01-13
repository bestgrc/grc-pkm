\\ 反斜杠的使用

java的字符串中，反斜杠有转译的功能，所以在java中使用反斜杠，需要其他语言中两倍的数量。

|         | 其他语言                                   | Java                                             |
| ------- | ------------------------------------------ | ------------------------------------------------ |
| \       | 插入一个正则的反斜杠，其后的字符有特殊意义 | 和其他字符组合，有特殊意义，例如换行\n和制表符\t |
| \\\\    | 插入一个普通反斜杠，无特殊意义             | 插入一个正则的反斜杠，其后的字符有特殊意义       |
| \\\\\\\ |                                            | 插入一个普通反斜杠                               |

String类自带的正则api：

boolean matches(String regex)

String[] split(String splitWord)

replaceFirst(String regex ,String repalcement)/replaceAll(String regex ,String repalcement)

