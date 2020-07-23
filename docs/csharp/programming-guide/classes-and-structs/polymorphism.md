---
title: 多型 - C# 程式設計手冊
description: '深入瞭解多型，這是物件導向程式設計語言（如 c #）中的重要概念，其中描述基底和衍生類別之間的關聯性。'
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 59b5f5d2d5a8f274845607aeca370c316670bd68
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925445"
---
# <a name="polymorphism-c-programming-guide"></a><span data-ttu-id="51265-103">多型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="51265-103">Polymorphism (C# Programming Guide)</span></span>

<span data-ttu-id="51265-104">多型通常是指物件導向程式設計的第三個重要部分，其重要性僅次於封裝和繼承。</span><span class="sxs-lookup"><span data-stu-id="51265-104">Polymorphism is often referred to as the third pillar of object-oriented programming, after encapsulation and inheritance.</span></span> <span data-ttu-id="51265-105">多型在希臘文中表示「多種形狀」，可分成下列兩方面：</span><span class="sxs-lookup"><span data-stu-id="51265-105">Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:</span></span>
  
- <span data-ttu-id="51265-106">在執行階段，衍生類別物件可視為方法參數和集合或陣列等位置中的基底類別物件。</span><span class="sxs-lookup"><span data-stu-id="51265-106">At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays.</span></span> <span data-ttu-id="51265-107">當這個多型發生時，物件的宣告型別就不再與執行時間型別完全相同。</span><span class="sxs-lookup"><span data-stu-id="51265-107">When this polymorphism occurs, the object's declared type is no longer identical to its run-time type.</span></span>
- <span data-ttu-id="51265-108">基底類別可以定義和實作 [virtual「方法」](../../language-reference/keywords/virtual.md) \*\*，而衍生類別可以[覆寫](../../language-reference/keywords/override.md)這些方法，換句話說，衍生類別會提供自己的定義和實作。</span><span class="sxs-lookup"><span data-stu-id="51265-108">Base classes may define and implement [virtual](../../language-reference/keywords/virtual.md) *methods*, and derived classes can [override](../../language-reference/keywords/override.md) them, which means they provide their own definition and implementation.</span></span> <span data-ttu-id="51265-109">在執行階段，當用戶端程式碼呼叫方法時，CLR 會查詢物件的執行階段類型，然後叫用虛擬方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="51265-109">At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method.</span></span> <span data-ttu-id="51265-110">在您的原始程式碼中，您可以呼叫基類上的方法，並使衍生類別的方法版本執行。</span><span class="sxs-lookup"><span data-stu-id="51265-110">In your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.</span></span>

<span data-ttu-id="51265-111">虛擬方法可讓您以一致的方式來使用相關物件群組。</span><span class="sxs-lookup"><span data-stu-id="51265-111">Virtual methods enable you to work with groups of related objects in a uniform way.</span></span> <span data-ttu-id="51265-112">例如，假設您有一個繪圖應用程式，可讓使用者在繪圖介面上建立各種圖形。</span><span class="sxs-lookup"><span data-stu-id="51265-112">For example, suppose you have a drawing application that enables a user to create various kinds of shapes on a drawing surface.</span></span> <span data-ttu-id="51265-113">您不知道使用者將在編譯時期建立哪一種圖形。</span><span class="sxs-lookup"><span data-stu-id="51265-113">You do not know at compile time which specific types of shapes the user will create.</span></span> <span data-ttu-id="51265-114">但是，應用程式必須追蹤所建立的所有不同圖形類型，並且必須根據使用者滑鼠動作來更新圖形。</span><span class="sxs-lookup"><span data-stu-id="51265-114">However, the application has to keep track of all the various types of shapes that are created, and it has to update them in response to user mouse actions.</span></span> <span data-ttu-id="51265-115">您可以使用多型，分兩個基本步驟來解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="51265-115">You can use polymorphism to solve this problem in two basic steps:</span></span>

1. <span data-ttu-id="51265-116">建立類別階層架構，其中每個特定圖形類別都是衍生自一個通用基底類別。</span><span class="sxs-lookup"><span data-stu-id="51265-116">Create a class hierarchy in which each specific shape class derives from a common base class.</span></span>
1. <span data-ttu-id="51265-117">使用虛擬方法，透過對基底類別方法發出單一呼叫，在任何衍生類別上叫用適當的方法。</span><span class="sxs-lookup"><span data-stu-id="51265-117">Use a virtual method to invoke the appropriate method on any derived class through a single call to the base class method.</span></span>

