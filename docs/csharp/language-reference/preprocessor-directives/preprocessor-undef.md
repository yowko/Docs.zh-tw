---
title: '#undef - C# 參考'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 5a3658c4e6bb32158e6f81c3ac5014fbedba0713
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235754"
---
# <a name="undef-c-reference"></a><span data-ttu-id="d8abd-102">#undef (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d8abd-102">#undef (C# Reference)</span></span>
<span data-ttu-id="d8abd-103">`#undef` 可讓您取消定義符號，如此一來，在 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞中使用符號作為運算式，運算式就會評估為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d8abd-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="d8abd-104">使用 [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 指示詞或 [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項可以定義符號。</span><span class="sxs-lookup"><span data-stu-id="d8abd-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="d8abd-105">`#undef` 指示詞必須先出現在檔案中，才能使用亦非指示詞的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8abd-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8abd-106">範例</span><span class="sxs-lookup"><span data-stu-id="d8abd-106">Example</span></span>  

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

<span data-ttu-id="d8abd-107">**未定義 DEBUG**</span><span class="sxs-lookup"><span data-stu-id="d8abd-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="d8abd-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8abd-108">See Also</span></span>

- [<span data-ttu-id="d8abd-109">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d8abd-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d8abd-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d8abd-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d8abd-111">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="d8abd-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
