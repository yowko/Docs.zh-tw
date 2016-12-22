---
title: "#define (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#define"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#define 指示詞 [C#]"
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #define (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以使用 `#define` 來定義符號。  當您以符號當做運算式傳遞至 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞時，這個運算式將評估為 `true`，如下列範例所示：  
  
 `#`  `define`   `DEBUG`  
  
## 備註  
  
> [!NOTE]
>  `#define` 指示詞無法用來宣告一般在 C 和 C\+\+ 中執行的常數值。  C\# 中的常數最好定義為 class 或 struct 的靜態成員。  如果擁有多個此類常數，請考慮建立個別的 "Constants" 類別來保存這些常數。  
  
 符號可以用來指定編譯條件。  您可以使用 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 測試符號。  您也可以使用 `conditional` 屬性來執行條件式編譯。  
  
 您可以定義符號，但是不能指定值給符號。  `#define` 指示詞必須已出現在檔案中，然後才能使用任何非同時為前置處理器指示詞的指令。  
  
 您也可以使用 [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項定義符號。  使用 [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 取消符號定義。  
  
 使用 `/define` 或 `#define` 定義的符號並不會和具相同名稱的變數發生衝突。  這是因為變數名稱並不會傳遞至前置處理器指示詞，而符號只能由前置處理器指示詞進行評估。  
  
 使用 `#define` 建立的符號範圍是定義此符號的檔案。  
  
 如下列範例所示，您必須將 `#define` 指示詞放在檔案的頂端。  
  
```c#  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 如需有關定義符號的範例，請參閱[\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [How to: Compile Conditionally with Trace and Debug](../Topic/How%20to:%20Compile%20Conditionally%20with%20Trace%20and%20Debug.md)   
 [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)   
 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)