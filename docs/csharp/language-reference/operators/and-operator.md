---
title: "&amp; 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "&_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "位元 AND 運算子 [C#]"
  - "連字號運算子 (&) [C#]"
  - "& 運算子 [C#]"
  - "AND 運算子 (&) [C#]"
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &amp; 運算子 (C# 參考)
& 運算子可做為一元或二元運算子。  
  
## 備註  
 一元 & 運算子會傳回運算元的位址 \(需要 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 的內容\)。  
  
 二元 & 運算子已為整數類資料型別及 `bool` 預先定義其運算方式。  對於整數類資料型別，& 會針對其運算元進行邏輯位元 AND 運算。  對於 `bool` 運算元，& 會針對其運算元進行邏輯 AND 運算，也就是說，只有在兩個運算元皆為 `true` 時，結果才會是 `true`。  
  
 `&` 運算子會同時評估兩個運算子，不管第一個運算子其值為何。  例如：  
  
 [!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 使用者定義型別可多載二進位 `&` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  對整數類資料型別執行 \(Integral Type\) 的作業，通常也適用於列舉型別。  當多載二元 \(Binary\) 運算子時，同時隱含多載其對應的指派運算子 \(若有的話\)。  
  
## 範例  
 [!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)