---
title: "#if (C# 參考) | Microsoft Docs"
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
  - "#if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#if 指示詞 [C#]"
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #if (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 編譯器遇到 `#if` 指示詞，且最後接著 [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 指示詞時，只有在定義特定的符號時，編譯器才會編譯編譯器之間的程式碼。  不同於 C 與 C\+\+，您無法指派數值給符號，C\# 中的 \#if 陳述式為布林值，只能夠測試是否已經定義符號。  例如：  
  
```  
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 您只能夠使用 [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) \(相等\)、[\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) \(不相等\) 運算子，測試 [true](../../../csharp/language-reference/keywords/true.md) 或 [false](../../../csharp/language-reference/keywords/false.md) 的結果。  True 表示已定義符號。  陳述式 `#if DEBUG` 的意義等同於 `#if (DEBUG == true)`。  您可以使用&&運算子 \(和\)， [&#124;&#124;](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md) \(或\) 和 [\!](../../../csharp/language-reference/operators/logical-negation-operator.md)\(而非\) 評估多個符號是否已定義。  也可以使用括弧來群組符號和運算子。  
  
## 備註  
 `#if` 和 [\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、[\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)、[\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 及 [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 指示詞，可以讓您依據一個或多個符號項目，包含或排除程式碼。  這項功能在編譯偵錯組建程式碼，或是編譯特定組態時相當有用。  
  
 以 `#if` 指示詞開始的條件指示詞必須明確地以 `#endif` 指示詞結束。  
  
 `#define` 讓您將符號當做運算式傳遞至 `#if` 指示詞，以定義此符號，這個運算式將評估為 `true`。  
  
 您也可以使用 [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項定義符號。  使用 [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 取消符號定義。  
  
 使用 `/define` 或 `#define` 定義的符號並不會和具相同名稱的變數發生衝突。  這是因為變數名稱並不會傳遞至前置處理器指示詞，而符號只能由前置處理器指示詞進行評估。  
  
 使用 `#define` 建立的符號範圍是在定義此符號的檔案中。  
  
## 範例  
  
```  
// preprocessor_if.cs  
#define DEBUG #define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
  **定義 DEBUG 和 MYTEST**   
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)