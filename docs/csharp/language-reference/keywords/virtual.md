---
title: "virtual (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
dev_langs:
- CSharp
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 24ca77a0a645a17c0223437e73539bc04ba80f23
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="virtual-c-reference"></a><span data-ttu-id="eaa6b-102">virtual (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="eaa6b-102">virtual (C# Reference)</span></span>
<span data-ttu-id="eaa6b-103">`virtual` 關鍵字可用來修改方法、屬性、索引子或事件宣告，並可在衍生類別中受到覆寫。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="eaa6b-104">例如，繼承這個方法的任何類別均可將其覆寫：</span><span class="sxs-lookup"><span data-stu-id="eaa6b-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="eaa6b-105">衍生類別中的[覆寫成員](../../../csharp/language-reference/keywords/override.md)可以變更虛擬成員的實作。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="eaa6b-106">如需如何使用 `virtual` 關鍵字的詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)以及[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaa6b-107">備註</span><span class="sxs-lookup"><span data-stu-id="eaa6b-107">Remarks</span></span>  
 <span data-ttu-id="eaa6b-108">叫用虛擬方法時，系統會檢查覆寫成員的物件執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="eaa6b-109">系統會呼叫最多衍生類別中的覆寫成員，且該成員可能是原始的成員 (若沒有任何衍生的類別已覆寫該成員的話)。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="eaa6b-110">此方法預設為非虛擬的方法。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="eaa6b-111">您無法覆寫非虛擬的方法。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="eaa6b-112">您不能搭配使用 `virtual` 修飾詞和 `static`、`abstract, private` 或 `override` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-112">You cannot use the `virtual` modifier with the `static`, `abstract, private`, or `override` modifiers.</span></span> <span data-ttu-id="eaa6b-113">下列範例說明虛擬屬性：</span><span class="sxs-lookup"><span data-stu-id="eaa6b-113">The following example shows a virtual property:</span></span>  
  
 <span data-ttu-id="eaa6b-114">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="eaa6b-114">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]</span></span>  
  
 <span data-ttu-id="eaa6b-115">除了宣告和引動過程語法的差異之外，虛擬屬性的行為類似抽象方法。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-115">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="eaa6b-116">在靜態屬性上使用 `virtual` 修飾詞是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-116">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="eaa6b-117">您可以納入使用 `override` 修飾詞的屬性宣告，以覆寫衍生類別中的虛擬繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-117">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa6b-118">範例</span><span class="sxs-lookup"><span data-stu-id="eaa6b-118">Example</span></span>  
 <span data-ttu-id="eaa6b-119">在此範例中，`Shape` 類別包含 `x` 和 `y` 這兩個座標，以及 `Area()` 虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-119">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="eaa6b-120">`Circle`、`Cylinder` 和 `Sphere` 這類不同圖形類別會繼承 `Shape` 類別，而系統會進行每一個圖形的介面區計算。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-120">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="eaa6b-121">每個衍生類別有其各自的 `Area()` 覆寫實作。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-121">Each derived class has it own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="eaa6b-122">請注意，`Circle`、`Sphere` 和 `Cylinder` 繼承類別都會使用建構函式來初始化基底類別，如下列宣告所示。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-122">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="eaa6b-123">下列程式會叫用適當的 `Area()` 方法實作，根據與方法相關聯的物件，計算並顯示每一個圖形的適當區域。</span><span class="sxs-lookup"><span data-stu-id="eaa6b-123">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 <span data-ttu-id="eaa6b-124">[!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="eaa6b-124">[!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="eaa6b-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="eaa6b-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eaa6b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaa6b-126">See Also</span></span>  
 <span data-ttu-id="eaa6b-127">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="eaa6b-128">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="eaa6b-129">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-129">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="eaa6b-130">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="eaa6b-131">[多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-131">[Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span></span>  
 <span data-ttu-id="eaa6b-132">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-132">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span></span>  
 <span data-ttu-id="eaa6b-133">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="eaa6b-133">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="eaa6b-134">new</span><span class="sxs-lookup"><span data-stu-id="eaa6b-134">new</span></span>](../../../csharp/language-reference/keywords/new.md)

