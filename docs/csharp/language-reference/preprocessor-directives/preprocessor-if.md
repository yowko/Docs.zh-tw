---
title: "#<a name=\"if-c-reference--microsoft-docs\"></a>if (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#if'
dev_langs:
- CSharp
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: 17
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
ms.sourcegitcommit: a780a11d8dd238187eb82933359bbb151bb3c333
ms.openlocfilehash: 4fc51446d297015d9e492703c9b1868c3b513c53
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="if-c-reference"></a>#if (C# 參考)
當 C# 編譯器遇到 `#if` 指示詞 (最後面接著 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 指示詞) 時，只有在定義了指定的符號時，它才會編譯指示詞之間的程式碼。  不同於 C 和 C++，您無法將數值指派給符號；C# 中的 #if 陳述式是布林值，只會測試是否已定義符號。 例如：  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 您可以只使用運算子 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (相等)、[!=](../../../csharp/language-reference/operators/not-equal-operator.md) (不等) 來測試 [true](../../../csharp/language-reference/keywords/true.md) 或 [false](../../../csharp/language-reference/keywords/false.md)。 True 表示已定義符號。 `#if DEBUG` 陳述式的意義與 `#if (DEBUG == true)` 一樣。 您可以使用運算子 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (且)、[&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (或) 及 [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (非)，來評估是否已定義多個符號。 您也可以使用括弧來將符號和運算子分組。  
  
## <a name="remarks"></a>備註  
 `#if` 連同 [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 及 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 指示詞，可讓您根據一或多個符號是否存在來包含或排除程式碼。 在編譯偵錯組建的程式碼時，或是在針對特定組態進行編譯時，這非常實用。  
  
 以 `#if` 指示詞開頭的條件式指示詞必須明確地以 `#endif` 指示詞終止。  
  
 `#define` 可讓您定義符號，如此一來，將定義的符號用於運算式並傳遞到 `#if` 指示詞時，運算式就會評估為 `true`。  
  
 您也可以使用 [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項來定義符號。 您可以使用 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 來取消定義符號。  
  
 您使用 `/define` 或 `#define` 定義的符號不會與相同名稱的變數發生衝突。 也就是，不應將變數名稱傳遞給前置處理器指示詞，而符號僅能由前置處理器指示詞評估。  
  
 使用 `#define` 建立的符號範圍是定義它的檔案。  
  
## <a name="example"></a>範例  
  
```csharp
// preprocessor_if.cs  
#define DEBUG#define MYTEST  
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
  
 **已定義 DEBUG 和 MYTEST**   
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)

