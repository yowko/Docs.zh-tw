---
description: '#undef - C# 參考'
title: '#undef - C# 參考'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91150553"
---
# <a name="undef-c-reference"></a>#undef (C# 參考)

`#undef` 可讓您取消定義符號，如此一來，在 [#if](./preprocessor-if.md) 指示詞中使用符號作為運算式，運算式就會評估為 `false`。  
  
 您可以使用 [#define](./preprocessor-define.md) 指示詞或 [-define](../compiler-options/define-compiler-option.md) 編譯器選項來定義符號。 `#undef` 指示詞必須先出現在檔案中，才能使用亦非指示詞的任何陳述式。  
  
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

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 預處理器指示詞](./index.md)
