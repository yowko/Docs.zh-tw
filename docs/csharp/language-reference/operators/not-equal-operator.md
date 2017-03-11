---
title: "!= 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "!=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "!= 運算子 [C#]"
  - "不等比較運算子 (!=) [C#]"
  - "不等於運算子 (!=) [C#]"
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# != 運算子 (C# 參考)
不等比較運算子 \(`!=`\) 在運算元相等時會傳回 false，不相等時傳回 true。  所有的型別 \(包括字串及物件\) 已預先定義不等比較運算子。  使用者定義型別可以多載 `!=` 運算子。  
  
## 備註  
 對於預先定義的實值型別，不等比較運算子 \(`!=`\) 的運算元若有不同的值，則會傳回 true，相同則傳回 false。  而對於 `string` 以外的參考型別，若兩個運算元參考至不同物件，`!=` 便會傳回 true。  針對 `string` 型別，`!=` 會比較字串的值。  
  
 使用者定義實值型別可多載 `!=` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  雖然針對預先定義的參考型別和使用者定義的參考型別，`!=` 的預設運作方法如上所述，但使用者定義的參考型別也可多載。  若多載 `!=`，則也必須多載 [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md)。  對整數類資料型別執行 \(Integral Type\) 的作業，通常也適用於列舉型別。  
  
## 範例  
 [!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#33)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)