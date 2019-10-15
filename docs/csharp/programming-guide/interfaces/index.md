---
title: 介面 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: a2cc7cb1b6da860a2c27bc8d2fe74e0ffde5f5e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053270"
---
# <a name="interfaces-c-programming-guide"></a><span data-ttu-id="e31a0-102">介面 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e31a0-102">Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="e31a0-103">介面包含[類別](../../language-reference/keywords/class.md)或 [struct](../../language-reference/keywords/struct.md) 可實作的一組相關功能定義。</span><span class="sxs-lookup"><span data-stu-id="e31a0-103">An interface contains definitions for a group of related functionalities that a [class](../../language-reference/keywords/class.md) or a [struct](../../language-reference/keywords/struct.md) can implement.</span></span>
  
<span data-ttu-id="e31a0-104">例如，您可以藉由使用介面，在類別中包含多個來源的行為。</span><span class="sxs-lookup"><span data-stu-id="e31a0-104">By using interfaces, you can, for example, include behavior from multiple sources in a class.</span></span> <span data-ttu-id="e31a0-105">這項功能在 C# 中是很重要的，因為語言不支援類別的多重繼承。</span><span class="sxs-lookup"><span data-stu-id="e31a0-105">That capability is important in C# because the language doesn't support multiple inheritance of classes.</span></span> <span data-ttu-id="e31a0-106">此外，如果您要模擬結構繼承，則必須使用介面，因為它們實際上無法繼承自另一個結構或類別。</span><span class="sxs-lookup"><span data-stu-id="e31a0-106">In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.</span></span>  
  
<span data-ttu-id="e31a0-107">您會使用 [interface](../../language-reference/keywords/interface.md) 關鍵字來定義介面，</span><span class="sxs-lookup"><span data-stu-id="e31a0-107">You define an interface by using the [interface](../../language-reference/keywords/interface.md) keyword.</span></span> <span data-ttu-id="e31a0-108">如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e31a0-108">as the following example shows.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

<span data-ttu-id="e31a0-109">結構的名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="e31a0-109">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="e31a0-110">依慣例，介面名稱的開頭是大寫的|capital `I`。</span><span class="sxs-lookup"><span data-stu-id="e31a0-110">By convention, interface names begin with a capital `I`.</span></span>

<span data-ttu-id="e31a0-111">任何實作 <xref:System.IEquatable%601> 介面的類別或結構，必須包含 <xref:System.IEquatable%601.Equals%2A> 方法的定義，該方法符合介面指定的簽章。</span><span class="sxs-lookup"><span data-stu-id="e31a0-111">Any class or struct that implements the <xref:System.IEquatable%601> interface must contain a definition for an <xref:System.IEquatable%601.Equals%2A> method that matches the signature that the interface specifies.</span></span> <span data-ttu-id="e31a0-112">如此一來，您可以倚賴實作 `IEquatable<T>` 的類別，以包含 `Equals` 方法，類別的執行個體可以使用該方法判斷它是否等於相同類別的另一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="e31a0-112">As a result, you can count on a class that implements `IEquatable<T>` to contain an `Equals` method with which an instance of the class can determine whether it's equal to another instance of the same class.</span></span>  
  
<span data-ttu-id="e31a0-113">`IEquatable<T>` 的定義不提供 `Equals` 的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-113">The definition of `IEquatable<T>` doesn’t provide an implementation for `Equals`.</span></span> <span data-ttu-id="e31a0-114">類別或結構可以執行多個介面，但類別只能繼承自單一類別。</span><span class="sxs-lookup"><span data-stu-id="e31a0-114">A class or struct can implement multiple interfaces, but a class can only inherit from a single class.</span></span>
  
