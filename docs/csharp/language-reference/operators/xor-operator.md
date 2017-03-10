---
title: "^ 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "^_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "^ 運算子 [C#]"
  - "bitwise exclusive OR 運算子 [C#]"
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# ^ 運算子 (C# 參考)
已為整數類資料型別和 `bool` 預先定義二元 `^` 運算子。  對於整數型別，`^` 會針對其運算元進行位元 \(Bitwise\) 互斥\-OR 運算。  對於 `bool` 運算元，`^` 會針對其運算元進行邏輯 Exclusive\-OR 運算；也就是說，只有在剛好有一個運算元為 `true` 時，結果才會是 `true`。  
  
## 備註  
 使用者定義型別可多載 `^` 運算子 \(請參閱 [operator](../../../csharp/language-reference/keywords/operator.md)\)。  對整數類資料型別執行 \(Integral Type\) 的作業，通常也適用於列舉型別。  
  
## 範例  
 [!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#30)]  
  
 前一個範例中的 `0xf8 ^ 0x3f` 運算會執行下列兩個二進位值的 Exclusive\-OR 位元 \(Bitwise\)，這兩個值分對應 16 進位的 F8 與 3F：  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Exclusive\-OR 的結果為 `1100 0111`，表示 16 進位的 C7。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)