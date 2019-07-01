---
title: 多型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: a7cd450fbc2e0a5acd32675ab2c6b46dc2c92757
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398373"
---
# <a name="polymorphism-c-programming-guide"></a><span data-ttu-id="56868-102">多型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="56868-102">Polymorphism (C# Programming Guide)</span></span>
<span data-ttu-id="56868-103">多型通常是指物件導向程式設計的第三個重要部分，其重要性僅次於封裝和繼承。</span><span class="sxs-lookup"><span data-stu-id="56868-103">Polymorphism is often referred to as the third pillar of object-oriented programming, after encapsulation and inheritance.</span></span> <span data-ttu-id="56868-104">多型在希臘文中表示「多種形狀」，可分成下列兩方面：</span><span class="sxs-lookup"><span data-stu-id="56868-104">Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:</span></span>  
  
- <span data-ttu-id="56868-105">在執行階段，衍生類別物件可視為方法參數和集合或陣列等位置中的基底類別物件。</span><span class="sxs-lookup"><span data-stu-id="56868-105">At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays.</span></span> <span data-ttu-id="56868-106">發生此情況時，物件的宣告類型與其執行階段類型將不再相同。</span><span class="sxs-lookup"><span data-stu-id="56868-106">When this occurs, the object's declared type is no longer identical to its run-time type.</span></span>  
  
- <span data-ttu-id="56868-107">基底類別可以定義和實作 [virtual](../../../csharp/language-reference/keywords/virtual.md)「方法」  ，而衍生類別可以[覆寫](../../../csharp/language-reference/keywords/override.md)這些方法，換句話說，衍生類別會提供自己的定義和實作。</span><span class="sxs-lookup"><span data-stu-id="56868-107">Base classes may define and implement [virtual](../../../csharp/language-reference/keywords/virtual.md) *methods*, and derived classes can [override](../../../csharp/language-reference/keywords/override.md) them, which means they provide their own definition and implementation.</span></span> <span data-ttu-id="56868-108">在執行階段，當用戶端程式碼呼叫方法時，CLR 會查詢物件的執行階段類型，然後叫用虛擬方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="56868-108">At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method.</span></span> <span data-ttu-id="56868-109">因此，在您的原始程式碼中，您可以在基底類別上呼叫方法，然後執行衍生類別版本的方法。</span><span class="sxs-lookup"><span data-stu-id="56868-109">Thus in your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.</span></span>  
  
 <span data-ttu-id="56868-110">虛擬方法可讓您以一致的方式來使用相關物件群組。</span><span class="sxs-lookup"><span data-stu-id="56868-110">Virtual methods enable you to work with groups of related objects in a uniform way.</span></span> <span data-ttu-id="56868-111">例如，假設您有一個繪圖應用程式，可讓使用者在繪圖介面上建立各種圖形。</span><span class="sxs-lookup"><span data-stu-id="56868-111">For example, suppose you have a drawing application that enables a user to create various kinds of shapes on a drawing surface.</span></span> <span data-ttu-id="56868-112">您不知道使用者將在編譯時期建立哪一種圖形。</span><span class="sxs-lookup"><span data-stu-id="56868-112">You do not know at compile time which specific types of shapes the user will create.</span></span> <span data-ttu-id="56868-113">但是，應用程式必須追蹤所建立的所有不同圖形類型，並且必須根據使用者滑鼠動作來更新圖形。</span><span class="sxs-lookup"><span data-stu-id="56868-113">However, the application has to keep track of all the various types of shapes that are created, and it has to update them in response to user mouse actions.</span></span> <span data-ttu-id="56868-114">您可以使用多型，分兩個基本步驟來解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="56868-114">You can use polymorphism to solve this problem in two basic steps:</span></span>  
  
1. <span data-ttu-id="56868-115">建立類別階層架構，其中每個特定圖形類別都是衍生自一個通用基底類別。</span><span class="sxs-lookup"><span data-stu-id="56868-115">Create a class hierarchy in which each specific shape class derives from a common base class.</span></span>  
  
