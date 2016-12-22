---
title: "#elif (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#elif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#elif 指示詞 [C#]"
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #elif (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#elif` 讓您可以建立複合條件指示詞。  如果前面的 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 和任何前面的 \(選擇性\) `#elif` 指示詞運算式都不是評估為 `true`，就會評估 `#elif` 運算式。  如果 `#elif` 運算式評估為 `true`，編譯器便會評估所有介於 `#elif` 和下一個條件指示詞之間的程式碼。  例如：  
  
```  
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 您可以使用 `==` \(等於\)、`!=` \(不等於\)、`&&` \(和\) 以及 `||` \(或\) 等運算子，來評估多重符號。  也可以使用括弧來群組符號和運算子。  
  
## 備註  
 `#elif` 等於使用：  
  
```  
#else  
#if  
```  
  
 但是使用 `#elif` 比較簡單，因為每個 `#if` 都需要配對一個 [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)，而 `#elif` 可以在無對應的 `#endif` 情況下使用。  
  
 如需如何使用 `#elif` 的範例，請參閱 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)