<span data-ttu-id="51265-118">首先，建立稱為 `Shape` 的基底類別，以及 `Rectangle`、`Circle` 和 `Triangle` 等衍生類別。</span><span class="sxs-lookup"><span data-stu-id="51265-118">First, create a base class called `Shape`, and derived classes such as `Rectangle`, `Circle`, and `Triangle`.</span></span> <span data-ttu-id="51265-119">將稱為 `Shape` 的虛擬方法提供給 `Draw` 類別，然後在每個衍生類別中覆寫此方法，以繪製該類別代表的特定圖形。</span><span class="sxs-lookup"><span data-stu-id="51265-119">Give the `Shape` class a virtual method called `Draw`, and override it in each derived class to draw the particular shape that the class represents.</span></span> <span data-ttu-id="51265-120">建立 `List<Shape>` 物件，並在 `Circle` 其中新增、 `Triangle` 和 `Rectangle` 。</span><span class="sxs-lookup"><span data-stu-id="51265-120">Create a `List<Shape>` object and add a `Circle`, `Triangle`, and `Rectangle` to it.</span></span>

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

<span data-ttu-id="51265-121">若要更新繪圖介面，請使用 [foreach](../../language-reference/keywords/foreach-in.md) 迴圈逐一查看清單，並在清單中的每個 `Shape` 物件上呼叫 `Draw` 方法。</span><span class="sxs-lookup"><span data-stu-id="51265-121">To update the drawing surface, use a [foreach](../../language-reference/keywords/foreach-in.md) loop to iterate through the list and call the `Draw` method on each `Shape` object in the list.</span></span> <span data-ttu-id="51265-122">即使清單中的每個物件都有已宣告的類型 `Shape` ，它還是會叫用的執行時間類型（每個衍生類別中的方法的覆寫版本）。</span><span class="sxs-lookup"><span data-stu-id="51265-122">Even though each object in the list has a declared type of `Shape`, it's the run-time type (the overridden version of the method in each derived class) that will be invoked.</span></span>

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

<span data-ttu-id="51265-123">在 C# 中，所有類型都是多型類型，因為所有類型 (包括使用者定義的類型) 都是繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="51265-123">In C#, every type is polymorphic because all types, including user-defined types, inherit from <xref:System.Object>.</span></span>  

## <a name="polymorphism-overview"></a><span data-ttu-id="51265-124">多型總覽</span><span class="sxs-lookup"><span data-stu-id="51265-124">Polymorphism overview</span></span>

### <a name="virtual-members"></a><span data-ttu-id="51265-125">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="51265-125">Virtual members</span></span>

<span data-ttu-id="51265-126">當衍生類別繼承自基類時，它會取得基類的所有方法、欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="51265-126">When a derived class inherits from a base class, it gains all the methods, fields, properties, and events of the base class.</span></span> <span data-ttu-id="51265-127">衍生類別的設計工具針對虛擬方法的行為有不同的選擇：</span><span class="sxs-lookup"><span data-stu-id="51265-127">The designer of the derived class has different choices for the behavior of virtual methods:</span></span>

- <span data-ttu-id="51265-128">衍生的類別可能會覆寫基類中的虛擬成員，並定義新的行為。</span><span class="sxs-lookup"><span data-stu-id="51265-128">The derived class may override virtual members in the base class, defining new behavior.</span></span>
- <span data-ttu-id="51265-129">衍生的類別會繼承最接近的基類方法，而不會覆寫它、保留現有的行為，但允許進一步的衍生類別來覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="51265-129">The derived class inherit the closest base class method without overriding it, preserving the existing behavior but enabling further derived classes to override the method.</span></span>
- <span data-ttu-id="51265-130">衍生的類別可以定義隱藏基類實作為之成員的新非虛擬執行。</span><span class="sxs-lookup"><span data-stu-id="51265-130">The derived class may define new non-virtual implementation of those members that hide the base class implementations.</span></span>

