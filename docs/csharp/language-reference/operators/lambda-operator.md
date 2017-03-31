---
title: "=&gt; 運算子 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a75967e61d2c674e87e321de1fb6e4062cca4f19
ms.lasthandoff: 03/13/2017

---
# <a name="gt-operator-c-reference"></a>=&gt; 運算子 (C# 參考)
`=>` 語彙基元又稱為 Lambda 運算子。 它會在「Lambda 運算式」**中使用，以分開右邊的 Lambda 主體和左邊的輸入變數。 Lambda 運算式是類似匿名方法的內嵌運算式，但更有彈性；它會在以方法語法所表示的 LINQ 查詢中大量使用。 如需詳細資訊，請參閱 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)。  
  
 下列範例顯示兩種方法來尋找及顯示字串陣列中最短字串的長度。 此範例的第一個部分會將 Lambda 運算式 (`w => w.Length`) 套用至 `words` 陣列的每個項目，然後使用 <xref:System.Linq.Enumerable.Min%2A> 方法來尋找最小長度。 相較之下，此範例的第二個部分會顯示使用查詢語法執行相同動作的較長方案。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="remarks"></a>備註  
 `=>` 運算子與指派運算子 (`=`) 具有相同的優先順序，而且為右向關聯。  
  
 您可以明確指定輸入變數的類型，或讓編譯器推斷類型；不論是哪種情況，此變數在編譯時都屬於強型別。 當您指定類型時，您必須以括號括住類型名稱和變數名稱，如下列範例所示。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example"></a>範例  
 下列範例示範如何為接受兩個引數的標準查詢運算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 多載，撰寫 Lambda 運算式。 因為 Lambda 運算式有多個參數，所以必須以括號括住這些參數。 第二個參數 `index` 表示集合中目前項目的索引。 `Where` 運算式會傳回長度小於其陣列索引位置的所有字串。  
  
```cs  
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
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
