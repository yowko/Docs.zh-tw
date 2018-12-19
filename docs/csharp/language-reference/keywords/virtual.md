---
title: virtual - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 0a6eb7bfcd598eb54b4b0cc5661d219367da2238
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237385"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="eb964-102">virtual (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="eb964-102">virtual (C# Reference)</span></span>
<span data-ttu-id="eb964-103">`virtual` 關鍵字可用來修改方法、屬性、索引子或事件宣告，並可在衍生類別中受到覆寫。</span><span class="sxs-lookup"><span data-stu-id="eb964-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="eb964-104">例如，繼承這個方法的任何類別均可將其覆寫：</span><span class="sxs-lookup"><span data-stu-id="eb964-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="eb964-105">衍生類別中的[覆寫成員](../../../csharp/language-reference/keywords/override.md)可以變更虛擬成員的實作。</span><span class="sxs-lookup"><span data-stu-id="eb964-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="eb964-106">如需如何使用 `virtual` 關鍵字的詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)以及[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="eb964-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb964-107">備註</span><span class="sxs-lookup"><span data-stu-id="eb964-107">Remarks</span></span>  
 <span data-ttu-id="eb964-108">叫用虛擬方法時，系統會檢查覆寫成員的物件執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="eb964-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="eb964-109">系統會呼叫最多衍生類別中的覆寫成員，且該成員可能是原始的成員 (若沒有任何衍生的類別已覆寫該成員的話)。</span><span class="sxs-lookup"><span data-stu-id="eb964-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="eb964-110">此方法預設為非虛擬的方法。</span><span class="sxs-lookup"><span data-stu-id="eb964-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="eb964-111">您無法覆寫非虛擬的方法。</span><span class="sxs-lookup"><span data-stu-id="eb964-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="eb964-112">您不能搭配使用 `virtual` 修飾詞和 `static`、`abstract`、`private` 或 `override` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="eb964-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="eb964-113">下列範例說明虛擬屬性：</span><span class="sxs-lookup"><span data-stu-id="eb964-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="eb964-114">除了宣告和引動過程語法的差異之外，虛擬屬性的行為類似抽象方法。</span><span class="sxs-lookup"><span data-stu-id="eb964-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="eb964-115">在靜態屬性上使用 `virtual` 修飾詞是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="eb964-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="eb964-116">您可以納入使用 `override` 修飾詞的屬性宣告，以覆寫衍生類別中的虛擬繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="eb964-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb964-117">範例</span><span class="sxs-lookup"><span data-stu-id="eb964-117">Example</span></span>  
 <span data-ttu-id="eb964-118">在此範例中，`Shape` 類別包含 `x` 和 `y` 這兩個座標，以及 `Area()` 虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="eb964-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="eb964-119">`Circle`、`Cylinder` 和 `Sphere` 這類不同圖形類別會繼承 `Shape` 類別，而系統會進行每一個圖形的介面區計算。</span><span class="sxs-lookup"><span data-stu-id="eb964-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="eb964-120">每個衍生類別有其各自的 `Area()` 覆寫實作。</span><span class="sxs-lookup"><span data-stu-id="eb964-120">Each derived class has its own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="eb964-121">請注意，`Circle`、`Sphere` 和 `Cylinder` 繼承類別都會使用建構函式來初始化基底類別，如下列宣告所示。</span><span class="sxs-lookup"><span data-stu-id="eb964-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="eb964-122">下列程式會叫用適當的 `Area()` 方法實作，根據與方法相關聯的物件，計算並顯示每一個圖形的適當區域。</span><span class="sxs-lookup"><span data-stu-id="eb964-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="eb964-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="eb964-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb964-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="eb964-124">See Also</span></span>

- [<span data-ttu-id="eb964-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="eb964-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="eb964-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="eb964-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="eb964-127">修飾詞</span><span class="sxs-lookup"><span data-stu-id="eb964-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="eb964-128">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="eb964-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="eb964-129">多型</span><span class="sxs-lookup"><span data-stu-id="eb964-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
- [<span data-ttu-id="eb964-130">abstract</span><span class="sxs-lookup"><span data-stu-id="eb964-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
- [<span data-ttu-id="eb964-131">override</span><span class="sxs-lookup"><span data-stu-id="eb964-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="eb964-132">new</span><span class="sxs-lookup"><span data-stu-id="eb964-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
