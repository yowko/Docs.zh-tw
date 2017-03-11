---
title: "相等比較 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "物件相等 [C#]"
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 相等比較 (C# 程式設計手冊)
有時候需要比較兩個值是否相等。  在某些情況下，您會測試「*實值相等*」\(Value Equality\)，也稱為「*等價*」\(Equivalence\)，這表示兩個變數包含的值相等。  在其他情況下，您需判斷兩個變數是否參考記憶體中的同一個基礎物件。  這種相等稱為「*參考相等*」\(Reference Equality\) 或「*一致*」\(Identity\)。  本主題說明這兩種相等，並提供詳細資訊的其他主題連結。  
  
## 參考相等  
 參考相等意指兩個物件參考全都參考到同一個基礎物件。  這只要用簡單的指派就可以做到，如下列範例所示。  
  
 [!code-cs[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/equality-comparisons_1.cs)]  
  
 此程式碼會建立兩個物件，但在指派陳述式後，兩個參考都參考到同一物件。  因此這兩個物件具有參考相等。  使用 <xref:System.Object.ReferenceEquals%2A> 方法即可判斷兩個參考是否參考到相同的物件。  
  
 參考相等的概念僅適用於參考類型。  實值類型物件不能有參考相等，因為當實值類型的執行個體指派給變數時，會產生一個實值副本。  因此，不可能有兩個 Unboxed 結構參考到記憶體中的相同位置。  此外，如果使用 <xref:System.Object.ReferenceEquals%2A> 比較兩個實值類型，結果永遠會是 `false`，即使物件中包含的值全都一致也一樣。  這是因為每個變數都 Boxed 成不同的物件執行個體。  如需詳細資訊，請參閱 [如何：參考相等 \(識別\) 的測試](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)。  
  
## 實值相等  
 實值相等是指兩個物件包含相同的值。  對於基本實值類型 \(例如 [int](../../../csharp/language-reference/keywords/int.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md)\)，測試實值相等相當直接簡單。  您可以用 [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) 運算子，如下列範例所示。  
  
```c#  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 至於大部分其他類型，測試實值相等比較複雜，因為您需要了解類型如何進行定義。  至於具有多重欄位或屬性的類別和結構，實值相等的定義通常是指所有欄位或屬性都有相同的值。  例如，有兩個 `Point` 物件，如果 pointA.X 等於 pointB.X 且 pointA.Y 等於 pointB.Y，即可定義為相等。  
  
 不過，沒有必要以類型中的所有欄位來定義等價。  可以以一個子集為準，  當您比較不屬於您的類型時，應確實了解該類型的等價是如何定義的。  如需如何在您自己的類別和結構中定義實值相等的詳細資訊，請參閱 [如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)。  
  
### 浮點值的實值相等  
 浮點值的相等比較 \([double](../../../csharp/language-reference/keywords/double.md) 和 [float](../../../csharp/language-reference/keywords/float.md)\) 會有問題，因為二進位電腦上的浮點數運算並不精確。  如需詳細資訊，請參閱 <xref:System.Double?displayProperty=fullName> 主題中的備註。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[如何：參考相等 \(識別\) 的測試](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|說明如何判斷兩個變數是否具有參考相等。|  
|[如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|說明如何提供類型的實值相等自訂定義。|  
|[C\# 程式設計手冊](../../../csharp/programming-guide/index.md)|提供重要 C\# 語言功能以及能夠透過 .NET Framework 用於 C\# 之功能的詳細資訊連結。|  
|[類型](../../../csharp/programming-guide/types/index.md)|提供 C\# 類型系統的詳細資訊以及其他資訊的連結。|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)