2. <span data-ttu-id="56868-116">使用虛擬方法，透過對基底類別方法發出單一呼叫，在任何衍生類別上叫用適當的方法。</span><span class="sxs-lookup"><span data-stu-id="56868-116">Use a virtual method to invoke the appropriate method on any derived class through a single call to the base class method.</span></span>  
  
 <span data-ttu-id="56868-117">首先，建立稱為 `Shape` 的基底類別，以及 `Rectangle`、`Circle` 和 `Triangle` 等衍生類別。</span><span class="sxs-lookup"><span data-stu-id="56868-117">First, create a base class called `Shape`, and derived classes such as `Rectangle`, `Circle`, and `Triangle`.</span></span> <span data-ttu-id="56868-118">將稱為 `Shape` 的虛擬方法提供給 `Draw` 類別，然後在每個衍生類別中覆寫此方法，以繪製該類別代表的特定圖形。</span><span class="sxs-lookup"><span data-stu-id="56868-118">Give the `Shape` class a virtual method called `Draw`, and override it in each derived class to draw the particular shape that the class represents.</span></span> <span data-ttu-id="56868-119">建立 `List<Shape>` 物件並加入 Circle、Triangle 和 Rectangle。</span><span class="sxs-lookup"><span data-stu-id="56868-119">Create a `List<Shape>` object and add a Circle, Triangle and Rectangle to it.</span></span> <span data-ttu-id="56868-120">若要更新繪圖介面，請使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 迴圈逐一查看清單，並在清單中的每個 `Shape` 物件上呼叫 `Draw` 方法。</span><span class="sxs-lookup"><span data-stu-id="56868-120">To update the drawing surface, use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loop to iterate through the list and call the `Draw` method on each `Shape` object in the list.</span></span> <span data-ttu-id="56868-121">即使清單中的每個物件都有 `Shape` 的宣告類型，會叫用的是執行階段類型 (每個衍生類別中之方法的覆寫版本)。</span><span class="sxs-lookup"><span data-stu-id="56868-121">Even though each object in the list has a declared type of `Shape`, it is the run-time type (the overridden version of the method in each derived class) that will be invoked.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#50)]  
  
 <span data-ttu-id="56868-122">在 C# 中，所有類型都是多型類型，因為所有類型 (包括使用者定義的類型) 都是繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="56868-122">In C#, every type is polymorphic because all types, including user-defined types, inherit from <xref:System.Object>.</span></span>  
  
## <a name="polymorphism-overview"></a><span data-ttu-id="56868-123">多型概觀</span><span class="sxs-lookup"><span data-stu-id="56868-123">Polymorphism Overview</span></span>  
  
### <a name="virtual-members"></a><span data-ttu-id="56868-124">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="56868-124">Virtual Members</span></span>  
 <span data-ttu-id="56868-125">當衍生類別從基底類別繼承時，會取得基底類別的所有方法、欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="56868-125">When a derived class inherits from a base class, it gains all the methods, fields, properties and events of the base class.</span></span> <span data-ttu-id="56868-126">衍生類別的設計工具可選擇是否要</span><span class="sxs-lookup"><span data-stu-id="56868-126">The designer of the derived class can choose whether to</span></span>  
  
- <span data-ttu-id="56868-127">覆寫在基底類別中的虛擬成員</span><span class="sxs-lookup"><span data-stu-id="56868-127">override virtual members in the base class,</span></span>  
  
- <span data-ttu-id="56868-128">繼承最近的基底類別方法，而不加以覆寫</span><span class="sxs-lookup"><span data-stu-id="56868-128">inherit the closest base class method without overriding it</span></span>  
  
