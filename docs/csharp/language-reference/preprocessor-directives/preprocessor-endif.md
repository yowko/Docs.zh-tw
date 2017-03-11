---
title: "#endif (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#endif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#endif 指示詞 [C#]"
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# #endif (C# 參考)
`#endif` 指定條件指示詞的結束，此條件指示詞以 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞開始。  例如：  
  
```  
  
      #define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## 備註  
 以 `#if` 指示詞開始的條件式指示詞必須以 `#endif` 指示詞明確結束。  如需如何使用 `#endif` 的範例，請參閱 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)