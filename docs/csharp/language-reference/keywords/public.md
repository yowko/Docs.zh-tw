---
description: public 關鍵字 - C# 參考
title: public 關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 26edaf7538d11d082a4b8863228213c3ebc46937
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122338"
---
# <a name="public-c-reference"></a><span data-ttu-id="68a9b-103">public (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="68a9b-103">public (C# Reference)</span></span>

<span data-ttu-id="68a9b-104">`public` 關鍵字是類型和類型成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="68a9b-104">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="68a9b-105">公用存取是最寬鬆的存取層級。</span><span class="sxs-lookup"><span data-stu-id="68a9b-105">Public access is the most permissive access level.</span></span> <span data-ttu-id="68a9b-106">不會限制存取公用成員，如此範例所示︰</span><span class="sxs-lookup"><span data-stu-id="68a9b-106">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="68a9b-107">如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)和[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="68a9b-107">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="68a9b-108">範例</span><span class="sxs-lookup"><span data-stu-id="68a9b-108">Example</span></span>

<span data-ttu-id="68a9b-109">在下列範例中，宣告兩個類別：`PointTest` 和 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="68a9b-109">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="68a9b-110">`PointTest`的公用成員 `x` 和 `y` 直接存取自 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="68a9b-110">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="68a9b-111">如果您將 `public` 存取層級變更為 [private](private.md) 或 [protected](protected.md)，則會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="68a9b-111">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="68a9b-112">'PointTest.y' 的保護層級導致無法對其進行存取。</span><span class="sxs-lookup"><span data-stu-id="68a9b-112">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68a9b-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="68a9b-113">C# language specification</span></span>  

<span data-ttu-id="68a9b-114">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[已宣告存取範圍](~/_csharplang/spec/basic-concepts.md#declared-accessibility)。</span><span class="sxs-lookup"><span data-stu-id="68a9b-114">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="68a9b-115">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="68a9b-115">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="68a9b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68a9b-116">See also</span></span>

- [<span data-ttu-id="68a9b-117">C # 參考</span><span class="sxs-lookup"><span data-stu-id="68a9b-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="68a9b-118">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="68a9b-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="68a9b-119">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="68a9b-119">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="68a9b-120">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="68a9b-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="68a9b-121">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="68a9b-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="68a9b-122">協助工具層級</span><span class="sxs-lookup"><span data-stu-id="68a9b-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="68a9b-123">修飾詞</span><span class="sxs-lookup"><span data-stu-id="68a9b-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="68a9b-124">私人</span><span class="sxs-lookup"><span data-stu-id="68a9b-124">private</span></span>](private.md)
- [<span data-ttu-id="68a9b-125">protected</span><span class="sxs-lookup"><span data-stu-id="68a9b-125">protected</span></span>](protected.md)
- [<span data-ttu-id="68a9b-126">internal</span><span class="sxs-lookup"><span data-stu-id="68a9b-126">internal</span></span>](internal.md)