- <span data-ttu-id="56868-129">定義隱藏基底類別實作的成員之新的非虛擬實作</span><span class="sxs-lookup"><span data-stu-id="56868-129">define new non-virtual implementation of those members that hide the base class implementations</span></span>  
  
 <span data-ttu-id="56868-130">只有在基底類別成員宣告為 [virtual](../../../csharp/language-reference/keywords/virtual.md) 或 [abstract](../../../csharp/language-reference/keywords/abstract.md) 時，衍生類別才能覆寫基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="56868-130">A derived class can override a base class member only if the base class member is declared as [virtual](../../../csharp/language-reference/keywords/virtual.md) or [abstract](../../../csharp/language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="56868-131">衍生成員必須使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字明確指出方法預定會參與虛擬引動過程。</span><span class="sxs-lookup"><span data-stu-id="56868-131">The derived member must use the [override](../../../csharp/language-reference/keywords/override.md) keyword to explicitly indicate that the method is intended to participate in virtual invocation.</span></span> <span data-ttu-id="56868-132">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="56868-132">The following code provides an example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#20)]  
  
 <span data-ttu-id="56868-133">欄位不可為虛擬，只有方法、屬性、事件和索引子可以是虛擬。</span><span class="sxs-lookup"><span data-stu-id="56868-133">Fields cannot be virtual; only methods, properties, events and indexers can be virtual.</span></span> <span data-ttu-id="56868-134">當衍生類別覆寫虛擬成員時，即使將該類別的執行個體當做基底類別的執行個體來存取，也會呼叫該成員。</span><span class="sxs-lookup"><span data-stu-id="56868-134">When a derived class overrides a virtual member, that member is called even when an instance of that class is being accessed as an instance of the base class.</span></span> <span data-ttu-id="56868-135">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="56868-135">The following code provides an example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#21)]  
  
 <span data-ttu-id="56868-136">虛擬方法和屬性可讓衍生類別不需要使用方法的基底類別實作，即可擴充基底類別。</span><span class="sxs-lookup"><span data-stu-id="56868-136">Virtual methods and properties enable derived classes to extend a base class without needing to use the base class implementation of a method.</span></span> <span data-ttu-id="56868-137">如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="56868-137">For more information, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md).</span></span> <span data-ttu-id="56868-138">介面是用來定義將其實作保留給衍生類別之一個方法或一組方法的另一種做法。</span><span class="sxs-lookup"><span data-stu-id="56868-138">An interface provides another way to define a method or set of methods whose implementation is left to derived classes.</span></span> <span data-ttu-id="56868-139">如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="56868-139">For more information, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
