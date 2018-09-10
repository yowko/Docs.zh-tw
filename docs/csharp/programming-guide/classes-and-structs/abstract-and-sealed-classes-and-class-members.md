---
title: 抽象和密封類別以及類別成員 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 0e80357a51bde270d5ed012f16f7b2e821f084c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517338"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="5f13e-102">抽象和密封類別以及類別成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5f13e-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="5f13e-103">[abstract](../../../csharp/language-reference/keywords/abstract.md) 關鍵字可讓您建立類別和[類別](../../../csharp/language-reference/keywords/class.md)成員，這些類別和成員並不完整，因此必須在衍生類別中實作。</span><span class="sxs-lookup"><span data-stu-id="5f13e-103">The [abstract](../../../csharp/language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../../csharp/language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="5f13e-104">[sealed](../../../csharp/language-reference/keywords/sealed.md) 關鍵字可讓您避免繼承類別，或是先前標記為 [virtual](../../../csharp/language-reference/keywords/virtual.md) 的特定類別成員。</span><span class="sxs-lookup"><span data-stu-id="5f13e-104">The [sealed](../../../csharp/language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="5f13e-105">抽象類別和類別成員</span><span class="sxs-lookup"><span data-stu-id="5f13e-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="5f13e-106">在類別定義前面加入 `abstract` 關鍵字，就可以將類別宣告為抽象。</span><span class="sxs-lookup"><span data-stu-id="5f13e-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="5f13e-107">例如: </span><span class="sxs-lookup"><span data-stu-id="5f13e-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 <span data-ttu-id="5f13e-108">抽象類別無法具現化。</span><span class="sxs-lookup"><span data-stu-id="5f13e-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="5f13e-109">抽象類別的用途是提供基底類別的通用定義，可供多個衍生類別共用。</span><span class="sxs-lookup"><span data-stu-id="5f13e-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="5f13e-110">例如，類別庫會定義做為其多個函式的參數使用的抽象類別，並且要求使用該類別庫的程式設計人員建立衍生類別來提供自己的類別實作。</span><span class="sxs-lookup"><span data-stu-id="5f13e-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="5f13e-111">抽象類別也可以定義抽象方法。</span><span class="sxs-lookup"><span data-stu-id="5f13e-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="5f13e-112">只要在方法的傳回類型前面加上關鍵字 `abstract`，就可以達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="5f13e-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="5f13e-113">例如: </span><span class="sxs-lookup"><span data-stu-id="5f13e-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 <span data-ttu-id="5f13e-114">抽象方法沒有任何實作，因此方法定義後面會接著一個分號，而不是一般方法區塊。</span><span class="sxs-lookup"><span data-stu-id="5f13e-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="5f13e-115">抽象類別的衍生類別必須實作所有抽象方法。</span><span class="sxs-lookup"><span data-stu-id="5f13e-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="5f13e-116">當抽象類別從基底類別繼承虛擬方法時，抽象類別可以使用抽象方法覆寫虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="5f13e-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="5f13e-117">例如: </span><span class="sxs-lookup"><span data-stu-id="5f13e-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 <span data-ttu-id="5f13e-118">如果 `virtual` 方法宣告為 `abstract`，則該方法對於繼承自抽象類別的任何類別來說仍為虛擬。</span><span class="sxs-lookup"><span data-stu-id="5f13e-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="5f13e-119">繼承抽象方法的類別無法存取方法的原始實作：在前一個範例中，F 類別的 `DoWork` 無法呼叫 D 類別的 `DoWork`。如此一來，抽象類別可以強制衍生的類別為虛擬方法提供新的方法實作。</span><span class="sxs-lookup"><span data-stu-id="5f13e-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="5f13e-120">密封類別和類別成員</span><span class="sxs-lookup"><span data-stu-id="5f13e-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="5f13e-121">在類別定義前面加入 `sealed` 關鍵字，就可以將類別宣告為 [sealed](../../../csharp/language-reference/keywords/sealed.md)。</span><span class="sxs-lookup"><span data-stu-id="5f13e-121">Classes can be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="5f13e-122">例如: </span><span class="sxs-lookup"><span data-stu-id="5f13e-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 <span data-ttu-id="5f13e-123">密封類別不能當做基底類別使用。</span><span class="sxs-lookup"><span data-stu-id="5f13e-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="5f13e-124">基於這個理由，該類別也不能是抽象類別。</span><span class="sxs-lookup"><span data-stu-id="5f13e-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="5f13e-125">密封類別可以避免衍生。</span><span class="sxs-lookup"><span data-stu-id="5f13e-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="5f13e-126">由於密封類別永遠不能當做基底類別使用，因此某些執行階段最佳化呼叫密封類別成員的速度就能夠稍為加快。</span><span class="sxs-lookup"><span data-stu-id="5f13e-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="5f13e-127">若方法、索引子、屬性或事件位於覆寫基底類別之虛擬成員的衍生類別上，就可以將該成員宣告為密封。</span><span class="sxs-lookup"><span data-stu-id="5f13e-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="5f13e-128">這樣一來，後續任何衍生類別的成員都不再擁有虛擬部分。</span><span class="sxs-lookup"><span data-stu-id="5f13e-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="5f13e-129">只要在類別成員宣告中的 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字前面放置 `sealed` 關鍵字，就可以達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="5f13e-129">This is accomplished by putting the `sealed` keyword before the [override](../../../csharp/language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="5f13e-130">例如: </span><span class="sxs-lookup"><span data-stu-id="5f13e-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5f13e-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="5f13e-131">See Also</span></span>

- [<span data-ttu-id="5f13e-132">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5f13e-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5f13e-133">類別和結構</span><span class="sxs-lookup"><span data-stu-id="5f13e-133">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="5f13e-134">繼承</span><span class="sxs-lookup"><span data-stu-id="5f13e-134">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
- [<span data-ttu-id="5f13e-135">方法</span><span class="sxs-lookup"><span data-stu-id="5f13e-135">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="5f13e-136">欄位</span><span class="sxs-lookup"><span data-stu-id="5f13e-136">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)  
- [<span data-ttu-id="5f13e-137">如何：定義抽象屬性</span><span class="sxs-lookup"><span data-stu-id="5f13e-137">How to: Define Abstract Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
