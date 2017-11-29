---
title: "#<a name=\"if-c-reference\"></a>if (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a><span data-ttu-id="76202-102">#if (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="76202-102">#if (C# Reference)</span></span>
<span data-ttu-id="76202-103">當 C# 編譯器遇到 `#if` 指示詞 (最後面接著 [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) 指示詞) 時，只有在定義了指定的符號時，它才會編譯指示詞之間的程式碼。</span><span class="sxs-lookup"><span data-stu-id="76202-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) directive, it will compile the code between the directives only if the specified symbol is defined.</span></span>  <span data-ttu-id="76202-104">不同於 C 和 C++，您無法將數值指派給符號；C# 中的 #if 陳述式是布林值，只會測試是否已定義符號。</span><span class="sxs-lookup"><span data-stu-id="76202-104">Unlike C and C++, you cannot assign a numeric value to a symbol; the #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="76202-105">例如：</span><span class="sxs-lookup"><span data-stu-id="76202-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 <span data-ttu-id="76202-106">您可以只使用運算子 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (相等)、[!=](../../../csharp/language-reference/operators/not-equal-operator.md) (不等) 來測試 [true](../../../csharp/language-reference/keywords/true.md) 或 [false](../../../csharp/language-reference/keywords/false.md)。</span><span class="sxs-lookup"><span data-stu-id="76202-106">You can use the operators [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (equality), [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (inequality) only to test for [true](../../../csharp/language-reference/keywords/true.md) or [false](../../../csharp/language-reference/keywords/false.md) .</span></span> <span data-ttu-id="76202-107">True 表示已定義符號。</span><span class="sxs-lookup"><span data-stu-id="76202-107">True means the symbol is defined.</span></span> <span data-ttu-id="76202-108">`#if DEBUG` 陳述式的意義與 `#if (DEBUG == true)` 一樣。</span><span class="sxs-lookup"><span data-stu-id="76202-108">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="76202-109">您可以使用運算子 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (且)、[&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (或) 及 [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="76202-109">You can use the operators [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (and), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (or), and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="76202-110">(非)，來評估是否已定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="76202-110">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="76202-111">您也可以使用括弧來將符號和運算子分組。</span><span class="sxs-lookup"><span data-stu-id="76202-111">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76202-112">備註</span><span class="sxs-lookup"><span data-stu-id="76202-112">Remarks</span></span>  
 <span data-ttu-id="76202-113">`#if` 連同 [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 及 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 指示詞，可讓您根據一或多個符號是否存在來包含或排除程式碼。</span><span class="sxs-lookup"><span data-stu-id="76202-113">`#if`, along with the [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md), [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), and [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="76202-114">在編譯偵錯組建的程式碼時，或是在針對特定組態進行編譯時，這非常實用。</span><span class="sxs-lookup"><span data-stu-id="76202-114">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>  
  
 <span data-ttu-id="76202-115">以 `#if` 指示詞開頭的條件式指示詞必須明確地以 `#endif` 指示詞終止。</span><span class="sxs-lookup"><span data-stu-id="76202-115">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>  
  
 <span data-ttu-id="76202-116">`#define` 可讓您定義符號，如此一來，將定義的符號用於運算式並傳遞到 `#if` 指示詞時，運算式就會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="76202-116">`#define` lets you define a symbol, such that, by using the symbol as the expression passed to the `#if` directive, the expression will evaluate to `true`.</span></span>  
  
 <span data-ttu-id="76202-117">您也可以使用 [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) 編譯器選項來定義符號。</span><span class="sxs-lookup"><span data-stu-id="76202-117">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="76202-118">您可以使用 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) 來取消定義符號。</span><span class="sxs-lookup"><span data-stu-id="76202-118">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="76202-119">透過 `/define` 或 `#define` 所定義的符號不會與相同名稱的變數發生衝突。</span><span class="sxs-lookup"><span data-stu-id="76202-119">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="76202-120">也就是，不應將變數名稱傳遞給前置處理器指示詞，而符號僅能由前置處理器指示詞評估。</span><span class="sxs-lookup"><span data-stu-id="76202-120">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="76202-121">使用 `#define` 建立的符號範圍是定義它的檔案。</span><span class="sxs-lookup"><span data-stu-id="76202-121">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76202-122">範例</span><span class="sxs-lookup"><span data-stu-id="76202-122">Example</span></span>  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
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
  
 <span data-ttu-id="76202-123">**已定義 DEBUG 和 MYTEST**</span><span class="sxs-lookup"><span data-stu-id="76202-123">**DEBUG and MYTEST are defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="76202-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76202-124">See Also</span></span>  
 [<span data-ttu-id="76202-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="76202-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="76202-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="76202-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="76202-127">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="76202-127">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
