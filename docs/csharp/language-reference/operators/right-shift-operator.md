---
title: "&gt;&gt; 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - ">>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">> 運算子 [C#]"
  - "向右位移運算子 (>>) [C#]"
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &gt;&gt; 運算子 (C# 參考)
向右移位 \(Right\-Shift\) 運算子 \(`>>`\) 會將第一個運算元向右移動，移動的位元數由第二個運算元所指定。  
  
## 備註  
 如果第一個運算元是 [int](../../../csharp/language-reference/keywords/int.md) 或 [uint](../../../csharp/language-reference/keywords/uint.md) \(32 位元的個數\)，則第二個運算元的低序位五個位元 \(第二個運算元以及 0x1f\) 會提供移位計數。  
  
 若第一個運算元是 [long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) \(64 位元的個數\)，第二個運算元的低序位六個位元 \(第二個運算元以及 0x3f\) 就會提供移位計數。  
  
 如果第一個運算元是  [int](../../../csharp/language-reference/keywords/int.md) 或 [long](../../../csharp/language-reference/keywords/long.md)，向右移位即為算術移位 \(高序位的空白位元已設為正負號位元\)。  如果第一個運算元是 [uint](../../../csharp/language-reference/keywords/uint.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) 型別，向右移位即為邏輯移位 \(高序位位元由零填滿\)。  
  
 使用者定義型別可多載 `>>` 運算子；第一個運算元的型別必須為使用者定義型別，而第二個運算元的型別必須為 [int](../../../csharp/language-reference/keywords/int.md)。  如需詳細資訊，請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)。  當多載二元 \(Binary\) 運算子時，同時隱含多載其對應的指派運算子 \(若有的話\)。  
  
## 範例  
 [!code-cs[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)