---
title: "=&gt; 運算子 (C# 參考)"
ms.date: 10/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44cb0485aefa8b0ab10a00ae0525180020ce436d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="gt-operator-c-reference"></a>=&gt; 運算子 (C# 參考)

`=>`運算子可以用於 C# 中的兩種方式：

- 做為[lambda 運算子](#lamba-operator)中[lambda 運算式](../../lambda-expressions.md)，分開 lambda 主體輸入的變數。
 
- 在[運算式主體定義](#expression-body-definition)，其會為成員名稱來區分成員實作。 

## <a name="lambda-operator"></a>Lambda 運算子

`=>` 語彙基元又稱為 Lambda 運算子。 它會在「Lambda 運算式」中使用，以分開右邊的 Lambda 主體和左邊的輸入變數。 Lambda 運算式是類似匿名方法的內嵌運算式，但更有彈性；它會在以方法語法所表示的 LINQ 查詢中大量使用。 如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 下列範例顯示兩種方法來尋找及顯示字串陣列中最短字串的長度。 此範例的第一個部分會將 Lambda 運算式 (`w => w.Length`) 套用至 `words` 陣列的每個項目，然後使用 <xref:System.Linq.Enumerable.Min%2A> 方法來尋找最小長度。 相較之下，此範例的第二個部分會顯示使用查詢語法執行相同動作的較長方案。  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a>備註  
 `=>` 運算子與指派運算子 (`=`) 具有相同的優先順序，而且為右向關聯。  
  
 您可以明確指定輸入變數的類型，或讓編譯器推斷類型；不論是哪種情況，此變數在編譯時都屬於強型別。 當您指定類型時，您必須以括號括住類型名稱和變數名稱，如下列範例所示。  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>範例  
 下列範例示範如何為接受兩個引數之標準查詢運算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 的多載，撰寫 Lambda 運算式。 因為 Lambda 運算式有多個參數，所以必須以括號括住這些參數。 第二個參數 `index` 表示集合中目前項目的索引。 `Where` 運算式會傳回長度小於其陣列索引位置的所有字串。  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a>運算式主體定義

運算式主體定義提供高度壓縮，可讀取表單中的成員實作。 它有下列一般語法：

```csharp
member => expression;
```
其中 *expression* 是有效的運算式。 請注意，*運算式*可以*陳述式運算式*只有在成員的傳回型別`void`，或如果成員是建構函式或完成項。

開頭為 C# 6 支援的方法和屬性的 get 陳述式的運算式主體定義。 運算式主體定義的建構函式、 完成項，屬性的 set 陳述式，以及 C# 7 支援索引子。

下列為運算式主體定義`Person.ToString`方法：

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

它是下列的方法定義的簡短版：

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
如需詳細運算式主體定義的詳細資訊，請參閱[運算式主體的成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。

## <a name="see-also"></a>另請參閱  
[C# 參考](../../../csharp/language-reference/index.md)   
[C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
[運算式主體的成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。