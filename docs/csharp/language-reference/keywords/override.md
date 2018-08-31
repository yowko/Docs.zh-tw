---
title: override (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: c0fdb777c4f5a64dbc92f6afe78cdb714585efe0
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752027"
---
# <a name="override-c-reference"></a><span data-ttu-id="52603-102">override (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="52603-102">override (C# Reference)</span></span>
<span data-ttu-id="52603-103">需要 `override` 修飾詞才能夠擴充或修改繼承方法、屬性、索引子或事件的抽象或虛擬實作。</span><span class="sxs-lookup"><span data-stu-id="52603-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52603-104">範例</span><span class="sxs-lookup"><span data-stu-id="52603-104">Example</span></span>  
 <span data-ttu-id="52603-105">在本例中，`Square` 類別必須提供 `Area` 的覆寫實作，因為 `Area` 繼承自抽象的 `ShapesClass`：</span><span class="sxs-lookup"><span data-stu-id="52603-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="52603-106">`override` 方法提供繼承自基底類別的成員新實作。</span><span class="sxs-lookup"><span data-stu-id="52603-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="52603-107">`override` 宣告覆寫的方法稱之為覆寫基底方法。</span><span class="sxs-lookup"><span data-stu-id="52603-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="52603-108">覆寫基底方法必須和 `override` 方法有相同的簽章。</span><span class="sxs-lookup"><span data-stu-id="52603-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="52603-109">如需繼承的資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="52603-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="52603-110">您無法覆寫非虛擬或靜態方法。</span><span class="sxs-lookup"><span data-stu-id="52603-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="52603-111">覆寫基底方法必須是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="52603-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="52603-112">`override` 宣告不能變更 `virtual` 方法的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="52603-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="52603-113">`override` 方法和 `virtual` 方法都必須具有相同的[存取層級修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="52603-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="52603-114">您不能使用 `new`、`static` 或 `virtual` 修飾詞來修改 `override` 方法。</span><span class="sxs-lookup"><span data-stu-id="52603-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="52603-115">要覆寫的屬性宣告必須指定和繼承屬性完全相同的存取修飾詞、型別和名稱，而覆寫的屬性必須是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="52603-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="52603-116">如需如何使用 `override` 關鍵字的詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)和[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="52603-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52603-117">範例</span><span class="sxs-lookup"><span data-stu-id="52603-117">Example</span></span>  
 <span data-ttu-id="52603-118">本例會定義名為 `Employee` 的基底類別，以及名為 `SalesEmployee` 的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="52603-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="52603-119">`SalesEmployee` 類別包含額外的欄位 `salesbonus`，並會覆寫方法 `CalculatePay` 以將其納入考量。</span><span class="sxs-lookup"><span data-stu-id="52603-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="52603-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="52603-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="52603-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="52603-121">See Also</span></span>  
 [<span data-ttu-id="52603-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="52603-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="52603-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="52603-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="52603-124">繼承</span><span class="sxs-lookup"><span data-stu-id="52603-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="52603-125">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="52603-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="52603-126">修飾詞</span><span class="sxs-lookup"><span data-stu-id="52603-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="52603-127">abstract</span><span class="sxs-lookup"><span data-stu-id="52603-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="52603-128">virtual</span><span class="sxs-lookup"><span data-stu-id="52603-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="52603-129">new</span><span class="sxs-lookup"><span data-stu-id="52603-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="52603-130">多型</span><span class="sxs-lookup"><span data-stu-id="52603-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