<span data-ttu-id="e31a0-115">如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="e31a0-115">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="e31a0-116">介面可以包含方法、屬性、事件、索引子，或以上四個成員類型的組合。</span><span class="sxs-lookup"><span data-stu-id="e31a0-116">Interfaces can contain methods, properties, events, indexers, or any combination of those four member types.</span></span> <span data-ttu-id="e31a0-117">如需範例的連結，請參閱[相關章節](./index.md#BKMK_RelatedSections)。</span><span class="sxs-lookup"><span data-stu-id="e31a0-117">For links to examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span> <span data-ttu-id="e31a0-118">介面不能包含常數、欄位、運算子、執行個體建構函式、完成項或類型。</span><span class="sxs-lookup"><span data-stu-id="e31a0-118">An interface can't contain constants, fields, operators, instance constructors, finalizers, or types.</span></span> <span data-ttu-id="e31a0-119">介面成員會自動變成公用，且它們不能包含任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e31a0-119">Interface members are automatically public, and they can't include any access modifiers.</span></span> <span data-ttu-id="e31a0-120">成員也不能是 [static](../../language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="e31a0-120">Members also can't be [static](../../language-reference/keywords/static.md).</span></span>  
  
<span data-ttu-id="e31a0-121">若要實作介面成員，實作類別的對應成員必須是公用、非靜態，且具有與介面成員相同的名稱和簽章。</span><span class="sxs-lookup"><span data-stu-id="e31a0-121">To implement an interface member, the corresponding member of the implementing class must be public, non-static, and have the same name and signature as the interface member.</span></span>  
  
<span data-ttu-id="e31a0-122">當類別或結構實作介面時，類別或結構必須提供介面定義之所有成員的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-122">When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface defines.</span></span> <span data-ttu-id="e31a0-123">介面本身不提供功能讓類別或結構可以如同繼承基底類別功能一般繼承。</span><span class="sxs-lookup"><span data-stu-id="e31a0-123">The interface itself provides no functionality that a class or struct can inherit in the way that it can inherit base class functionality.</span></span> <span data-ttu-id="e31a0-124">不過，如果基底類別實作介面，則衍生自基底類別的任何類別都會繼承該實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-124">However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.</span></span>  
  
<span data-ttu-id="e31a0-125">下列範例會示範 <xref:System.IEquatable%601> 介面的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-125">The following example shows an implementation of the <xref:System.IEquatable%601> interface.</span></span> <span data-ttu-id="e31a0-126">實作類別 `Car` 必須提供 <xref:System.IEquatable%601.Equals%2A> 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-126">The implementing class, `Car`, must provide an implementation of the <xref:System.IEquatable%601.Equals%2A> method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
<span data-ttu-id="e31a0-127">類別的屬性與索引子可以針對介面中定義的屬性或索引子定義額外的存取子。</span><span class="sxs-lookup"><span data-stu-id="e31a0-127">Properties and indexers of a class can define extra accessors for a property or indexer that's defined in an interface.</span></span> <span data-ttu-id="e31a0-128">例如，介面可能會宣告具有 [get](../../language-reference/keywords/get.md) 存取子的屬性。</span><span class="sxs-lookup"><span data-stu-id="e31a0-128">For example, an interface might declare a property that has a [get](../../language-reference/keywords/get.md) accessor.</span></span> <span data-ttu-id="e31a0-129">實作介面的類別可以宣告具有 `get` 和 [set](../../language-reference/keywords/set.md) 存取子的相同屬性。</span><span class="sxs-lookup"><span data-stu-id="e31a0-129">The class that implements the interface can declare the same property with both a `get` and [set](../../language-reference/keywords/set.md) accessor.</span></span> <span data-ttu-id="e31a0-130">不過，如果屬性或索引子使用明確的實作，則存取子必須相符。</span><span class="sxs-lookup"><span data-stu-id="e31a0-130">However, if the property or indexer uses explicit implementation, the accessors must match.</span></span> <span data-ttu-id="e31a0-131">如需明確實作的詳細資訊，請參閱[明確介面實作](explicit-interface-implementation.md)和[介面屬性](../classes-and-structs/interface-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="e31a0-131">For more information about explicit implementation, see [Explicit Interface Implementation](explicit-interface-implementation.md) and [Interface Properties](../classes-and-structs/interface-properties.md).</span></span>  

<span data-ttu-id="e31a0-132">介面可以繼承自其他介面。</span><span class="sxs-lookup"><span data-stu-id="e31a0-132">Interfaces can inherit from other interfaces.</span></span> <span data-ttu-id="e31a0-133">類別可能透過基底類別包含介面多次，繼承或透過其他介面繼承的介面。</span><span class="sxs-lookup"><span data-stu-id="e31a0-133">A class might include an interface multiple times through base classes that it inherits or through interfaces that other interfaces inherit.</span></span> <span data-ttu-id="e31a0-134">不過，類別只能提供介面實作一次，而且只有在類別將介面宣告為類別 (`class ClassName : InterfaceName`) 定義的一部分時。</span><span class="sxs-lookup"><span data-stu-id="e31a0-134">However, the class can provide an implementation of an interface only one time and only if the class declares the interface as part of the definition of the class (`class ClassName : InterfaceName`).</span></span> <span data-ttu-id="e31a0-135">如果因為您繼承實作介面的基底類別而繼承介面，則基底類別會提供介面成員的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-135">If the interface is inherited because you inherited a base class that implements the interface, the base class provides the implementation of the members of the interface.</span></span> <span data-ttu-id="e31a0-136">不過，衍生的類別可以實作任何虛擬介面成員，而不使用繼承的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-136">However, the derived class can reimplement any virtual interface members instead of using the inherited implementation.</span></span>  
  
<span data-ttu-id="e31a0-137">基底類別也可以使用虛擬成員來實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="e31a0-137">A base class can also implement interface members by using virtual members.</span></span> <span data-ttu-id="e31a0-138">在此情況下，衍生的類別可以藉由覆寫虛擬成員來變更介面行為。</span><span class="sxs-lookup"><span data-stu-id="e31a0-138">In that case, a derived class can change the interface behavior by overriding the virtual members.</span></span> <span data-ttu-id="e31a0-139">如需虛擬成員的詳細資訊，請參閱[多型](../classes-and-structs/polymorphism.md)。</span><span class="sxs-lookup"><span data-stu-id="e31a0-139">For more information about virtual members, see [Polymorphism](../classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="interfaces-summary"></a><span data-ttu-id="e31a0-140">介面摘要</span><span class="sxs-lookup"><span data-stu-id="e31a0-140">Interfaces summary</span></span>

<span data-ttu-id="e31a0-141">介面具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e31a0-141">An interface has the following properties:</span></span>  

- <span data-ttu-id="e31a0-142">介面類似只有抽象成員的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="e31a0-142">An interface is like an abstract base class with only abstract members.</span></span> <span data-ttu-id="e31a0-143">任何實作介面的類別或結構必須實作它的所有成員。</span><span class="sxs-lookup"><span data-stu-id="e31a0-143">Any class or struct that implements the interface must implement all its members.</span></span>
- <span data-ttu-id="e31a0-144">介面無法直接具現化。</span><span class="sxs-lookup"><span data-stu-id="e31a0-144">An interface can't be instantiated directly.</span></span> <span data-ttu-id="e31a0-145">其成員是由實作介面的任何類別或結構實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-145">Its members are implemented by any class or struct that implements the interface.</span></span>
- <span data-ttu-id="e31a0-146">介面可以包含事件、索引子、方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="e31a0-146">Interfaces can contain events, indexers, methods, and properties.</span></span>
- <span data-ttu-id="e31a0-147">介面不包含方法的實作。</span><span class="sxs-lookup"><span data-stu-id="e31a0-147">Interfaces contain no implementation of methods.</span></span>
- <span data-ttu-id="e31a0-148">類別或結構可以實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="e31a0-148">A class or struct can implement multiple interfaces.</span></span> <span data-ttu-id="e31a0-149">類別可以繼承基底類別，也會實作一或多個介面。</span><span class="sxs-lookup"><span data-stu-id="e31a0-149">A class can inherit a base class and also implement one or more interfaces.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e31a0-150">本節內容</span><span class="sxs-lookup"><span data-stu-id="e31a0-150">In this section</span></span>

[<span data-ttu-id="e31a0-151">明確介面實作</span><span class="sxs-lookup"><span data-stu-id="e31a0-151">Explicit Interface Implementation</span></span>](explicit-interface-implementation.md)  
 <span data-ttu-id="e31a0-152">說明如何建立介面特定的類別成員。</span><span class="sxs-lookup"><span data-stu-id="e31a0-152">Explains how to create a class member that’s specific to an interface.</span></span>  
  
 [<span data-ttu-id="e31a0-153">如何：明確實作介面成員</span><span class="sxs-lookup"><span data-stu-id="e31a0-153">How to: Explicitly Implement Interface Members</span></span>](how-to-explicitly-implement-interface-members.md)  
 <span data-ttu-id="e31a0-154">提供如何明確實作介面成員的範例。</span><span class="sxs-lookup"><span data-stu-id="e31a0-154">Provides an example of how to explicitly implement members of interfaces.</span></span>  
  
 [<span data-ttu-id="e31a0-155">如何：明確實作兩個介面的成員</span><span class="sxs-lookup"><span data-stu-id="e31a0-155">How to: Explicitly Implement Members of Two Interfaces</span></span>](how-to-explicitly-implement-members-of-two-interfaces.md)  
 <span data-ttu-id="e31a0-156">提供如何透過繼承明確實作介面成員的範例。</span><span class="sxs-lookup"><span data-stu-id="e31a0-156">Provides an example of how to explicitly implement members of interfaces with inheritance.</span></span>  
  
## <a name="BKMK_RelatedSections"></a> <span data-ttu-id="e31a0-157">相關章節</span><span class="sxs-lookup"><span data-stu-id="e31a0-157">Related Sections</span></span>

- [<span data-ttu-id="e31a0-158">介面屬性</span><span class="sxs-lookup"><span data-stu-id="e31a0-158">Interface Properties</span></span>](../classes-and-structs/interface-properties.md)  
- [<span data-ttu-id="e31a0-159">介面中的索引子</span><span class="sxs-lookup"><span data-stu-id="e31a0-159">Indexers in Interfaces</span></span>](../indexers/indexers-in-interfaces.md)  
- [<span data-ttu-id="e31a0-160">如何：實作介面事件</span><span class="sxs-lookup"><span data-stu-id="e31a0-160">How to:  Implement Interface Events</span></span>](../events/how-to-implement-interface-events.md)  
- [<span data-ttu-id="e31a0-161">類別和結構</span><span class="sxs-lookup"><span data-stu-id="e31a0-161">Classes and Structs</span></span>](../classes-and-structs/index.md)  
- [<span data-ttu-id="e31a0-162">繼承</span><span class="sxs-lookup"><span data-stu-id="e31a0-162">Inheritance</span></span>](../classes-and-structs/inheritance.md)  
- [<span data-ttu-id="e31a0-163">方法</span><span class="sxs-lookup"><span data-stu-id="e31a0-163">Methods</span></span>](../classes-and-structs/methods.md)  
- [<span data-ttu-id="e31a0-164">多型</span><span class="sxs-lookup"><span data-stu-id="e31a0-164">Polymorphism</span></span>](../classes-and-structs/polymorphism.md)  
- [<span data-ttu-id="e31a0-165">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="e31a0-165">Abstract and Sealed Classes and Class Members</span></span>](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [<span data-ttu-id="e31a0-166">屬性</span><span class="sxs-lookup"><span data-stu-id="e31a0-166">Properties</span></span>](../classes-and-structs/properties.md)  
- [<span data-ttu-id="e31a0-167">事件</span><span class="sxs-lookup"><span data-stu-id="e31a0-167">Events</span></span>](../events/index.md)  
- [<span data-ttu-id="e31a0-168">索引子</span><span class="sxs-lookup"><span data-stu-id="e31a0-168">Indexers</span></span>](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="e31a0-169">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="e31a0-169">featured book chapter</span></span>

<span data-ttu-id="e31a0-170">[了解 C# 3.0：掌握 C# 3.0 的基本概念](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)中的[介面](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29)</span><span class="sxs-lookup"><span data-stu-id="e31a0-170">[Interfaces](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) in [Learning C# 3.0: Master the Fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)</span></span>

## <a name="see-also"></a><span data-ttu-id="e31a0-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e31a0-171">See also</span></span>

- [<span data-ttu-id="e31a0-172">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e31a0-172">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e31a0-173">繼承</span><span class="sxs-lookup"><span data-stu-id="e31a0-173">Inheritance</span></span>](../classes-and-structs/inheritance.md)
- [<span data-ttu-id="e31a0-174">識別碼名稱</span><span class="sxs-lookup"><span data-stu-id="e31a0-174">Identifier names</span></span>](../inside-a-program/identifier-names.md)
