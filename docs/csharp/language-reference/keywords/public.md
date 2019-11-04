---
title: public 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422551"
---
# <a name="public-c-reference"></a><span data-ttu-id="ef04c-102">public (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ef04c-102">public (C# Reference)</span></span>

<span data-ttu-id="ef04c-103">`public` 關鍵字是類型和類型成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="ef04c-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="ef04c-104">公用存取是最寬鬆的存取層級。</span><span class="sxs-lookup"><span data-stu-id="ef04c-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="ef04c-105">不會限制存取公用成員，如此範例所示︰</span><span class="sxs-lookup"><span data-stu-id="ef04c-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="ef04c-106">如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)和[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="ef04c-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="ef04c-107">範例</span><span class="sxs-lookup"><span data-stu-id="ef04c-107">Example</span></span>

<span data-ttu-id="ef04c-108">在下列範例中，宣告兩個類別：`PointTest` 和 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="ef04c-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="ef04c-109">`PointTest`的公用成員 `x` 和 `y` 直接存取自 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="ef04c-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="ef04c-110">如果您將 `public` 存取層級變更為 [private](private.md) 或 [protected](protected.md)，則會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="ef04c-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="ef04c-111">'PointTest.y' 的保護層級導致無法對其進行存取。</span><span class="sxs-lookup"><span data-stu-id="ef04c-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ef04c-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ef04c-112">C# language specification</span></span>  

<span data-ttu-id="ef04c-113">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[已宣告存取範圍](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="ef04c-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ef04c-114">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="ef04c-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef04c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ef04c-115">See also</span></span>

- [<span data-ttu-id="ef04c-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ef04c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ef04c-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ef04c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ef04c-118">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="ef04c-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="ef04c-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ef04c-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ef04c-120">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="ef04c-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="ef04c-121">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="ef04c-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="ef04c-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="ef04c-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ef04c-123">private</span><span class="sxs-lookup"><span data-stu-id="ef04c-123">private</span></span>](private.md)
- [<span data-ttu-id="ef04c-124">protected</span><span class="sxs-lookup"><span data-stu-id="ef04c-124">protected</span></span>](protected.md)
- [<span data-ttu-id="ef04c-125">internal</span><span class="sxs-lookup"><span data-stu-id="ef04c-125">internal</span></span>](internal.md)
