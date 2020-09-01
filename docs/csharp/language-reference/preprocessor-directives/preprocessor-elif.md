---
description: '#elif - C# 參考'
title: '#elif - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 3aa9082b392b352091b9fde74a85f9dd155ad7b1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132283"
---
# <a name="elif-c-reference"></a><span data-ttu-id="7b762-103">#elif (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7b762-103">#elif (C# Reference)</span></span>
<span data-ttu-id="7b762-104">`#elif` 可讓您建立複合條件指示詞。</span><span class="sxs-lookup"><span data-stu-id="7b762-104">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="7b762-105">如果前面的 [#if](./preprocessor-if.md) 和任何前面的選擇性 `#elif` 指示詞運算式都不是評估為 `true`，就會評估 `#elif` 運算式。</span><span class="sxs-lookup"><span data-stu-id="7b762-105">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="7b762-106">如果 `#elif` 運算式評估為 `true`，編譯器會評估 `#elif` 與下一個條件指示詞之間的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b762-106">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="7b762-107">例如：</span><span class="sxs-lookup"><span data-stu-id="7b762-107">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="7b762-108">您可以使用 `==` (相等)、`!=` (不相等)、`&&` (和) 以及 `||` (或) 運算子來評估多個符號。</span><span class="sxs-lookup"><span data-stu-id="7b762-108">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="7b762-109">您也可以使用括弧來將符號和運算子分組。</span><span class="sxs-lookup"><span data-stu-id="7b762-109">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b762-110">備註</span><span class="sxs-lookup"><span data-stu-id="7b762-110">Remarks</span></span>  
 <span data-ttu-id="7b762-111">`#elif` 相當於使用：</span><span class="sxs-lookup"><span data-stu-id="7b762-111">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="7b762-112">使用 `#elif` 更為簡單，因為每個 `#if` 都需要 [#endif](./preprocessor-endif.md)，而 `#elif` 可以在沒有相符 `#endif` 的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="7b762-112">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="7b762-113">如需如何使用 `#elif` 的範例，請參閱 [#if](./preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="7b762-113">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b762-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b762-114">See also</span></span>

- [<span data-ttu-id="7b762-115">C # 參考</span><span class="sxs-lookup"><span data-stu-id="7b762-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b762-116">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7b762-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b762-117">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="7b762-117">C# Preprocessor Directives</span></span>](./index.md)
