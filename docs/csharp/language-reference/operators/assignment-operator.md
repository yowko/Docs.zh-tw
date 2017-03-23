---
title: "= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "= 運算子 [C#]"
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# = 運算子 (C# 參考)
指派運算子 \(`=`\) 會將右方運算元的值儲存在左方運算元所表示的儲存位置、屬性或索引子，並傳回該值做為結果。  運算元必須為同一型別 \(或右方的運算元可以隱含轉換為左方運算元的型別\)。  
  
## 備註  
 指派運算子不可被多載。  不過，您可以定義型別的隱含轉換運算子，如此可以讓您在這些型別中使用指派運算子。  如需詳細資訊，請參閱 [使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。  
  
## 範例  
 [!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)