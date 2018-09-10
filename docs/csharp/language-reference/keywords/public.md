---
title: public 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 84a3bc49b6eea047d518edc01dab7f2301854b6a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518182"
---
# <a name="public-c-reference"></a><span data-ttu-id="c7a6f-102">public (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c7a6f-102">public (C# Reference)</span></span>

<span data-ttu-id="c7a6f-103">`public` 關鍵字是類型和類型成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c7a6f-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="c7a6f-104">公用存取是最寬鬆的存取層級。</span><span class="sxs-lookup"><span data-stu-id="c7a6f-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="c7a6f-105">不會限制存取公用成員，如此範例所示︰</span><span class="sxs-lookup"><span data-stu-id="c7a6f-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="c7a6f-106">如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)和[存取範圍層級](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a6f-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="c7a6f-107">範例</span><span class="sxs-lookup"><span data-stu-id="c7a6f-107">Example</span></span>

<span data-ttu-id="c7a6f-108">在下列範例中，宣告兩個類別：`PointTest` 和 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="c7a6f-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="c7a6f-109">`PointTest`的公用成員 `x` 和 `y` 直接存取自 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="c7a6f-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="c7a6f-110">如果您將 `public` 存取層級變更為 [private](private.md) 或 [protected](protected.md)，則會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="c7a6f-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="c7a6f-111">'PointTest.y' 的保護層級導致無法對其進行存取。</span><span class="sxs-lookup"><span data-stu-id="c7a6f-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7a6f-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c7a6f-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c7a6f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7a6f-113">See also</span></span>

- [<span data-ttu-id="c7a6f-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c7a6f-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7a6f-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c7a6f-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7a6f-116">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="c7a6f-116">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="c7a6f-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c7a6f-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c7a6f-118">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="c7a6f-118">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="c7a6f-119">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="c7a6f-119">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="c7a6f-120">修飾詞</span><span class="sxs-lookup"><span data-stu-id="c7a6f-120">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="c7a6f-121">private</span><span class="sxs-lookup"><span data-stu-id="c7a6f-121">private</span></span>](private.md)
- [<span data-ttu-id="c7a6f-122">protected</span><span class="sxs-lookup"><span data-stu-id="c7a6f-122">protected</span></span>](protected.md)
- [<span data-ttu-id="c7a6f-123">internal</span><span class="sxs-lookup"><span data-stu-id="c7a6f-123">internal</span></span>](internal.md)