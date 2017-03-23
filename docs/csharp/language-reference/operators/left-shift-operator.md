---
title: "&lt;&lt; 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<<_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<< 運算子 [C#]"
  - "向左位移運算子 (<<) [C#]"
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# &lt;&lt; 運算子 (C# 參考)
向左移位 \(Left\-Shift\) 運算子 \(`<<`\) 會將第一個運算元向左移動，移動的位元數由第二個運算元所指定。  第二個運算元的型別必須是 [int](../../../csharp/language-reference/keywords/int.md) 或已預先定義隱含數值轉換成 `int` 的型別。  
  
## 備註  
 如果第一個運算元是 [int](../../../csharp/language-reference/keywords/int.md) 或 [uint](../../../csharp/language-reference/keywords/uint.md) \(32 位元的個數\)，第二個運算元的低序位五個位元就會提供移位計數。  也就是說，實際的移位計數是 0 至 31 個位元。  
  
 若第一個運算元是 [long](../../../csharp/language-reference/keywords/long.md) 或 [unlong](../../../csharp/language-reference/keywords/ulong.md) \(64 位元的個數\)，則第二個運算元的低序位六個位元會提供移位計數。  也就是說，實際的移位計數是 0 至 63 個位元。  
  
 捨棄移位後，會捨棄任何不在第一個運算元類型範圍內的高序位位元，而低序位的空白位元將由零填滿。  移位運算子不會造成溢位。  
  
 使用者定義型別可多載 `<<` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)，第一個運算元的型別必須為使用者定義型別，而第二個運算元的型別必須為 `int`。  當多載二元 \(Binary\) 運算子時，同時隱含多載其對應的指派運算子 \(若有的話\)。  
  
## 範例  
 [!code-cs[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## 註解  
 請注意，`i<<1` 和 `i<<33`  會得到相同的結果，因為 1 和 33 的低階層五個位元相同。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)