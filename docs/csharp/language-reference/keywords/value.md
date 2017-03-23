---
title: "value (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "value_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "value 關鍵字 [C#]"
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# value (C# 參考)
內容關鍵字 `value` 是在一般屬性宣告的 set 存取子中使用的。  這個關鍵字類似於方法的輸入參數。  `value` 一字會參考用戶端程式碼嘗試指派給屬性的值。  在下列範例中，`MyDerivedClass` 中名為 `Name` 的屬性會使用 `value` 參數，將新字串指派給支援欄位 `name`。  從用戶端程式碼的觀點來看，這項作業是以簡單的指派撰寫的。  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 如需使用 `value` 的詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)