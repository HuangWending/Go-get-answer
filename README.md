# Go-get-answer
Go问答程序
package main
声明程序所属的包为main。
import (
	"bufio"
	"fmt"
	"os"
	"strings"
)
引入需要使用的包，其中包括bufio用于读取用户输入，fmt用于格式化输入输出，os用于访问操作系统功能，strings用于处理字符串。
func getAnswer(question string) string {
定义了一个名为getAnswer的函数，接收一个字符串类型的参数question，并返回一个字符串作为回答。
	switch question {
	case "你好":
		return "你好"
	case "你的名字是什么":
		return "黄文定"
	case "你的生日是什么时候":
		return "2009年7月18日"
	case "你是中国人吗":
		return "我是中国人"
	case "台湾是中国的吗":
		return "台湾是中国的"
	case "你爱我吗":
		return "这是一个由我决定的选项，我需要认真，但是我还是爱着你"
	case "你喜欢去哪里":
		return "中国大陆和中国台湾"
	case "你有朋友吗":
		return "没有"
	case "你的心情怎么样":
		return "自卑，孤独"
	default:
		return "抱歉，我黄文定无法回答你的问题。"
	}
}
使用switch语句根据question的值进行匹配，并返回相应的回答字符串。
func main() {
	reader := bufio.NewReader(os.Stdin)
创建一个用于读取用户输入的bufio.Reader对象，并将其与标准输入（键盘输入）关联。
	for {
		fmt.Print("请输入你的问题（输入'退出'结束程序）: ")
		userQuestion, _ := reader.ReadString('\n')
		userQuestion = strings.TrimSpace(userQuestion)
使用for循环持续接收用户输入的问题，fmt.Print用于打印提示信息，reader.ReadString('\n')读取用户输入的一行文本，strings.TrimSpace去除输入文本的前后空格。
		if userQuestion == "退出" {
			break
		}
如果用户输入了"退出"，则跳出循环，结束程序。
		response := getAnswer(userQuestion)
		fmt.Println(response)
	}
}
调用getAnswer函数获取回答，并使用fmt.Println打印回答到控制台。然后继续下一次循环，等待用户输入新的问题。
