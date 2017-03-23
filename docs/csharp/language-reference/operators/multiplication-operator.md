---
title: "* 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "*_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "* 運算子 [C#]"
  - "乘法運算子 (*) [C#]"
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# * 運算子 (C# 參考)
乘法運算子 \(`*`\) 會計算運算元的乘積。  此外還有取值運算子可允許讀取和寫入指標。  
  
## 備註  
 所有的數字型別都已預先定義了乘法運算子。  
  
 `*` 運算子也可以用來宣告指標型別和取值指標。  這個運算子只能在不安全的內容中使用，此內容以 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字表示，並且需要使用 [\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項。  取值運算子也就是所謂的間接取值運算子。  
  
 使用者定義型別可多載二元 `*` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  當多載二元 \(Binary\) 運算子時，同時隱含多載其對應的指派運算子 \(若有的話\)。  
  
## 範例  
 [!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## 範例  
 [!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)