---
title: "+ 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "+_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "+ 運算子 [C#]"
  - "加法運算子 [C#]"
  - "串連運算子 [C#]"
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# + 運算子 (C# 參考)
`+` 運算子可做為一元 \(Unary\) 或二元 \(Binary\) 運算子。  
  
## 備註  
 已為所有數字型別預先定義一元 `+` 運算子。  數字型別的一元 `+` 運算結果就是運算元的值。  
  
 二元 `+` 運算子已為數字和字串型別預先定義。  對於數字型別，\+ 會計算兩個運算元的總和。  若運算元其中之一或兩者皆為字串型別，\+ 會將運算元的字串表示串連起來。  
  
 委派型別也有提供執行委派串連的二元 `+` 運算子。  
  
 使用者定義型別可多載一元 `+` 和二元 `+` 運算子。  對整數類資料型別執行 \(Integral Type\) 的作業，通常也適用於列舉型別。  如需詳細資訊，請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)。  
  
## 範例  
 [!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)