### <a name="hiding-base-class-members-with-new-members"></a><span data-ttu-id="56868-140">使用新成員隱藏基底類別成員</span><span class="sxs-lookup"><span data-stu-id="56868-140">Hiding Base Class Members with New Members</span></span>  
 <span data-ttu-id="56868-141">如果您想讓衍生成員使用與基底類別中成員相同的名稱，但不想讓該成員參與虛擬引動過程，則可以使用 [new](../../../csharp/language-reference/keywords/new-modifier.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="56868-141">If you want your derived member to have the same name as a member in a base class, but you do not want it to participate in virtual invocation, you can use the [new](../../../csharp/language-reference/keywords/new-modifier.md) keyword.</span></span> <span data-ttu-id="56868-142">`new` 關鍵字會放置在要取代之類別成員的傳回類型前面。</span><span class="sxs-lookup"><span data-stu-id="56868-142">The `new` keyword is put before the return type of a class member that is being replaced.</span></span> <span data-ttu-id="56868-143">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="56868-143">The following code provides an example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#18)]  
  
 <span data-ttu-id="56868-144">您仍然可以透過將衍生類別執行個體轉換成基底類別執行個體，從用戶端程式碼存取隱藏的基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="56868-144">Hidden base class members can still be accessed from client code by casting the instance of the derived class to an instance of the base class.</span></span> <span data-ttu-id="56868-145">例如：</span><span class="sxs-lookup"><span data-stu-id="56868-145">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#19)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a><span data-ttu-id="56868-146">防止衍生類別覆寫虛擬成員</span><span class="sxs-lookup"><span data-stu-id="56868-146">Preventing Derived Classes from Overriding Virtual Members</span></span>  
 <span data-ttu-id="56868-147">虛擬成員會無限期保持為虛擬，而不論在虛擬成員與原本宣告的類別之間已宣告多少類別。</span><span class="sxs-lookup"><span data-stu-id="56868-147">Virtual members remain virtual indefinitely, regardless of how many classes have been declared between the virtual member and the class that originally declared it.</span></span> <span data-ttu-id="56868-148">如果類別 A 宣告一個虛擬成員，類別 B 衍生自 A，而類別 C 又衍生自 B，則類別 C 會繼承虛擬成員，且不論類別 B 是否宣告該成員的覆寫，類別 C 都可以選擇覆寫該成員。</span><span class="sxs-lookup"><span data-stu-id="56868-148">If class A declares a virtual member, and class B derives from A, and class C derives from B, class C inherits the virtual member, and has the option to override it, regardless of whether class B declared an override for that member.</span></span> <span data-ttu-id="56868-149">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="56868-149">The following code provides an example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#22)]  
  
 <span data-ttu-id="56868-150">衍生類別可以透過將覆寫宣告為 [sealed](../../../csharp/language-reference/keywords/sealed.md)，來停止虛擬繼承。</span><span class="sxs-lookup"><span data-stu-id="56868-150">A derived class can stop virtual inheritance by declaring an override as [sealed](../../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="56868-151">若要執行這項操作，您必須在類別成員宣告中的 `sealed` 關鍵字前面放置 `override` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="56868-151">This requires putting the `sealed` keyword before the `override` keyword in the class member declaration.</span></span> <span data-ttu-id="56868-152">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="56868-152">The following code provides an example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#24)]  
  
 <span data-ttu-id="56868-153">在上述範例中，`DoWork` 方法對衍生自 C 的任何類別不再是虛擬。對 C 執行個體而言，它仍然是虛擬，即使它們轉換成類型 B 或類型 A 也是一樣。使用 `new` 關鍵字，可以將密封方法取代為衍生類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="56868-153">In the previous example, the method `DoWork` is no longer virtual to any class derived from C. It is still virtual for instances of C, even if they are cast to type B or type A. Sealed methods can be replaced by derived classes by using the `new` keyword, as the following example shows:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#25)]  
  
 <span data-ttu-id="56868-154">在這個範例中，如果使用類型 D 的變數在 D 上呼叫 `DoWork`，則會呼叫新的 `DoWork`。</span><span class="sxs-lookup"><span data-stu-id="56868-154">In this case, if `DoWork` is called on D using a variable of type D, the new `DoWork` is called.</span></span> <span data-ttu-id="56868-155">如果使用類型 C、B 或 A 的變數來存取 D 的執行個體，對 `DoWork` 的呼叫會遵循虛擬繼承的原則，並將這些呼叫路由傳送至類別 C 上的 `DoWork` 實作。</span><span class="sxs-lookup"><span data-stu-id="56868-155">If a variable of type C, B, or A is used to access an instance of D, a call to `DoWork` will follow the rules of virtual inheritance, routing those calls to the implementation of `DoWork` on class C.</span></span>  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a><span data-ttu-id="56868-156">從衍生類別存取基底類別虛擬成員</span><span class="sxs-lookup"><span data-stu-id="56868-156">Accessing Base Class Virtual Members from Derived Classes</span></span>  
 <span data-ttu-id="56868-157">已取代或覆寫方法或屬性的衍生類別，仍可使用 `base` 關鍵字存取基底類別上的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="56868-157">A derived class that has replaced or overridden a method or property can still access the method or property on the base class using the `base` keyword.</span></span> <span data-ttu-id="56868-158">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="56868-158">The following code provides an example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#26)]  
  
 <span data-ttu-id="56868-159">如需詳細資訊，請參閱 [base](../../../csharp/language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="56868-159">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56868-160">建議虛擬成員使用 `base`，在其所擁有的實作中呼叫其基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="56868-160">It is recommended that virtual members use `base` to call the base class implementation of that member in their own implementation.</span></span> <span data-ttu-id="56868-161">允許發生基底類別行為，可讓衍生類別集中實作衍生類別的特定行為。</span><span class="sxs-lookup"><span data-stu-id="56868-161">Letting the base class behavior occur enables the derived class to concentrate on implementing behavior specific to the derived class.</span></span> <span data-ttu-id="56868-162">如果不呼叫基底類別實作，則衍生類別可自行決定是否要讓其行為與基底類別的行為相容。</span><span class="sxs-lookup"><span data-stu-id="56868-162">If the base class implementation is not called, it is up to the derived class to make their behavior compatible with the behavior of the base class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56868-163">本節內容</span><span class="sxs-lookup"><span data-stu-id="56868-163">In This Section</span></span>  
  
- [<span data-ttu-id="56868-164">使用 Override 和 New 關鍵字進行版本控制</span><span class="sxs-lookup"><span data-stu-id="56868-164">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
- [<span data-ttu-id="56868-165">了解使用 Override 和 New 關鍵字的時機</span><span class="sxs-lookup"><span data-stu-id="56868-165">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
- [<span data-ttu-id="56868-166">如何：覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="56868-166">How to: Override the ToString Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="56868-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56868-167">See also</span></span>

- [<span data-ttu-id="56868-168">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="56868-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="56868-169">繼承</span><span class="sxs-lookup"><span data-stu-id="56868-169">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="56868-170">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="56868-170">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="56868-171">方法</span><span class="sxs-lookup"><span data-stu-id="56868-171">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="56868-172">事件</span><span class="sxs-lookup"><span data-stu-id="56868-172">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="56868-173">屬性</span><span class="sxs-lookup"><span data-stu-id="56868-173">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="56868-174">索引子</span><span class="sxs-lookup"><span data-stu-id="56868-174">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="56868-175">型別</span><span class="sxs-lookup"><span data-stu-id="56868-175">Types</span></span>](../../../csharp/programming-guide/types/index.md)
