---
description: override 修飾詞 - C# 參考
title: override 修飾詞 - C# 參考
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434883"
---
# <a name="override-c-reference"></a><span data-ttu-id="6ef86-103">覆寫 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="6ef86-103">override (C# reference)</span></span>

<span data-ttu-id="6ef86-104">需要 `override` 修飾詞才能夠擴充或修改繼承方法、屬性、索引子或事件的抽象或虛擬實作。</span><span class="sxs-lookup"><span data-stu-id="6ef86-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

<span data-ttu-id="6ef86-105">在下列範例中， `Square` 類別必須提供的覆寫實作為， `GetArea` 因為 `GetArea` 是繼承自抽象 `Shape` 類：</span><span class="sxs-lookup"><span data-stu-id="6ef86-105">In the following example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="6ef86-106">`override`方法會提供繼承自基類之方法的新實作為。</span><span class="sxs-lookup"><span data-stu-id="6ef86-106">An `override` method provides a new implementation of the method inherited from a base class.</span></span> <span data-ttu-id="6ef86-107">`override` 宣告覆寫的方法稱之為覆寫基底方法。</span><span class="sxs-lookup"><span data-stu-id="6ef86-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="6ef86-108">方法的簽章必須與覆 `override` 寫基底方法的簽章相同。</span><span class="sxs-lookup"><span data-stu-id="6ef86-108">An `override` method must have the same signature as the overridden base method.</span></span> <span data-ttu-id="6ef86-109">從 c # 9.0 開始，方法支援協變數傳回型別 `override` 。</span><span class="sxs-lookup"><span data-stu-id="6ef86-109">Beginning with C# 9.0, `override` methods support covariant return types.</span></span> <span data-ttu-id="6ef86-110">尤其是，方法的傳回型別 `override` 可以衍生自對應基底方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="6ef86-110">In particular, the return type of an `override` method can derive from the return type of the corresponding base method.</span></span> <span data-ttu-id="6ef86-111">在 c # 8.0 及更早版本中，方法的傳回類型 `override` 和覆寫的基底方法必須相同。</span><span class="sxs-lookup"><span data-stu-id="6ef86-111">In C# 8.0 and earlier, the return types of an `override` method and the overridden base method must be the same.</span></span>

<span data-ttu-id="6ef86-112">您無法覆寫非虛擬或靜態方法。</span><span class="sxs-lookup"><span data-stu-id="6ef86-112">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="6ef86-113">覆寫基底方法必須是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="6ef86-113">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="6ef86-114">`override` 宣告不能變更 `virtual` 方法的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="6ef86-114">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="6ef86-115">`override` 方法和 `virtual` 方法都必須具有相同的[存取層級修飾詞](access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="6ef86-115">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="6ef86-116">您不能使用 `new`、`static` 或 `virtual` 修飾詞來修改 `override` 方法。</span><span class="sxs-lookup"><span data-stu-id="6ef86-116">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="6ef86-117">覆寫屬性宣告必須指定與繼承的屬性完全相同的存取修飾詞、型別和名稱。</span><span class="sxs-lookup"><span data-stu-id="6ef86-117">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property.</span></span> <span data-ttu-id="6ef86-118">從 c # 9.0 開始，唯讀的覆寫屬性支援協變數傳回型別。</span><span class="sxs-lookup"><span data-stu-id="6ef86-118">Beginning with C# 9.0, read-only overriding properties support covariant return types.</span></span> <span data-ttu-id="6ef86-119">覆寫的屬性必須是 `virtual` 、 `abstract` 或 `override` 。</span><span class="sxs-lookup"><span data-stu-id="6ef86-119">The overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="6ef86-120">如需如何使用關鍵字的詳細資訊 `override` ，請參閱使用 [Override 和 new 關鍵字進行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ，以及 [瞭解使用 override 和 new 關鍵字](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)的時機。</span><span class="sxs-lookup"><span data-stu-id="6ef86-120">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span> <span data-ttu-id="6ef86-121">如需繼承的資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="6ef86-121">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ef86-122">範例</span><span class="sxs-lookup"><span data-stu-id="6ef86-122">Example</span></span>

<span data-ttu-id="6ef86-123">本例會定義名為 `Employee` 的基底類別，以及名為 `SalesEmployee` 的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="6ef86-123">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="6ef86-124">`SalesEmployee` 類別包含額外的欄位 `salesbonus`，並會覆寫方法 `CalculatePay` 以將其納入考量。</span><span class="sxs-lookup"><span data-stu-id="6ef86-124">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="6ef86-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6ef86-125">C# language specification</span></span>

<span data-ttu-id="6ef86-126">如需詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的覆[寫方法](~/_csharplang/spec/classes.md#override-methods)一節。</span><span class="sxs-lookup"><span data-stu-id="6ef86-126">For more information, see the [Override methods](~/_csharplang/spec/classes.md#override-methods) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="6ef86-127">如需有關協變數傳回類型的詳細資訊，請參閱 [功能提案注意事項](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)。</span><span class="sxs-lookup"><span data-stu-id="6ef86-127">For more information about covariant return types, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ef86-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ef86-128">See also</span></span>

- [<span data-ttu-id="6ef86-129">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="6ef86-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6ef86-130">繼承</span><span class="sxs-lookup"><span data-stu-id="6ef86-130">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="6ef86-131">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="6ef86-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="6ef86-132">修飾詞</span><span class="sxs-lookup"><span data-stu-id="6ef86-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="6ef86-133">抽象</span><span class="sxs-lookup"><span data-stu-id="6ef86-133">abstract</span></span>](abstract.md)
- [<span data-ttu-id="6ef86-134">virtual</span><span class="sxs-lookup"><span data-stu-id="6ef86-134">virtual</span></span>](virtual.md)
- [<span data-ttu-id="6ef86-135">新的 (修飾詞) </span><span class="sxs-lookup"><span data-stu-id="6ef86-135">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="6ef86-136">多型</span><span class="sxs-lookup"><span data-stu-id="6ef86-136">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
