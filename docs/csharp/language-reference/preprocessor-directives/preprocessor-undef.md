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
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150553"
---
# <a name="undef-c-reference"></a><span data-ttu-id="3f8e2-103">#undef (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3f8e2-103">#undef (C# Reference)</span></span>

<span data-ttu-id="3f8e2-104">`#undef` 可讓您取消定義符號，如此一來，在 [#if](./preprocessor-if.md) 指示詞中使用符號作為運算式，運算式就會評估為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3f8e2-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="3f8e2-105">您可以使用 [#define](./preprocessor-define.md) 指示詞或 [-define](../compiler-options/define-compiler-option.md) 編譯器選項來定義符號。</span><span class="sxs-lookup"><span data-stu-id="3f8e2-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="3f8e2-106">`#undef` 指示詞必須先出現在檔案中，才能使用亦非指示詞的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="3f8e2-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f8e2-107">範例</span><span class="sxs-lookup"><span data-stu-id="3f8e2-107">Example</span></span>  

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

<span data-ttu-id="3f8e2-108">**未定義 DEBUG**</span><span class="sxs-lookup"><span data-stu-id="3f8e2-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="3f8e2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f8e2-109">See also</span></span>

- [<span data-ttu-id="3f8e2-110">C # 參考</span><span class="sxs-lookup"><span data-stu-id="3f8e2-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f8e2-111">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3f8e2-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3f8e2-112">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="3f8e2-112">C# Preprocessor Directives</span></span>](./index.md)
