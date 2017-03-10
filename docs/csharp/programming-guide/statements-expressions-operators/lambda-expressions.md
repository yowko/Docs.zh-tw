---
title: "Lambda 運算式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2017-03-03"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Lambda 運算式 [C#]"
  - "外部變數 [C#]"
  - "陳述式 lambda [C#]"
  - "運算式 lambda [C#]"
  - "運算式 [C#], Lambda"
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 64
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 64
---
# Lambda 運算式 (C# 程式設計手冊)
Lambda 運算式是[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)，可用來建立[委派](../../../csharp/programming-guide/delegates/using-delegates.md)或[運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)類型。 使用 Lambda 運算式可以撰寫區域函式，這些函式可以當做引數傳遞，或是當做函式呼叫的值傳回。 Lambda 運算式對於撰寫 LINQ 查詢運算式而言特別有用。  
  
 若要建立 Lambda 運算式，請在 Lambda 運算子 [\=\>](../../../csharp/language-reference/operators/lambda-operator.md) 的左邊指定輸入參數 \(如果有的話\)，並將運算式或陳述式區塊放在另一邊。 例如，Lambda 運算式 `x => x * x` 會指定名為 `x` 的參數，並傳回 `x` 的平方值。 您可以將這個運算式指派給委派類型，如下列範例所示：  
  
```c#  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 若要建立運算式樹狀架構類型：  
  
```c#  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 `=>` 運算子與指派 \(`=`\) 具有相同的優先順序，而且為[右向關聯](../../../csharp/programming-guide/statements-expressions-operators/operators.md) \(請參閱＜運算子＞文章的＜關聯性＞一節\)。  
  
 在以方法為基礎的 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 查詢中，Lambda 會用來做為標準查詢運算子方法的引數，例如 <xref:System.Linq.Enumerable.Where%2A>。  
  
 當您使用以方法為基礎的語法呼叫 <xref:System.Linq.Enumerable.Where%2A> 類別中的 <xref:System.Linq.Enumerable> 方法時 \(就像是在 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] to Objects 和 [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 中所執行\)，此參數會是委派類型 <xref:System.Func%602?displayProperty=fullName>。 Lambda 運算式是建立委派最方便的方式。 例如，當您在 <xref:System.Linq.Queryable?displayProperty=fullName> 類別中呼叫相同方法時 \(就像是在 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] 中所執行\)，參數類型就會是 <xref:System.Linq.Expressions.Expression?displayProperty=fullName>\<Func\>，其中 Func 是最多擁有十六個輸入參數的任一個 Func 委派。 再次強調，Lambda 運算式就是建構該運算式樹狀架構非常簡潔的方式。 Lambda 會讓 `Where` 呼叫看起來很相似，但是實際上從 Lambda 建立的物件類型並不相同。  
  
 在上面的範例中，請注意委派簽章擁有一個 `int` 類型的隱含類型輸入參數，而且會傳回 `int`。 由於 Lambda 運算式還有一個輸入參數 \(`x`\) 和可由編譯器隱含轉換為 `int` 類型的傳回值，因此 Lambda 運算式可以轉換為該類型的委派  \(類型推斷將於下列各節中詳細討論\)。 使用輸入參數 5 叫用委派時，它傳回的結果會是 25。  
  
 Lambda 不可出現在 [is](../../../csharp/language-reference/keywords/is.md) 或 [as](../../../csharp/language-reference/keywords/as.md) 運算子的左邊。  
  
 所有適用於匿名方法的限制，也都適用於 Lambda 運算式。 如需詳細資訊，請參閱[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)。  
  
## 運算式 Lambda  
 在 \=\> 運算子右邊有運算式的 Lambda 運算式稱為「*運算式 Lambda*」\(Expression Lambda\)。 運算式 Lambda 會在[運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)的建構過程中大量使用。 運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：  
  
```  
(input parameters) => expression  
```  
  
 只有在 Lambda 包含一個輸入參數時，括號才是選擇項，否則括號是必要項。 兩個或多個輸入參數會包含在括號中，並且以逗號分隔：  
  
```c#  
(x, y) => x == y  
```  
  
 有時候編譯器會很難或是無法推斷輸入類型。 當這種情形發生時，您可以明確指定類型，如下列範例所示：  
  
```c#  
(int x, string s) => s.Length > x  
```  
  
 以空括號指定零個輸入參數：  
  
```c#  
() => SomeMethod()  
```  
  
 請注意，在上面的範例中，運算式 Lambda 的主體可以包含方法呼叫。 不過，如果您要建立在 .NET Framework 外部 \(例如在 SQL Server 中\) 評估的運算式樹狀架構，則不應在 Lambda 運算式中使用方法呼叫。 這些方法在 .NET 通用語言執行平台內容之外將不具任何意義。  
  
## 陳述式 Lambda  
 陳述式 Lambda 看起來就像是運算式 Lambda，不同之處在於，陳述式會包含於大括號內：  
  
