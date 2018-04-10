---
title: '#elif (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a><span data-ttu-id="c48c9-102">#elif (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c48c9-102">#elif (C# Reference)</span></span>
<span data-ttu-id="c48c9-103">`#elif` 可讓您建立複合條件指示詞。</span><span class="sxs-lookup"><span data-stu-id="c48c9-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="c48c9-104">如果前面的 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 和任何前面的選擇性 `#elif` 指示詞運算式都不是評估為 `true`，就會評估 `#elif` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c48c9-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="c48c9-105">如果 `#elif` 運算式評估為 `true`，編譯器會評估 `#elif` 與下一個條件指示詞之間的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="c48c9-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="c48c9-106">例如：</span><span class="sxs-lookup"><span data-stu-id="c48c9-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="c48c9-107">您可以使用 `==` (相等)、`!=` (不相等)、`&&` (和) 以及 `||` (或) 運算子來評估多個符號。</span><span class="sxs-lookup"><span data-stu-id="c48c9-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="c48c9-108">您也可以使用括弧來將符號和運算子分組。</span><span class="sxs-lookup"><span data-stu-id="c48c9-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c48c9-109">備註</span><span class="sxs-lookup"><span data-stu-id="c48c9-109">Remarks</span></span>  
 <span data-ttu-id="c48c9-110">`#elif` 相當於使用：</span><span class="sxs-lookup"><span data-stu-id="c48c9-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="c48c9-111">使用 `#elif` 更為簡單，因為每個 `#if` 都需要 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)，而 `#elif` 可以在沒有相符 `#endif` 的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="c48c9-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="c48c9-112">如需如何使用 `#elif` 的範例，請參閱 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="c48c9-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48c9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c48c9-113">See Also</span></span>  
 [<span data-ttu-id="c48c9-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c48c9-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c48c9-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c48c9-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c48c9-116">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="c48c9-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
