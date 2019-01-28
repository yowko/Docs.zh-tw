---
title: '#define - C# 參考'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 3b543181e3d836226759e77f0d56ed3c3e57e7ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696200"
---
# <a name="define-c-reference"></a><span data-ttu-id="8f0a0-102">#define (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8f0a0-102">#define (C# Reference)</span></span>
<span data-ttu-id="8f0a0-103">您可以使用 `#define` 來定義符號。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="8f0a0-104">當您將符號作為運算式傳遞給 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 指示詞時，運算式會判斷值為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8f0a0-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="8f0a0-105">備註</span><span class="sxs-lookup"><span data-stu-id="8f0a0-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f0a0-106">如果常數值通常是在 C 和 C++ 中進行宣告，您就不能使用 `#define` 指示詞進行宣告。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="8f0a0-107">在 C# 中的常數是特別定義為類別或結構的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="8f0a0-108">如果您有數個這類常數，請考慮建立個別的「常數」類別來保留它們。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="8f0a0-109">符號可以用來指定編譯的條件。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="8f0a0-110">您可以使用 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 或 [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) 來測試符號。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="8f0a0-111">您也可以使用 <xref:System.Diagnostics.ConditionalAttribute> 執行條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="8f0a0-112">您可以定義符號，但不能將值指派給符號。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="8f0a0-113">如果您要使用的任何指示並不是前置處理器指示詞，則檔案中必須先出現 `#define` 指示詞才行。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="8f0a0-114">您也可以使用 [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項來定義符號。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-114">You can also define a symbol with the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="8f0a0-115">您可以使用 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 來取消定義符號。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="8f0a0-116">透過 `-define` 或 `#define` 所定義的符號不會與相同名稱的變數發生衝突。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="8f0a0-117">也就是說，您不應將變數名稱傳遞給前置處理器指示詞，而且符號僅能由前置處理器指示詞來評估。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="8f0a0-118">使用 `#define` 所建立的符號範圍即為定義符號的檔案。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="8f0a0-119">如下列範例所示，您必須將 `#define` 指示詞放在檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="8f0a0-120">如需如何取消定義符號的範例，請參閱 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)。</span><span class="sxs-lookup"><span data-stu-id="8f0a0-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0a0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f0a0-121">See also</span></span>

- [<span data-ttu-id="8f0a0-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8f0a0-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="8f0a0-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8f0a0-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8f0a0-124">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="8f0a0-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
- [<span data-ttu-id="8f0a0-125">const</span><span class="sxs-lookup"><span data-stu-id="8f0a0-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)
- [<span data-ttu-id="8f0a0-126">如何：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="8f0a0-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="8f0a0-127">#undef</span><span class="sxs-lookup"><span data-stu-id="8f0a0-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="8f0a0-128">#if</span><span class="sxs-lookup"><span data-stu-id="8f0a0-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
