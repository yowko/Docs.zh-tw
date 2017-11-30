---
title: "new 修飾詞 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28124c2f3ecef01fd4bc43fe7cfc975dd6466506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="5f96c-102">new 修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5f96c-102">new Modifier (C# Reference)</span></span>
<span data-ttu-id="5f96c-103">`new` 關鍵字做為宣告修飾詞使用時，會明確隱藏繼承自基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="5f96c-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="5f96c-104">當您隱藏繼承的成員時，該成員的衍生版本就會取代基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="5f96c-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="5f96c-105">雖然您可以在不使用 `new` 修飾詞的情況下隱藏成員，但是編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="5f96c-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="5f96c-106">如果您使用 `new` 明確隱藏成員，它會隱藏這個警告。</span><span class="sxs-lookup"><span data-stu-id="5f96c-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>  
  
 <span data-ttu-id="5f96c-107">若要隱藏繼承的成員，請在衍生類別中使用相同的成員名稱宣告該成員，並且使用 `new` 關鍵讚加以修飾。</span><span class="sxs-lookup"><span data-stu-id="5f96c-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="5f96c-108">例如: </span><span class="sxs-lookup"><span data-stu-id="5f96c-108">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 <span data-ttu-id="5f96c-109">在這個範例中，`BaseC.Invoke` 是藉由 `DerivedC.Invoke` 隱藏。</span><span class="sxs-lookup"><span data-stu-id="5f96c-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="5f96c-110">`x` 欄位不受影響，因為它不是由類似的名稱所隱藏。</span><span class="sxs-lookup"><span data-stu-id="5f96c-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>  
  
 <span data-ttu-id="5f96c-111">經由繼承隱藏的名稱會採用下列其中一種格式：</span><span class="sxs-lookup"><span data-stu-id="5f96c-111">Name hiding through inheritance takes one of the following forms:</span></span>  
  
-   <span data-ttu-id="5f96c-112">一般而言，在類別或結構中引入的常數、欄位、屬性或類型會隱藏共用其名稱的所有基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="5f96c-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="5f96c-113">不過有一些特殊案例。</span><span class="sxs-lookup"><span data-stu-id="5f96c-113">There are special cases.</span></span>  <span data-ttu-id="5f96c-114">例如，如果您宣告名為 `N` 的新欄位採用不可叫用的類型，而且基底類型將 `N` 宣告為方法，則新欄位不會隱藏引動過程語法中的基底宣告。</span><span class="sxs-lookup"><span data-stu-id="5f96c-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="5f96c-115">請參閱[5.0 C# 語言規格](http://go.microsoft.com/fwlink/?LinkId=199552)如需詳細資訊 （請參閱 < 運算式 > 一節中的 < 成員查詢 > 一節）。</span><span class="sxs-lookup"><span data-stu-id="5f96c-115">See the [C# 5.0 language specification](http://go.microsoft.com/fwlink/?LinkId=199552) for details (see section "Member Lookup" in section "Expressions").</span></span>  
  
-   <span data-ttu-id="5f96c-116">類別或結構中引入的方法會隱藏在基底類別中共用該名稱的屬性、欄位和類型。</span><span class="sxs-lookup"><span data-stu-id="5f96c-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="5f96c-117">它也會隱藏所有具有相同簽章的基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="5f96c-117">It also hides all base class methods that have the same signature.</span></span>  
  
-   <span data-ttu-id="5f96c-118">類別或結構中引入的索引子會隱藏所有具有相同簽章的基底類別索引子。</span><span class="sxs-lookup"><span data-stu-id="5f96c-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>  
  
 <span data-ttu-id="5f96c-119">在相同的成員上同時使用 `new` 和 [override](../../../csharp/language-reference/keywords/override.md) 是不正確的，因為這兩個修飾詞在意義上互斥。</span><span class="sxs-lookup"><span data-stu-id="5f96c-119">It is an error to use both `new` and [override](../../../csharp/language-reference/keywords/override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="5f96c-120">`new` 修飾詞會以相同名稱建立新成員，並使原始成員隱藏。</span><span class="sxs-lookup"><span data-stu-id="5f96c-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="5f96c-121">`override` 修飾詞會擴充繼承成員的實作。</span><span class="sxs-lookup"><span data-stu-id="5f96c-121">The `override` modifier extends the implementation for an inherited member.</span></span>  
  
 <span data-ttu-id="5f96c-122">在未隱藏繼承的成員之宣告中使用 `new` 修飾詞會產生警告。</span><span class="sxs-lookup"><span data-stu-id="5f96c-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f96c-123">範例</span><span class="sxs-lookup"><span data-stu-id="5f96c-123">Example</span></span>  
 <span data-ttu-id="5f96c-124">在這個範例中，基底類別 `BaseC` 以及衍生類別 `DerivedC` 會使用相同的欄位名稱 `x`，而該欄位名稱會隱藏繼承之欄位的值。</span><span class="sxs-lookup"><span data-stu-id="5f96c-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="5f96c-125">範例中將示範 `new` 修飾詞的用法。</span><span class="sxs-lookup"><span data-stu-id="5f96c-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="5f96c-126">另外還會示範如何使用完整限定名稱存取基底類別的隱藏成員。</span><span class="sxs-lookup"><span data-stu-id="5f96c-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="5f96c-127">範例</span><span class="sxs-lookup"><span data-stu-id="5f96c-127">Example</span></span>  
 <span data-ttu-id="5f96c-128">在這個範例中，巢狀類別會隱藏在基底類別中具有相同名稱的類別。</span><span class="sxs-lookup"><span data-stu-id="5f96c-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="5f96c-129">這個範例將示範如何使用 `new` 修飾詞消除警告訊息，以及如何使用完整限定名稱存取隱藏的類別成員。</span><span class="sxs-lookup"><span data-stu-id="5f96c-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 <span data-ttu-id="5f96c-130">如果您移除 `new` 修飾詞，程式仍會進行編譯和執行，但是您會收到下列警告：</span><span class="sxs-lookup"><span data-stu-id="5f96c-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="5f96c-131">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5f96c-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f96c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f96c-132">See Also</span></span>  
 [<span data-ttu-id="5f96c-133">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5f96c-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5f96c-134">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5f96c-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5f96c-135">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f96c-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5f96c-136">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="5f96c-136">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="5f96c-137">修飾詞</span><span class="sxs-lookup"><span data-stu-id="5f96c-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="5f96c-138">使用 Override 和 New 關鍵字進行版本控制</span><span class="sxs-lookup"><span data-stu-id="5f96c-138">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="5f96c-139">了解使用 Override 和 New 關鍵字的時機</span><span class="sxs-lookup"><span data-stu-id="5f96c-139">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
