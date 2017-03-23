---
title: "#else (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#else"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#else 指示詞 [C#]"
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# #else (C# 參考)
`#else` 可讓您建立複合條件指示詞，如果在之前的 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 \(選擇性\) [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 指示詞中，沒有任何運算式為 `true`，則編譯器將會評估在 `#else` 與隨後的 `#endif` 之間的程式碼。  
  
## 備註  
 [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 必須是 `#else` 之後的下一個前置處理器指示詞 \(Preprocessor Directive\)。  如需如何使用 `#else` 的範例，請參閱 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)