```  
(input parameters) => {statement;}  
```  
  
 陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。  
  
```c#  
delegate void TestDelegate(string s);  
…  
TestDelegate myDel = n => { string s = n + " " + "World"; Console.WriteLine(s); };  
myDel("Hello");  
```  
  
 陳述式 Lambda 就像匿名方法，它不能用來建立運算式樹狀架構。  
  
## 非同步 Lambda  
 您可以使用 [async](../../../csharp/language-reference/keywords/async.md) 和 [await](../../../csharp/language-reference/keywords/await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。 例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync` 的事件處理常式。  
  
```c#  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\r\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  
  
 您可以使用非同步 Lambda 加入相同的事件處理常式。 若要加入這個處理常式，請將 `async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示。  
  
```c#  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\r\nControl returned to Click event handler.\r\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  
  
 如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 具有標準查詢運算子的 Lambda  
 許多標準查詢運算子都有輸入參數，參數的類型為其中一種 <xref:System.Func%602> 系列泛型委派。 這些委派使用類型參數定義輸入參數的數目和類型，以及委派的傳回類型。 對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。 例如，請考慮下列委派類型：  
  
```c#  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 委派可以具現化為 `Func<int,bool> myFunc`，其中 `int` 是輸入參數，而 `bool` 是傳回值。 傳回值一律在最後一個類型參數中指定。`Func<int, string, bool>` 會定義具有兩個輸入參數 `int` 和 `string` 且傳回類型為 `bool` 的委派。 叫用下列 `Func` 委派時將會傳回 true 或 false，指出輸入參數是否等於 5：  
  
```c#  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 您也可以在引數類型為 `Expression<Func>` 時，於例如 System.Linq.Queryable 中定義的標準查詢運算子內提供 Lambda 運算式。 當您指定 `Expression<Func>` 引數時，Lambda 將會編譯為運算式樹狀架構。  
  
 標準查詢運算子，也就是 <xref:System.Linq.Enumerable.Count%2A> 方法，如下所示：  
  
```c#  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 編譯器會推斷輸入參數的類型，您也可以明確指定類型。 這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 \(`n`\)。  
  
 下列程式碼行產生的序列會包含 `numbers` 陣列中所有位於 9 左邊的元素，因為 9 是序列中第一個不符合條件的數字：  
  
```c#  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 這個範例會示範將多個輸入參數包含在括號內的指定方式。 這個方法會傳回數字陣列中的所有元素，直到遇到數值小於其位置的數字為止。 切勿混淆 Lambda 運算子 \(`=>`\) 與大於或等於運算子 \(`>=`\)。  
  
```c#  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## Lambda 中的類型推斷  
 撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數的委派類型，以及 C\# 語言規格中所述的其他因素來推斷類型。 對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。 因此，如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：  
  
```c#  
customers.Where(c => c.City == "London");  
```  
  
 以下是 Lambda 的一般規則：  
  
-   Lambda 必須包含與委派類型相同數目的參數。  
  
-   Lambda 中的每個輸入參數都必須能夠隱含轉換為其對應的委派參數。  
  
-   Lambda 的傳回值 \(如果有的話\) 必須能夠隱含轉換為委派的傳回類型。  
  
 請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。 不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。 在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 <xref:System.Linq.Expressions.Expression> 類型。  
  
## Lambda 運算式中的變數範圍  
 Lambda 可以參考*外部變數*\(Outer Variable\) \(請參閱[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)\)，這些變數必須包含在定義 Lambda 函式的方法範圍內，或是在包含 Lambda 運算式的類型範圍內。 以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。 外部變數必須確實指派，才能用於 Lambda 運算式。 下列範例將示範這些規則：  
  
```c#  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
  
```  
  
 下列規則適用於 Lambda 運算式中的變數範圍：  
  
-   已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。  
  
-   導入 Lambda 運算式內的變數無法在外部方法中看見。  
  
-   Lambda 運算式無法直接從封入方法擷取 `ref` 或 `out` 參數。  
  
-   Lambda 運算式中的 return 陳述式不會造成封入方法傳回。  
  
-   如果跳躍陳述式的目標不在區塊內，則 Lambda 運算式不可包含 Lambda 函式內的 `goto` 陳述式、`break` 陳述式或 `continue` 陳述式。 即使目標位於區塊內，跳躍陳述式出現在 Lambda 函式區塊外部也一樣是錯誤。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 精選書籍章節  
 [C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369) \(C\# 3.0 Cookbook 第三版：250 個以上 C\# 3.0 程式設計人員適用的方案\) 中的[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) \(委派、事件和 Lambda 運算式\)  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [運算式樹狀架構](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Studio 2008 C\# 範例 \(請參閱 LINQ 範例查詢檔案和 XQuery 程式\)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)   
 [Recursive lambda expressions \(遞迴的 Lambda 運算式\)](http://go.microsoft.com/fwlink/?LinkId=112395)