<span data-ttu-id="51265-131">只有在基底類別成員宣告為 [virtual](../../language-reference/keywords/virtual.md) 或 [abstract](../../language-reference/keywords/abstract.md) 時，衍生類別才能覆寫基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="51265-131">A derived class can override a base class member only if the base class member is declared as [virtual](../../language-reference/keywords/virtual.md) or [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="51265-132">衍生成員必須使用 [override](../../language-reference/keywords/override.md) 關鍵字明確指出方法預定會參與虛擬引動過程。</span><span class="sxs-lookup"><span data-stu-id="51265-132">The derived member must use the [override](../../language-reference/keywords/override.md) keyword to explicitly indicate that the method is intended to participate in virtual invocation.</span></span> <span data-ttu-id="51265-133">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="51265-133">The following code provides an example:</span></span>

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

<span data-ttu-id="51265-134">欄位不可以是虛擬的;只有方法、屬性、事件和索引子可以是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="51265-134">Fields cannot be virtual; only methods, properties, events, and indexers can be virtual.</span></span> <span data-ttu-id="51265-135">當衍生類別覆寫虛擬成員時，即使將該類別的執行個體當做基底類別的執行個體來存取，也會呼叫該成員。</span><span class="sxs-lookup"><span data-stu-id="51265-135">When a derived class overrides a virtual member, that member is called even when an instance of that class is being accessed as an instance of the base class.</span></span> <span data-ttu-id="51265-136">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="51265-136">The following code provides an example:</span></span>

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#SnippetTestVirtualMethods)]

<span data-ttu-id="51265-137">虛擬方法和屬性可讓衍生類別不需要使用方法的基底類別實作，即可擴充基底類別。</span><span class="sxs-lookup"><span data-stu-id="51265-137">Virtual methods and properties enable derived classes to extend a base class without needing to use the base class implementation of a method.</span></span> <span data-ttu-id="51265-138">如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="51265-138">For more information, see [Versioning with the Override and New Keywords](./versioning-with-the-override-and-new-keywords.md).</span></span> <span data-ttu-id="51265-139">介面是用來定義將其實作保留給衍生類別之一個方法或一組方法的另一種做法。</span><span class="sxs-lookup"><span data-stu-id="51265-139">An interface provides another way to define a method or set of methods whose implementation is left to derived classes.</span></span> <span data-ttu-id="51265-140">如需詳細資訊，請參閱[介面](../interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="51265-140">For more information, see [Interfaces](../interfaces/index.md).</span></span>

### <a name="hide-base-class-members-with-new-members"></a><span data-ttu-id="51265-141">以新成員隱藏基類成員</span><span class="sxs-lookup"><span data-stu-id="51265-141">Hide base class members with new members</span></span>

<span data-ttu-id="51265-142">如果您想要讓衍生類別具有與基類中的成員同名的成員，您可以使用[new](../../language-reference/keywords/new-modifier.md)關鍵字來隱藏基類成員。</span><span class="sxs-lookup"><span data-stu-id="51265-142">If you want your derived class to have a member with the same name as a member in a base class, you can use the [new](../../language-reference/keywords/new-modifier.md) keyword to hide the base class member.</span></span> <span data-ttu-id="51265-143">`new` 關鍵字會放置在要取代之類別成員的傳回類型前面。</span><span class="sxs-lookup"><span data-stu-id="51265-143">The `new` keyword is put before the return type of a class member that is being replaced.</span></span> <span data-ttu-id="51265-144">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="51265-144">The following code provides an example:</span></span>

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

<span data-ttu-id="51265-145">藉由將衍生類別的實例轉換為基類的實例，可以從用戶端程式代碼存取隱藏的基類成員。</span><span class="sxs-lookup"><span data-stu-id="51265-145">Hidden base class members may be accessed from client code by casting the instance of the derived class to an instance of the base class.</span></span> <span data-ttu-id="51265-146">例如：</span><span class="sxs-lookup"><span data-stu-id="51265-146">For example:</span></span>

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a><span data-ttu-id="51265-147">防止衍生類別覆寫虛擬成員</span><span class="sxs-lookup"><span data-stu-id="51265-147">Prevent derived classes from overriding virtual members</span></span>  

<span data-ttu-id="51265-148">無論虛擬成員和原本宣告它的類別之間已宣告多少個類別，虛擬成員仍然是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="51265-148">Virtual members remain virtual, regardless of how many classes have been declared between the virtual member and the class that originally declared it.</span></span> <span data-ttu-id="51265-149">如果類別宣告虛擬成員，而衍生自的類別和衍生自的類別，則 `A` `B` `A` `C` `B` 類別 `C` 會繼承虛擬成員，而不論類別是否已宣告該成員的覆寫，都可以覆寫它 `B` 。</span><span class="sxs-lookup"><span data-stu-id="51265-149">If class `A` declares a virtual member, and class `B` derives from `A`, and class `C` derives from `B`, class `C` inherits the virtual member, and may override it, regardless of whether class `B` declared an override for that member.</span></span> <span data-ttu-id="51265-150">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="51265-150">The following code provides an example:</span></span>

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

<span data-ttu-id="51265-151">衍生類別可以透過將覆寫宣告為 [sealed](../../language-reference/keywords/sealed.md)，來停止虛擬繼承。</span><span class="sxs-lookup"><span data-stu-id="51265-151">A derived class can stop virtual inheritance by declaring an override as [sealed](../../language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="51265-152">停止繼承需要將關鍵字放在 `sealed` `override` 類別成員宣告的關鍵字前面。</span><span class="sxs-lookup"><span data-stu-id="51265-152">Stopping inheritance requires putting the `sealed` keyword before the `override` keyword in the class member declaration.</span></span> <span data-ttu-id="51265-153">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="51265-153">The following code provides an example:</span></span>

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

<span data-ttu-id="51265-154">在上述範例中，方法 `DoWork` 不再虛擬至任何衍生自的類別 `C` 。</span><span class="sxs-lookup"><span data-stu-id="51265-154">In the previous example, the method `DoWork` is no longer virtual to any class derived from `C`.</span></span> <span data-ttu-id="51265-155">`C`即使是轉換成類型或類型，它仍是虛擬的實例 `B` `A` 。</span><span class="sxs-lookup"><span data-stu-id="51265-155">It's still virtual for instances of `C`, even if they're cast to type `B` or type `A`.</span></span> <span data-ttu-id="51265-156">密封的方法可以使用關鍵字取代為衍生類別 `new` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="51265-156">Sealed methods can be replaced by derived classes by using the `new` keyword, as the following example shows:</span></span>

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

<span data-ttu-id="51265-157">在此情況下，如果 `DoWork` `D` 使用型別的變數呼叫，則 `D` `DoWork` 會呼叫新的。</span><span class="sxs-lookup"><span data-stu-id="51265-157">In this case, if `DoWork` is called on `D` using a variable of type `D`, the new `DoWork` is called.</span></span> <span data-ttu-id="51265-158">如果 `C` 使用、或類型的變數 `B` `A` 來存取的實例 `D` ，則的呼叫 `DoWork` 將會遵循虛擬繼承的規則，並將這些呼叫路由至 `DoWork` 類別上的執行 `C` 。</span><span class="sxs-lookup"><span data-stu-id="51265-158">If a variable of type `C`, `B`, or `A` is used to access an instance of `D`, a call to `DoWork` will follow the rules of virtual inheritance, routing those calls to the implementation of `DoWork` on class `C`.</span></span>

### <a name="access-base-class-virtual-members-from-derived-classes"></a><span data-ttu-id="51265-159">從衍生類別存取基類虛擬成員</span><span class="sxs-lookup"><span data-stu-id="51265-159">Access base class virtual members from derived classes</span></span>

<span data-ttu-id="51265-160">已取代或覆寫方法或屬性的衍生類別，仍可使用 `base` 關鍵字存取基底類別上的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="51265-160">A derived class that has replaced or overridden a method or property can still access the method or property on the base class using the `base` keyword.</span></span> <span data-ttu-id="51265-161">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="51265-161">The following code provides an example:</span></span>

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

<span data-ttu-id="51265-162">如需詳細資訊，請參閱 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="51265-162">For more information, see [base](../../language-reference/keywords/base.md).</span></span>

> [!NOTE]
> <span data-ttu-id="51265-163">建議虛擬成員使用 `base`，在其所擁有的實作中呼叫其基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="51265-163">It is recommended that virtual members use `base` to call the base class implementation of that member in their own implementation.</span></span> <span data-ttu-id="51265-164">允許發生基底類別行為，可讓衍生類別集中實作衍生類別的特定行為。</span><span class="sxs-lookup"><span data-stu-id="51265-164">Letting the base class behavior occur enables the derived class to concentrate on implementing behavior specific to the derived class.</span></span> <span data-ttu-id="51265-165">如果不呼叫基底類別實作，則衍生類別可自行決定是否要讓其行為與基底類別的行為相容。</span><span class="sxs-lookup"><span data-stu-id="51265-165">If the base class implementation is not called, it is up to the derived class to make their behavior compatible with the behavior of the base class.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="51265-166">本節內容</span><span class="sxs-lookup"><span data-stu-id="51265-166">In this section</span></span>

- [<span data-ttu-id="51265-167">使用 Override 和 New 關鍵字進行版本設定</span><span class="sxs-lookup"><span data-stu-id="51265-167">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="51265-168">了解使用 Override 和 New 關鍵字的時機</span><span class="sxs-lookup"><span data-stu-id="51265-168">Knowing When to Use Override and New Keywords</span></span>](./knowing-when-to-use-override-and-new-keywords.md)
- [<span data-ttu-id="51265-169">如何覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="51265-169">How to override the ToString method</span></span>](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a><span data-ttu-id="51265-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51265-170">See also</span></span>

- [<span data-ttu-id="51265-171">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="51265-171">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="51265-172">繼承</span><span class="sxs-lookup"><span data-stu-id="51265-172">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="51265-173">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="51265-173">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="51265-174">方法</span><span class="sxs-lookup"><span data-stu-id="51265-174">Methods</span></span>](./methods.md)
- [<span data-ttu-id="51265-175">事件</span><span class="sxs-lookup"><span data-stu-id="51265-175">Events</span></span>](../events/index.md)
- [<span data-ttu-id="51265-176">屬性</span><span class="sxs-lookup"><span data-stu-id="51265-176">Properties</span></span>](./properties.md)
- [<span data-ttu-id="51265-177">索引子</span><span class="sxs-lookup"><span data-stu-id="51265-177">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="51265-178">類型</span><span class="sxs-lookup"><span data-stu-id="51265-178">Types</span></span>](../types/index.md)
