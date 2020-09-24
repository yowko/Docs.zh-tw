---
description: '#define - C# 參考'
title: '#define - C# 參考'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 961c20c091a4a6d7da421d94500abd41d2d60a5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160498"
---
# <a name="define-c-reference"></a><span data-ttu-id="78e43-103">#define (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="78e43-103">#define (C# Reference)</span></span>

<span data-ttu-id="78e43-104">您可以使用 `#define` 來定義符號。</span><span class="sxs-lookup"><span data-stu-id="78e43-104">You use `#define` to define a symbol.</span></span> <span data-ttu-id="78e43-105">當您將符號作為運算式傳遞給 [#if](./preprocessor-if.md) 指示詞時，運算式會判斷值為 `true`，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="78e43-105">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="78e43-106">備註</span><span class="sxs-lookup"><span data-stu-id="78e43-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78e43-107">如果常數值通常是在 C 和 C++ 中進行宣告，您就不能使用 `#define` 指示詞進行宣告。</span><span class="sxs-lookup"><span data-stu-id="78e43-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="78e43-108">在 C# 中的常數是特別定義為類別或結構的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="78e43-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="78e43-109">如果您有數個這類常數，請考慮建立個別的「常數」類別來保留它們。</span><span class="sxs-lookup"><span data-stu-id="78e43-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="78e43-110">符號可以用來指定編譯的條件。</span><span class="sxs-lookup"><span data-stu-id="78e43-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="78e43-111">您可以使用 [#if](./preprocessor-if.md) 或 [#elif](./preprocessor-elif.md) 來測試符號。</span><span class="sxs-lookup"><span data-stu-id="78e43-111">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="78e43-112">您也可以使用 <xref:System.Diagnostics.ConditionalAttribute> 執行條件式編譯。</span><span class="sxs-lookup"><span data-stu-id="78e43-112">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="78e43-113">您可以定義符號，但不能將值指派給符號。</span><span class="sxs-lookup"><span data-stu-id="78e43-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="78e43-114">如果您要使用的任何指示並不是前置處理器指示詞，則檔案中必須先出現 `#define` 指示詞才行。</span><span class="sxs-lookup"><span data-stu-id="78e43-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="78e43-115">您也可以使用 [-define](../compiler-options/define-compiler-option.md) 編譯器選項來定義符號。</span><span class="sxs-lookup"><span data-stu-id="78e43-115">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="78e43-116">您可以使用 [#undef](./preprocessor-undef.md) 來取消定義符號。</span><span class="sxs-lookup"><span data-stu-id="78e43-116">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="78e43-117">透過 `-define` 或 `#define` 所定義的符號不會與相同名稱的變數發生衝突。</span><span class="sxs-lookup"><span data-stu-id="78e43-117">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="78e43-118">也就是，不應將變數名稱傳遞給前置處理器指示詞，而符號僅能由前置處理器指示詞評估。</span><span class="sxs-lookup"><span data-stu-id="78e43-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="78e43-119">使用 `#define` 所建立的符號範圍即為定義符號的檔案。</span><span class="sxs-lookup"><span data-stu-id="78e43-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="78e43-120">如下列範例所示，您必須將 `#define` 指示詞放在檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="78e43-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="78e43-121">如需如何取消定義符號的範例，請參閱 [#undef](./preprocessor-undef.md)。</span><span class="sxs-lookup"><span data-stu-id="78e43-121">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e43-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78e43-122">See also</span></span>

- [<span data-ttu-id="78e43-123">C # 參考</span><span class="sxs-lookup"><span data-stu-id="78e43-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="78e43-124">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="78e43-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="78e43-125">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="78e43-125">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="78e43-126">const</span><span class="sxs-lookup"><span data-stu-id="78e43-126">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="78e43-127">作法：使用追蹤和偵錯進行條件式編譯</span><span class="sxs-lookup"><span data-stu-id="78e43-127">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="78e43-128">#undef</span><span class="sxs-lookup"><span data-stu-id="78e43-128">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="78e43-129">#if</span><span class="sxs-lookup"><span data-stu-id="78e43-129">#if</span></span>](./preprocessor-if.md)
