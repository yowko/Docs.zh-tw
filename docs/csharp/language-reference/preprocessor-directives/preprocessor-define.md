---
title: "#define (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#define'
dev_langs:
- CSharp
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 0db5a86fee1ed2139ae5046ada66121ffe8210b1
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="define-c-reference"></a>#define (C# 參考)
您可以使用 `#define` 來定義符號。 當您將符號作為運算式傳遞給 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞時，運算式會判斷值為 `true`，如下列範例所示：  
  
 `#`  `define`   `DEBUG`  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  如果常數值通常是在 C 和 C++ 中進行宣告，您就不能使用 `#define` 指示詞進行宣告。 在 C# 中的常數是特別定義為類別或結構的靜態成員。 如果您有數個這類常數，請考慮建立個別的「常數」類別來保留它們。  
  
 符號可以用來指定編譯的條件。 您可以使用 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 來測試符號。 您也可以使用 `conditional` 屬性來執行條件式編譯。  
  
 您可以定義符號，但不能將值指派給符號。 如果您要使用的任何指示並不是前置處理器指示詞，則檔案中必須先出現 `#define` 指示詞才行。  
  
 您也可以使用 [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項來定義符號。 您可以使用 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 來取消定義符號。  
  
 透過 `/define` 或 `#define` 所定義的符號不會與相同名稱的變數發生衝突。 也就是說，您不應將變數名稱傳遞給前置處理器指示詞，而且符號僅能由前置處理器指示詞來評估。  
  
 使用 `#define` 所建立的符號範圍即為定義符號的檔案。  
  
 如下列範例所示，您必須將 `#define` 指示詞放在檔案頂端。  
  
```csharp  
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
  
 如需如何取消定義符號的範例，請參閱 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [如何：使用追蹤和偵錯進行條件式編譯](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)   
 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)   
 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
