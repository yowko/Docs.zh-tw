---
redirect_url: /dotnet/articles/csharp/programming-guide/main-and-command-args/
caps.handback.revision: 30
---
# Main() 和命令列引數 (C# 程式設計手冊)
`Main` 方法為 C\# 主控台應用程式 \(Console Application\) 或視窗應用程式的進入點   \(程式庫和服務並不需要 `Main` 方法做為進入點\)。  當應用程式啟動時，`Main` 方法是第一個叫用 \(Invoke\) 的方法。  
  
 C\# 程式只能有一個進入點。  如果不只一個類別有 `Main` 方法，您就必須搭配 **\/main** 編譯器選項來編譯程式，以指定要做為進入點的 `Main` 方法。  如需詳細資訊，請參閱[\/main \(Specify Location of Main Method\)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)。  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/main-and-command-line-ar_1.cs)]  
  
## 概觀  
  
-   `Main` 方法為 .exe 程式的進入點，是程式控制的開始及結束位置。  
  
-   `Main` 是在類別或結構內宣告。  `Main` 必須是 [靜態](../../../csharp/language-reference/keywords/static.md) ，而且不能是 [公用](../../../csharp/language-reference/keywords/public.md)。  \(在前面範例中，它會接收預設的 [private](../../../csharp/language-reference/keywords/private.md) 存取\)。封入類別或結構不一定要是靜態的。  
  
-   `Main` 可以有 `void` 或 `int` 傳回型別。  
  
-   宣告 `Main` 方法時，可以選擇是否搭配包含命令列引數的 `string[]` 參數。  在使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 建立 Windows Form 應用程式時，您可以手動加入參數，或者以 <xref:System.Environment> 類別來取得命令列引數。  參數會讀取為以零為基底索引的命令列引數。C 和 C\+\+ 不同的是，程式名稱不做為第一個命令列引數。  
  
## 本章節內容  
  
-   [命令列引數](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Main\(\) 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [C\# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<paveover\>C\# Sample Applications](http://msdn.microsoft.com/zh-tw/9a9d7aaa-51d3-4224-b564-95409b0f3e15)