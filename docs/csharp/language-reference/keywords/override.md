---
title: override 修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: bbdbcaf466e0b4dca4b78902ca9e7a49b02ac718
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394240"
---
# <a name="override-c-reference"></a><span data-ttu-id="64b8b-102">override (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="64b8b-102">override (C# Reference)</span></span>

<span data-ttu-id="64b8b-103">需要 `override` 修飾詞才能夠擴充或修改繼承方法、屬性、索引子或事件的抽象或虛擬實作。</span><span class="sxs-lookup"><span data-stu-id="64b8b-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="64b8b-104">範例</span><span class="sxs-lookup"><span data-stu-id="64b8b-104">Example</span></span>

<span data-ttu-id="64b8b-105">在此範例中， `Square`類別必須提供的`GetArea`覆寫實作為`GetArea` ，因為繼承自抽象`Shape`類：</span><span class="sxs-lookup"><span data-stu-id="64b8b-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="64b8b-106">`override` 方法提供繼承自基底類別的成員新實作。</span><span class="sxs-lookup"><span data-stu-id="64b8b-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="64b8b-107">`override` 宣告覆寫的方法稱之為覆寫基底方法。</span><span class="sxs-lookup"><span data-stu-id="64b8b-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="64b8b-108">覆寫基底方法必須和 `override` 方法有相同的簽章。</span><span class="sxs-lookup"><span data-stu-id="64b8b-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="64b8b-109">如需繼承的資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="64b8b-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="64b8b-110">您無法覆寫非虛擬或靜態方法。</span><span class="sxs-lookup"><span data-stu-id="64b8b-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="64b8b-111">覆寫基底方法必須是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="64b8b-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="64b8b-112">`override` 宣告不能變更 `virtual` 方法的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="64b8b-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="64b8b-113">`override` 方法和 `virtual` 方法都必須具有相同的[存取層級修飾詞](access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="64b8b-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="64b8b-114">您不能使用 `new`、`static` 或 `virtual` 修飾詞來修改 `override` 方法。</span><span class="sxs-lookup"><span data-stu-id="64b8b-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="64b8b-115">要覆寫的屬性宣告必須指定和繼承屬性完全相同的存取修飾詞、型別和名稱，而覆寫的屬性必須是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="64b8b-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="64b8b-116">如需如何使用 `override` 關鍵字的詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)和[了解使用 Override 和 New 關鍵字的時機](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="64b8b-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="64b8b-117">範例</span><span class="sxs-lookup"><span data-stu-id="64b8b-117">Example</span></span>

<span data-ttu-id="64b8b-118">本例會定義名為 `Employee` 的基底類別，以及名為 `SalesEmployee` 的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="64b8b-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="64b8b-119">`SalesEmployee` 類別包含額外的欄位 `salesbonus`，並會覆寫方法 `CalculatePay` 以將其納入考量。</span><span class="sxs-lookup"><span data-stu-id="64b8b-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="64b8b-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="64b8b-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="64b8b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64b8b-121">See also</span></span>

- [<span data-ttu-id="64b8b-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="64b8b-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="64b8b-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="64b8b-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="64b8b-124">繼承</span><span class="sxs-lookup"><span data-stu-id="64b8b-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="64b8b-125">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="64b8b-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="64b8b-126">修飾詞</span><span class="sxs-lookup"><span data-stu-id="64b8b-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="64b8b-127">abstract</span><span class="sxs-lookup"><span data-stu-id="64b8b-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="64b8b-128">virtual</span><span class="sxs-lookup"><span data-stu-id="64b8b-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="64b8b-129">new (修飾詞)</span><span class="sxs-lookup"><span data-stu-id="64b8b-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="64b8b-130">多型</span><span class="sxs-lookup"><span data-stu-id="64b8b-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
