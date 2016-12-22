---
title: "=&gt; 運算子 (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "=>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lambda 運算子 [C#]"
  - "=> 運算子 [C#]"
  - "Lambda 運算式 [C#]，=> 運算子"
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# =&gt; 運算子 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`=>` 語彙基元又稱為 Lambda 運算子。  它會在「*Lambda 運算式*」\(Lambda Expression\) 中使用，以分開右邊的 Lambda 主體和左邊的輸入變數。  Lambda 運算式是類似匿名方法 \(Anonymous Method\) 的內嵌 \(Inline\) 運算式，但更有彈性。它會在以方法語法所表示的 LINQ 查詢中大量使用。  如需詳細資訊，請參閱[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 下列範例顯示兩種尋找並顯示較短的字串長度陣列中的字串。  此範例的第一部分將 Lambda 運算式 \(`w => w.Length`\) 的 `words` 陣列中的每個項目會使用 <xref:System.Linq.Enumerable.Min%2A> 方法來尋找最小長度。  對於比較時，這個範例的第二部分顯示較長的方案使用查詢語法執行相同的動作。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## 備註  
 `=>` 運算子和指派運算子 \(`=`\) 具有相同的優先順序，而且是右向關聯的。  
  
 您可以明確指定項目變數的型別或讓編譯器推斷;在任何情況下，變數是強型別在編譯時間。  當您指定型別時，您必須將型別括住名稱和這個變數名稱，，如下列範例所示。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## 範例  
 下列範例顯示如何為採用兩個引數的標準查詢運算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 的多載將 Lambda 運算式。  因為 Lambda 運算式有多個參數，必須以括號括住參數。  第二個參數，則為 `index`，表示目前項目在集合中的索引。  `Where` 運算式傳回長度小於其陣列索引位置的字串。  
  
```c#  
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
  
    // Compare the following code, which arrives at the same list of short  
    // digits but takes more work to get there.  
    Console.WriteLine("\nExample that uses a for loop:");  
    List<string> shortDigits2 = new List<string>();  
    for (var i = 0; i < digits.Length; i++)  
    {  
        if (digits[i].Length < i)  
            shortDigits2.Add(digits[i]);  
    }  
  
    foreach (var d in shortDigits2)  
    {  
        Console.WriteLine(d);  
    }  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
  
    // Example that uses a for loop:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)