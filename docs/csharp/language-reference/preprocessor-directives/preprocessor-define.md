---
title: '#define - C# 參考'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: d207c96621564acd8070c9d5f618f43a6d8f15a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924594"
---
# <a name="define-c-reference"></a>#define (C# 參考)
您可以使用 `#define` 來定義符號。 當您將符號作為運算式傳遞給 [#if](./preprocessor-if.md) 指示詞時，運算式會判斷值為 `true`，如下列範例所示：  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 如果常數值通常是在 C 和 C++ 中進行宣告，您就不能使用 `#define` 指示詞進行宣告。 在 C# 中的常數是特別定義為類別或結構的靜態成員。 如果您有數個這類常數，請考慮建立個別的「常數」類別來保留它們。  
  
 符號可以用來指定編譯的條件。 您可以使用 [#if](./preprocessor-if.md) 或 [#elif](./preprocessor-elif.md) 來測試符號。 您也可以使用 <xref:System.Diagnostics.ConditionalAttribute> 執行條件式編譯。  
  
 您可以定義符號，但不能將值指派給符號。 如果您要使用的任何指示並不是前置處理器指示詞，則檔案中必須先出現 `#define` 指示詞才行。  
  
 您也可以使用 [-define](../compiler-options/define-compiler-option.md) 編譯器選項來定義符號。 您可以使用 [#undef](./preprocessor-undef.md) 來取消定義符號。  
  
 透過 `-define` 或 `#define` 所定義的符號不會與相同名稱的變數發生衝突。 也就是說，您不應將變數名稱傳遞給前置處理器指示詞，而且符號僅能由前置處理器指示詞來評估。  
  
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
  
 如需如何取消定義符號的範例，請參閱 [#undef](./preprocessor-undef.md)。  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 前置處理器指示詞](./index.md)
- [const](../keywords/const.md)
- [如何：使用追蹤和偵錯進行條件式編譯](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [#undef](./preprocessor-undef.md)
- [#if](./preprocessor-if.md)
