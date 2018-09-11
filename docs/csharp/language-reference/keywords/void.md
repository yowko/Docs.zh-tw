---
title: void (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 223db893dd42181c234d9a07c1a1c00af26f0c30
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275578"
---
# <a name="void-c-reference"></a><span data-ttu-id="f077f-102">void (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f077f-102">void (C# Reference)</span></span>
<span data-ttu-id="f077f-103">當 `void` 作為方法的傳回型別時，其可指定方法不要傳回值。</span><span class="sxs-lookup"><span data-stu-id="f077f-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="f077f-104">方法的參數清單中不允許 `void`。</span><span class="sxs-lookup"><span data-stu-id="f077f-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="f077f-105">如果某方法不採用任何參數，且不傳回任何值，其宣告方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="f077f-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="f077f-106">`void` 也可用於不安全的內容中，以宣告未知類型的指標。</span><span class="sxs-lookup"><span data-stu-id="f077f-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="f077f-107">如需詳細資訊，請參閱[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f077f-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="f077f-108">`void` 是 .NET Framework <xref:System.Void?displayProperty=nameWithType> 類型的別名。</span><span class="sxs-lookup"><span data-stu-id="f077f-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f077f-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f077f-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f077f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f077f-110">See also</span></span>

- [<span data-ttu-id="f077f-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f077f-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f077f-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f077f-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f077f-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="f077f-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="f077f-114">參考型別</span><span class="sxs-lookup"><span data-stu-id="f077f-114">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="f077f-115">實值型別</span><span class="sxs-lookup"><span data-stu-id="f077f-115">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="f077f-116">方法</span><span class="sxs-lookup"><span data-stu-id="f077f-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="f077f-117">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="f077f-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
