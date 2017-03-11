---
title: "?? 運算子 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "??_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "?? 運算子 [C#]"
  - "聯合運算子 [C#]"
  - "條件式 AND 運算子 (&&) [C#]"
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# ?? 運算子 (C# 參考)
`??` 運算子稱為 null 聯合運算子。如果運算元不是 null，則會傳回左方運算元，否則傳回右方運算元。  
  
## 備註  
 可為 Null 的類型可以表示來自類型網域的值，或值可以是未定義 \(這種情況下，值為 null\)。  當左方運算元是可為 null 類型且其值為 null 時，您可以使用 `??` 運算子的語法表達能力傳回適當的值 \(右方運算元\)。  如果您嘗試在不使用 `??` 運算子的情況下，將可為 null 的實值類型指派給不可為 null 的實值類型，則會產生編譯時期錯誤。  如果您使用轉型，而可為 null 的實值類型目前為未定義，則會擲回 `InvalidOperationException` 例外狀況。  
  
 如需詳細資訊，請參閱[可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)。  
  
 ?? 運算子的結果不會視為常數，即使它的引數都是常數也一樣。  
  
## 範例  
 [!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#53)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 運算子](../../../csharp/language-reference/operators/index.md)   
 [可為 Null 的類型](../../../csharp/programming-guide/nullable-types/index.md)   
 [「增益」\(Lift\) 的真正意義是什麼？](http://go.microsoft.com/fwlink/?LinkID=112382)