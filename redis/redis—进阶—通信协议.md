- RESP 是 Redis 序列化协议的简写。它是一种直观的文本协议，优势在于实现异常简单，解析性能极好。
- Redis 协议将传输的结构数据分为 5 种最小单元类型，单元结束时统一加上回车换行符号\r\n。
    - 单行字符串 以 + 符号开头。
    - 多行字符串 以 $ 符号开头，后跟字符串长度。
    - 整数值 以 : 符号开头，后跟整数的字符串形式。
    - 错误消息 以 - 符号开头。
    - 数组 以 * 号开头，后跟数组的长度。
### Example：
- 单行字符串 hello world +hello world\r\n 
- 数字 :1024\r\n
