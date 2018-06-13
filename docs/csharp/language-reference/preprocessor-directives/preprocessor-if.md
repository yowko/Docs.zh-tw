---
title: '#if 前置處理器指示詞 (C# 參考)'
ms.date: 02/13/2017
f1_keywords:
- '#if'
helpviewer_keywords:
- '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
ms.openlocfilehash: 2ae0af6971dbf549b52e8168e035d8582bdab61d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287679"
---
# <a name="if-c-reference"></a><span data-ttu-id="eb8a8-102">#if (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="eb8a8-102">#if (C# Reference)</span></span>

<span data-ttu-id="eb8a8-103">當 C# 編譯器遇到 `#if` 指示詞，且其後接著 [#endif](preprocessor-endif.md) 指示詞時，只有在定義了指定的符號時，它才會編譯指示詞之間的程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-103">When the C# compiler encounters an `#if` directive, followed eventually by an [#endif](preprocessor-endif.md) directive, it compiles the code between the directives only if the specified symbol is defined.</span></span> <span data-ttu-id="eb8a8-104">不同於 C 和 C++，您無法將數值指派給符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-104">Unlike C and C++, you cannot assign a numeric value to a symbol.</span></span> <span data-ttu-id="eb8a8-105">C# 中的 #if 陳述式是布林值，且只測試是否已經定義符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-105">The #if statement in C# is Boolean and only tests whether the symbol has been defined or not.</span></span> <span data-ttu-id="eb8a8-106">例如: </span><span class="sxs-lookup"><span data-stu-id="eb8a8-106">For example:</span></span>

```csharp
#if DEBUG
    Console.WriteLine("Debug version");
#endif
```

<span data-ttu-id="eb8a8-107">您只能使用運算子 [==](../operators/equality-comparison-operator.md) (相等) 和 [!=](../operators/not-equal-operator.md) (不等) 來測試 [true](../keywords/true.md) 或 [false](../keywords/false.md)。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-107">You can use the operators [==](../operators/equality-comparison-operator.md) (equality) and [!=](../operators/not-equal-operator.md) (inequality) only to test for [true](../keywords/true.md) or [false](../keywords/false.md).</span></span> <span data-ttu-id="eb8a8-108">True 表示已定義符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-108">True means the symbol is defined.</span></span> <span data-ttu-id="eb8a8-109">`#if DEBUG` 陳述式的意義與 `#if (DEBUG == true)` 一樣。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-109">The statement `#if DEBUG` has the same meaning as `#if (DEBUG == true)`.</span></span> <span data-ttu-id="eb8a8-110">您可以使用運算子 [&&](../operators/conditional-and-operator.md) (且)、[&#124;&#124;](../operators/conditional-or-operator.md) (或) 及 [!](../operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="eb8a8-110">You can use the operators [&&](../operators/conditional-and-operator.md) (and), [&#124;&#124;](../operators/conditional-or-operator.md) (or), and [!](../operators/logical-negation-operator.md)</span></span> <span data-ttu-id="eb8a8-111">(非)，來評估是否已定義多個符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-111">(not) to evaluate whether multiple symbols have been defined.</span></span> <span data-ttu-id="eb8a8-112">您也可以使用括弧來將符號和運算子分組。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-112">You can also group symbols and operators with parentheses.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb8a8-113">備註</span><span class="sxs-lookup"><span data-stu-id="eb8a8-113">Remarks</span></span>

