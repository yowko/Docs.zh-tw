---
title: "explicit (C# 參考) | Microsoft Docs"
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
  - "explicit_CSharpKeyword"
  - "explicit"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "explicit 關鍵字 [C#]"
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# explicit (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`explicit` 關鍵字會宣告必須以轉型 \(cast\) 叫用的使用者定義型別轉換運算子。  例如，此運算子會從名為 Fahrenheit 的類別轉換成名為 Celsius 的類別：  
  
 [!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 可以如下所示的方式叫用轉換運算子：  
  
 [!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 轉換運算子會從來源型別轉換成目標型別。  來源型別會提供轉換運算子。  不同於隱含轉換，明確轉換運算子必須經由轉型 \(Cast\) 的方式叫用。  若轉換作業會造成例外狀況或遺失資訊，您應將其標記為 `explicit`。  這可以防止編譯器在不顯示任何訊息下叫用轉換作業，而引發不可預知的後果。  
  
 省略轉型會導致編譯時期錯誤 CS0266。  
  
 如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。  
  
## 範例  
 下列範例提供 `Fahrenheit` 和 `Celsius` 類別，這兩個類別都提供了明確轉換運算子給其他類別。  
  
 [!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## 範例  
 下面的範例定義了結構 `Digit`，代表了一個單一的十進位數字。  並定義一個可以將 `byte` 轉換為 `Digit` 的運算子，但由於不是所有的位元組都可以轉換成 `Digit`，故此轉換為明確。  
  
 [!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [隱含](../../../csharp/language-reference/keywords/implicit.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [如何：在結構之間實作使用者定義的轉換](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)   
 [所繫結之使用者定義明確轉換在 C\#](http://go.microsoft.com/fwlink/?LinkId=112384)