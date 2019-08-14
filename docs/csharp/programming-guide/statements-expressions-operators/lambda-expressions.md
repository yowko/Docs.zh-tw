---
title: Lambda 運算式 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 36dab520d67d08d1b3304f1453bfb2c07a2f1c32
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671699"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda 運算式 (C# 程式設計指南)

「Lambda 運算式」  是下列兩種形式之一的運算式：

- 以運算式作為主體的[運算式 Lambda](#expression-lambdas)：

  ```csharp
  (input-parameters) => expression
  ```

- 以陳述式區塊作為主體的[陳述式 Lambda](#statement-lambdas)：

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

請使用 [Lambda 宣告運算子 `=>` ](../../language-reference/operators/lambda-operator.md) 來分隔 Lambda 的參數清單及其主體。 若要建立 Lambda 運算式，請在 Lambda 運算子 的左邊指定輸入參數 (如果有的話)，並在另一邊指定運算式或陳述式區塊。

任何 Lambda 運算式可轉換成[委派](../../language-reference/builtin-types/reference-types.md#the-delegate-type)型別。 Lambda 運算式可以轉換成的委派型別，是由其參數和傳回值的型別所定義。 如果 Lambda 運算式不會傳回值，則其可轉換成其中一個 `Action` 委派型別；否則可轉換成其中一個 `Func` 委派型別。 例如，具有兩個參數且不會傳回值的 Lambda 運算式，可以轉換成 <xref:System.Action%602> 委派。 具有一個參數且會傳回值的 Lambda 運算式，可以轉換成 <xref:System.Func%602> 委派。 在下列範例中，Lambda 運算式 `x => x * x` 會指定名為 `x` 的參數，並傳回 `x` 平方的值，此運算式已指派給委派型別的變數：

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Lambda 運算式也可以轉換成[運算式樹狀架構](../concepts/expression-trees/index.md)型別，如下列範例所示：

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

您可以在任何需要委派型別或運算式樹狀架構執行個體的程式碼中使用 Lambda 運算式，例如作為 <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> 方法的引數，以傳遞應該在背景中執行的程式碼。 當您撰寫 [LINQ 查詢運算式](../../linq/index.md)時，也可以使用 Lambda 運算式，如下列範例所示：

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

當您使用以方法為基礎的語法呼叫 <xref:System.Linq.Enumerable?displayProperty=nameWithType> 類別中的 <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> 方法時 (例如在 LINQ to Objects 和 LINQ to XML中所執行)，此參數會是委派型別 <xref:System.Func%602?displayProperty=nameWithType>。 當您在 <xref:System.Linq.Queryable?displayProperty=nameWithType> 類別中呼叫 <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> 方法時 (例如在 LINQ to SQL 中所執行)，參數型別是運算式樹狀架構型別 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)。 在這兩種情況下，您都可以使用相同的 Lambda 運算式來指定參數值。 那會讓兩個 `Select` 呼叫看起來很相似，但是實際上從 Lambda 建立的物件型別並不相同。
  
## <a name="expression-lambdas"></a>運算式 Lambda

在 `=>` 運算子右邊有運算式的 Lambda 運算式稱為「運算式 Lambda」  。 運算式 Lambda 會在[運算式樹狀架構](../concepts/expression-trees/index.md)的建構過程中大量使用。 運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：

```csharp
(input-parameters) => expression
```

只有在 Lambda 包含一個輸入參數時，括號才是選擇項，否則括號是必要項。

以空括號指定零個輸入參數：  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

兩個或多個輸入參數會包含在括號中，並且以逗號分隔：

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

有時候編譯器無法推斷輸入類型。 您可以明確指定類型，如下列範例所示：

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

輸入參數類型必須全部為明確或全部為隱含；否則，會發生 [CS0748](../../misc/cs0748.md) 編譯器錯誤。

運算式 Lambda 的主體可以包含方法呼叫。 不過，如果您要建立在 .NET 通用語言執行平台外部 (例如在 SQL Server 中) 評估的運算式樹狀架構，則不應在 Lambda 運算式中使用方法呼叫。 這些方法在 .NET 通用語言執行平台內容之外將不具任何意義。

## <a name="statement-lambdas"></a>陳述式 Lambda

陳述式 Lambda 看起來就像是運算式 Lambda，不同之處在於，陳述式會包含於大括號內：

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

陳述式 Lambda 無法用來建立運算式樹狀架構。
  
## <a name="async-lambdas"></a>非同步 Lambda

您可以使用 [async](../../language-reference/keywords/async.md) 和 [await](../../language-reference/keywords/await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。 例如，下列 Windows Form 範例包含呼叫並等候非同步方法 `ExampleMethodAsync`的事件處理常式。

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

您可以使用非同步 Lambda 加入相同的事件處理常式。 若要加入這個處理常式，請將 `async` 修飾詞加入至 Lambda 參數清單前面，如下列範例所示：

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](../concepts/async/index.md)。

## <a name="lambda-expressions-and-tuples"></a>Lambda 運算式和元組

從 C# 7.0 開始，C# 語言提供[元組](../../tuples.md)的內建支援。 您可以將元組當做引數提供給 Lambda 運算式，而您的 Lambda 運算式也可以傳回元組。 在某些情況下，C# 編譯器會使用型別推斷來判斷元組元件的類型。

若要定義元組，請以括號括住其元件的逗號分隔清單。 下列範例使用具有 3 個元件的元組將一連串數字傳遞至 Lambda 運算式，這會使每個值加倍，並傳回具有三個元件的元組，其中包含乘法運算的結果。

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

通常，元組的欄位會命名為 `Item1`、`Item2`，依此類推。不過，您可以定義具有具名元件的元組，如下列範例所示。

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

如需 C# 元組的詳細資訊，請參閱 [C# 元組型別](../../tuples.md)。

## <a name="lambdas-with-the-standard-query-operators"></a>具有標準查詢運算子的 Lambda

其他實作中的 LINQ to Objects 具有輸入參數，其類型是其中一種 <xref:System.Func%601> 系列的泛型委派。 這些委派使用型別參數定義輸入參數的數目和類型，以及委派的傳回型別。 對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。 例如，請考慮 <xref:System.Func%602> 委派類型：  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

委派可以具現化為 `Func<int, bool>` 執行個體，其中 `int` 是輸入參數，而 `bool` 是傳回值。 傳回值一律在最後一個類型參數中指定。 例如，`Func<int, string, bool>` 定義具有兩個輸入參數 (`int` 和 `string`) 的委派與 `bool` 的傳回類型。 叫用下列 `Func` 委派時會傳回布林值，指出輸入參數是否等於 5：

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

您也可以在引數類型為 <xref:System.Linq.Expressions.Expression%601> 時提供 Lambda 運算式，例如在定義於 <xref:System.Linq.Queryable> 類型的標準查詢運算子中。 當您指定 <xref:System.Linq.Expressions.Expression%601> 引數時，Lambda 會編譯成運算式樹狀結構。
  
下列範例使用 <xref:System.Linq.Enumerable.Count%2A> 標準查詢運算子：

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

編譯器會推斷輸入參數的類型，您也可以明確指定類型。 這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 (`n`)。

下列範例產生的序列會包含 `numbers` 陣列中所有位於 9 前面的元素，因為 9 是序列中第一個不符合條件的數字：

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

下列範例會用括號括住的方式來指定多個輸入參數。 這個方法會傳回 `numbers` 陣列中的所有元素，直到遇到其值小於陣列中的序數位置的數字為止：

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda 運算式中的型別推斷

撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數類型，以及 C# 語言規格中所述的其他因素來推斷類型。 對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。 如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：  

```csharp
customers.Where(c => c.City == "London");
```

Lambda 型別推斷的一般規則如下所示：

- Lambda 必須包含與委派類型相同數目的參數。

- Lambda 中的每個輸入參數都必須能夠隱含轉換為其對應的委派參數。

- Lambda 的傳回值 (如果有的話) 必須能夠隱含轉換為委派的傳回類型。
  
請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。 不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。 在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 <xref:System.Linq.Expressions.Expression> 類型。

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Lambda 運算式中的擷取外部變數和變數範圍

Lambda 可以參考「外部變數」  。 這些是在定義 Lambda 運算式的方法範圍內，或是在包含 Lambda 運算式的型別範圍內的變數。 以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。 外部變數必須確實指派，才能用於 Lambda 運算式。 下列範例將示範這些規則：

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

下列規則適用於 Lambda 運算式中的變數範圍：  

- 已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。

- 導入 Lambda 運算式內的變數無法在封入方法中看見。

- Lambda 運算式無法直接從封入方法擷取 [in](../../language-reference/keywords/in-parameter-modifier.md)、[ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數。

- Lambda 運算式中的 [return](../../language-reference/keywords/return.md) 陳述式不會造成封入方法傳回。

- 如果該跳躍陳述式的目標位於 Lambda 運算式區塊之外，則 Lambda 運算式不能包含 [goto](../../language-reference/keywords/goto.md)、[break](../../language-reference/keywords/break.md) 或 [continue](../../language-reference/keywords/continue.md) 陳述式。 即使目標位於區塊內，跳躍陳述式出現在 Lambda 運算式區塊外部也一樣是錯誤。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。

## <a name="featured-book-chapter"></a>精選書籍章節

[C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)中的[委派、事件與 Lambda 運算式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29)  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [LINQ (Language-Integrated Query)](../concepts/linq/index.md)
- [運算式樹狀結構](../concepts/expression-trees/index.md)
- [區域函式與 Lambda 運算式的比較](../../local-functions-vs-lambdas.md)
- [隱含型別 Lambda 運算式](../../implicitly-typed-lambda-expressions.md)
- [Visual Studio 2008 C# 範例 (請參閱 LINQ 範例查詢檔案和 XQuery 程式)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Recursive lambda expressions (遞迴的 Lambda 運算式)](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
