---
title: "#<a name=\"undef-c-reference\"></a>undef (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#undef'
helpviewer_keywords: '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a>#undef (C# 參考)
`#undef` 可讓您取消定義符號，如此一來，在 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞中使用符號作為運算式，運算式就會評估為 `false`。  
  
 使用 [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 指示詞或 [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項可以定義符號。 `#undef` 指示詞必須先出現在檔案中，才能使用亦非指示詞的任何陳述式。  
  
## <a name="example"></a>範例  
  
```csharp
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
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