<span data-ttu-id="eb8a8-114">`#if` 連同 [#else](preprocessor-else.md)、[#elif](preprocessor-elif.md)、[#endif](preprocessor-endif.md)、[#define](preprocessor-define.md) 及 [#undef](preprocessor-undef.md) 指示詞，可讓您根據一或多個符號是否存在來包含或排除程式碼。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-114">`#if`, along with the [#else](preprocessor-else.md), [#elif](preprocessor-elif.md), [#endif](preprocessor-endif.md), [#define](preprocessor-define.md), and [#undef](preprocessor-undef.md) directives, lets you include or exclude code based on the existence of one or more symbols.</span></span> <span data-ttu-id="eb8a8-115">在編譯偵錯組建的程式碼時，或是在針對特定組態進行編譯時，這非常實用。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-115">This can be useful when compiling code for a debug build or when compiling for a specific configuration.</span></span>

<span data-ttu-id="eb8a8-116">以 `#if` 指示詞開頭的條件式指示詞必須明確地以 `#endif` 指示詞終止。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-116">A conditional directive beginning with a `#if` directive must explicitly be terminated with a `#endif` directive.</span></span>

<span data-ttu-id="eb8a8-117">`#define` 可讓您定義符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-117">`#define` lets you define a symbol.</span></span> <span data-ttu-id="eb8a8-118">屆時，使用該符號作為傳遞到 `#if` 指示詞的運算式，運算式就會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-118">By then using the symbol as the expression passed to the `#if` directive, the expression evaluates to `true`.</span></span>

<span data-ttu-id="eb8a8-119">您也可以使用 [/define](../compiler-options/define-compiler-option.md) 編譯器選項來定義符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-119">You can also define a symbol with the [/define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="eb8a8-120">您可以使用 [#undef](preprocessor-undef.md) 來取消定義符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-120">You can undefine a symbol with [#undef](preprocessor-undef.md).</span></span>

<span data-ttu-id="eb8a8-121">透過 `/define` 或 `#define` 定義的符號不會與相同名稱的變數發生衝突。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-121">A symbol that you define with `/define` or with `#define` doesn't conflict with a variable of the same name.</span></span> <span data-ttu-id="eb8a8-122">也就是說，您不應將變數名稱傳遞給前置處理器指示詞，而且符號僅能由前置處理器指示詞來評估。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-122">That is, a variable name should not be passed to a preprocessor directive, and a symbol can only be evaluated by a preprocessor directive.</span></span>

<span data-ttu-id="eb8a8-123">使用 `#define` 建立的符號範圍是定義它的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-123">The scope of a symbol created with `#define` is the file in which it was defined.</span></span>

<span data-ttu-id="eb8a8-124">建置系統也能分辨代表不同[目標 Framework](../../../standard/frameworks.md) 的預先定義前置處理器符號。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-124">The build system is also aware of predefined preprocessor symbols representing different [target frameworks](../../../standard/frameworks.md).</span></span> <span data-ttu-id="eb8a8-125">若要建立能以多個 .NET 實作或版本為目標的應用程式，這些符號就很實用。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-125">They're useful when creating applications that can target more than one .NET implementation or version.</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="eb8a8-126">其他預先定義符號包括 DEBUG 和 TRACE 常數。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-126">Other predefined symbols include the DEBUG and TRACE constants.</span></span> <span data-ttu-id="eb8a8-127">您可以使用 `#define` 來覆寫為專案所設定的值。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-127">You can override the values set for the project using `#define`.</span></span> <span data-ttu-id="eb8a8-128">例如，DEBUG 符號會根據您的組建組態屬性 ("Debug" 或 "Release" 模式) 而自動設定。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-128">The DEBUG symbol, for example, is automatically set depending on your build configuration properties ("Debug" or "Release" mode).</span></span>

## <a name="examples"></a><span data-ttu-id="eb8a8-129">範例</span><span class="sxs-lookup"><span data-stu-id="eb8a8-129">Examples</span></span>

<span data-ttu-id="eb8a8-130">以下範例說明如何在檔案上定義 MYTEST 符號，然後測試 MYTEST 和 DEBUG 符號的值。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-130">The following example shows you how to define a MYTEST symbol on a file and then test the values of the MYTEST and DEBUG symbols.</span></span> <span data-ttu-id="eb8a8-131">此範例的輸出視您使用 Debug 或 Release 組態模式建置專案而有所不同。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-131">The output of this example depends on whether you built the project on Debug or Release configuration mode.</span></span>

```csharp
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

<span data-ttu-id="eb8a8-132">以下範例說明如何測試不同的目標 Framework，讓您可以盡可能使用較新的 API：</span><span class="sxs-lookup"><span data-stu-id="eb8a8-132">The following example shows you how to test for different target frameworks so you can use newer APIs when possible:</span></span>

```csharp
public class MyClass
{
    static void Main()
    {
#if NET40
        WebClient _client = new WebClient();
#else
        HttpClient _client = new HttpClient();
#endif
    }
    //...
}
```

## <a name="see-also"></a><span data-ttu-id="eb8a8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb8a8-133">See also</span></span>

[<span data-ttu-id="eb8a8-134">C# 參考</span><span class="sxs-lookup"><span data-stu-id="eb8a8-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="eb8a8-135">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="eb8a8-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="eb8a8-136">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="eb8a8-136">C# Preprocessor Directives</span></span>](index.md)  
<span data-ttu-id="eb8a8-137">[如何：使用追蹤和偵錯進行條件式編譯](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)。</span><span class="sxs-lookup"><span data-stu-id="eb8a8-137">[How to: Compile Conditionally with Trace and Debug](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).</span></span>
