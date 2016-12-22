---
title: "#undef (C# 參考) | Microsoft Docs"
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
  - "#undef"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#undef 指示詞 [C#]"
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #undef (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#undef` 可讓您將符號當做 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞中的運算式使用，以便取消符號的定義，此運算式將會評估為 `false`。  
  
 [\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 指示詞或 [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項都可用來定義符號。  `#undef` 指示詞必須在您使用任何非同時為指示詞的陳述式之前，便已出現在檔案中。  
  
## 範例  
  
```  
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
  **未定義 DEBUG**   
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)