---
title: "轉換運算子 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 轉換運算子"
  - "轉換運算子 [C#]"
  - "運算子 [C#], 轉換"
  - "使用者定義的轉換 [C#]"
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 轉換運算子 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 可讓程式設計人員宣告類別或結構轉換，使類別或結構能夠與其他的類別、結構或基本的型別相互轉換。  轉換定義的方式和運算子一樣，並且對轉換成的型別來命名。  在要轉換的型別引數或轉換所產生的型別中，必須有一個是包含型別，但不能兩者都是。  
  
 [!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## 轉換運算子概觀  
 轉換運算子有下列屬性︰  
  
-   宣告為 `implicit` 的轉換會在必要時自動發生。  
  
-   宣告為 `explicit` 的轉換需要呼叫轉型  
  
-   所有轉換必須宣告為 `static`。  
  
## 相關章節  
 如需詳細資訊，請參閱下列主題：  
  
-   [使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [如何：在結構之間實作使用者定義的轉換](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [隱含](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../visual-basic/language-reference/modifiers/static.md)  
  
## 請參閱  
 <xref:System.Convert>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [所繫結之使用者定義的明確轉換在 C\#](http://go.microsoft.com/fwlink/?LinkId=112384)