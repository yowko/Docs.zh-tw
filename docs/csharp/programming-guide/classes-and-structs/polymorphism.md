---
title: 多型 - C# 程式設計手冊
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170165"
---
# <a name="polymorphism-c-programming-guide"></a><span data-ttu-id="b190f-102">多型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b190f-102">Polymorphism (C# Programming Guide)</span></span>

<span data-ttu-id="b190f-103">多型通常是指物件導向程式設計的第三個重要部分，其重要性僅次於封裝和繼承。</span><span class="sxs-lookup"><span data-stu-id="b190f-103">Polymorphism is often referred to as the third pillar of object-oriented programming, after encapsulation and inheritance.</span></span> <span data-ttu-id="b190f-104">多型在希臘文中表示「多種形狀」，可分成下列兩方面：</span><span class="sxs-lookup"><span data-stu-id="b190f-104">Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:</span></span>
  
- <span data-ttu-id="b190f-105">在執行階段，衍生類別物件可視為方法參數和集合或陣列等位置中的基底類別物件。</span><span class="sxs-lookup"><span data-stu-id="b190f-105">At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays.</span></span> <span data-ttu-id="b190f-106">發生此多態性時，物件的聲明類型不再與其運行時類型相同。</span><span class="sxs-lookup"><span data-stu-id="b190f-106">When this polymorphism occurs, the object's declared type is no longer identical to its run-time type.</span></span>
- <span data-ttu-id="b190f-107">基底類別可以定義和實作 [virtual「方法」](../../language-reference/keywords/virtual.md) \*\*，而衍生類別可以[覆寫](../../language-reference/keywords/override.md)這些方法，換句話說，衍生類別會提供自己的定義和實作。</span><span class="sxs-lookup"><span data-stu-id="b190f-107">Base classes may define and implement [virtual](../../language-reference/keywords/virtual.md) *methods*, and derived classes can [override](../../language-reference/keywords/override.md) them, which means they provide their own definition and implementation.</span></span> <span data-ttu-id="b190f-108">在執行階段，當用戶端程式碼呼叫方法時，CLR 會查詢物件的執行階段類型，然後叫用虛擬方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="b190f-108">At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method.</span></span> <span data-ttu-id="b190f-109">在原始程式碼中，可以調用基類上的方法，並導致執行派生類的方法版本。</span><span class="sxs-lookup"><span data-stu-id="b190f-109">In your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.</span></span>

<span data-ttu-id="b190f-110">虛擬方法可讓您以一致的方式來使用相關物件群組。</span><span class="sxs-lookup"><span data-stu-id="b190f-110">Virtual methods enable you to work with groups of related objects in a uniform way.</span></span> <span data-ttu-id="b190f-111">例如，假設您有一個繪圖應用程式，可讓使用者在繪圖介面上建立各種圖形。</span><span class="sxs-lookup"><span data-stu-id="b190f-111">For example, suppose you have a drawing application that enables a user to create various kinds of shapes on a drawing surface.</span></span> <span data-ttu-id="b190f-112">您不知道使用者將在編譯時期建立哪一種圖形。</span><span class="sxs-lookup"><span data-stu-id="b190f-112">You do not know at compile time which specific types of shapes the user will create.</span></span> <span data-ttu-id="b190f-113">但是，應用程式必須追蹤所建立的所有不同圖形類型，並且必須根據使用者滑鼠動作來更新圖形。</span><span class="sxs-lookup"><span data-stu-id="b190f-113">However, the application has to keep track of all the various types of shapes that are created, and it has to update them in response to user mouse actions.</span></span> <span data-ttu-id="b190f-114">您可以使用多型，分兩個基本步驟來解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="b190f-114">You can use polymorphism to solve this problem in two basic steps:</span></span>

1. <span data-ttu-id="b190f-115">建立類別階層架構，其中每個特定圖形類別都是衍生自一個通用基底類別。</span><span class="sxs-lookup"><span data-stu-id="b190f-115">Create a class hierarchy in which each specific shape class derives from a common base class.</span></span>
1. <span data-ttu-id="b190f-116">使用虛擬方法，透過對基底類別方法發出單一呼叫，在任何衍生類別上叫用適當的方法。</span><span class="sxs-lookup"><span data-stu-id="b190f-116">Use a virtual method to invoke the appropriate method on any derived class through a single call to the base class method.</span></span>

<span data-ttu-id="b190f-117">首先，建立稱為 `Shape` 的基底類別，以及 `Rectangle`、`Circle` 和 `Triangle` 等衍生類別。</span><span class="sxs-lookup"><span data-stu-id="b190f-117">First, create a base class called `Shape`, and derived classes such as `Rectangle`, `Circle`, and `Triangle`.</span></span> <span data-ttu-id="b190f-118">將稱為 `Shape` 的虛擬方法提供給 `Draw` 類別，然後在每個衍生類別中覆寫此方法，以繪製該類別代表的特定圖形。</span><span class="sxs-lookup"><span data-stu-id="b190f-118">Give the `Shape` class a virtual method called `Draw`, and override it in each derived class to draw the particular shape that the class represents.</span></span> <span data-ttu-id="b190f-119">創建物件`List<Shape>`並添加`Circle`、`Triangle`和`Rectangle`。</span><span class="sxs-lookup"><span data-stu-id="b190f-119">Create a `List<Shape>` object and add a `Circle`, `Triangle`, and `Rectangle` to it.</span></span>

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

<span data-ttu-id="b190f-120">若要更新繪圖介面，請使用 [foreach](../../language-reference/keywords/foreach-in.md) 迴圈逐一查看清單，並在清單中的每個 `Shape` 物件上呼叫 `Draw` 方法。</span><span class="sxs-lookup"><span data-stu-id="b190f-120">To update the drawing surface, use a [foreach](../../language-reference/keywords/foreach-in.md) loop to iterate through the list and call the `Draw` method on each `Shape` object in the list.</span></span> <span data-ttu-id="b190f-121">即使清單中的每個物件都有聲明的類型`Shape`，但將被調用的是運行時類型（每個派生類中方法的重寫版本）。</span><span class="sxs-lookup"><span data-stu-id="b190f-121">Even though each object in the list has a declared type of `Shape`, it's the run-time type (the overridden version of the method in each derived class) that will be invoked.</span></span>

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

<span data-ttu-id="b190f-122">在 C# 中，所有類型都是多型類型，因為所有類型 (包括使用者定義的類型) 都是繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="b190f-122">In C#, every type is polymorphic because all types, including user-defined types, inherit from <xref:System.Object>.</span></span>  

## <a name="polymorphism-overview"></a><span data-ttu-id="b190f-123">多態性概述</span><span class="sxs-lookup"><span data-stu-id="b190f-123">Polymorphism overview</span></span>

### <a name="virtual-members"></a><span data-ttu-id="b190f-124">虛擬成員</span><span class="sxs-lookup"><span data-stu-id="b190f-124">Virtual members</span></span>

<span data-ttu-id="b190f-125">當派生類從基類繼承時，它將獲得基類的所有方法、欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="b190f-125">When a derived class inherits from a base class, it gains all the methods, fields, properties, and events of the base class.</span></span> <span data-ttu-id="b190f-126">派生類的設計器可以針對虛擬方法的行為做出不同的選擇：</span><span class="sxs-lookup"><span data-stu-id="b190f-126">The designer of the derived class can different choices for the behavior of virtual methods:</span></span>

- <span data-ttu-id="b190f-127">派生類可以覆蓋基類中的虛擬成員，定義新行為。</span><span class="sxs-lookup"><span data-stu-id="b190f-127">The derived class may override virtual members in the base class, defining new behavior.</span></span>
- <span data-ttu-id="b190f-128">派生類繼承最接近的基類方法而不重寫它，保留現有行為，但允許進一步的派生類重寫該方法。</span><span class="sxs-lookup"><span data-stu-id="b190f-128">The derived class inherit the closest base class method without overriding it, preserving the existing behavior but enabling further derived classes to override the method.</span></span>
- <span data-ttu-id="b190f-129">派生類可以定義隱藏基類實現的成員的新非虛擬實現。</span><span class="sxs-lookup"><span data-stu-id="b190f-129">The derived class may define new non-virtual implementation of those members that hide the base class implementations.</span></span>

<span data-ttu-id="b190f-130">只有在基底類別成員宣告為 [virtual](../../language-reference/keywords/virtual.md) 或 [abstract](../../language-reference/keywords/abstract.md) 時，衍生類別才能覆寫基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="b190f-130">A derived class can override a base class member only if the base class member is declared as [virtual](../../language-reference/keywords/virtual.md) or [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="b190f-131">衍生成員必須使用 [override](../../language-reference/keywords/override.md) 關鍵字明確指出方法預定會參與虛擬引動過程。</span><span class="sxs-lookup"><span data-stu-id="b190f-131">The derived member must use the [override](../../language-reference/keywords/override.md) keyword to explicitly indicate that the method is intended to participate in virtual invocation.</span></span> <span data-ttu-id="b190f-132">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="b190f-132">The following code provides an example:</span></span>

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

<span data-ttu-id="b190f-133">欄位不能為虛擬欄位;因此，欄位不能為虛擬欄位。只有方法、屬性、事件和索引子可以是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="b190f-133">Fields cannot be virtual; only methods, properties, events, and indexers can be virtual.</span></span> <span data-ttu-id="b190f-134">當衍生類別覆寫虛擬成員時，即使將該類別的執行個體當做基底類別的執行個體來存取，也會呼叫該成員。</span><span class="sxs-lookup"><span data-stu-id="b190f-134">When a derived class overrides a virtual member, that member is called even when an instance of that class is being accessed as an instance of the base class.</span></span> <span data-ttu-id="b190f-135">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="b190f-135">The following code provides an example:</span></span>

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

<span data-ttu-id="b190f-136">虛擬方法和屬性可讓衍生類別不需要使用方法的基底類別實作，即可擴充基底類別。</span><span class="sxs-lookup"><span data-stu-id="b190f-136">Virtual methods and properties enable derived classes to extend a base class without needing to use the base class implementation of a method.</span></span> <span data-ttu-id="b190f-137">如需詳細資訊，請參閱[使用 Override 和 New 關鍵字進行版本控制](./versioning-with-the-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="b190f-137">For more information, see [Versioning with the Override and New Keywords](./versioning-with-the-override-and-new-keywords.md).</span></span> <span data-ttu-id="b190f-138">介面是用來定義將其實作保留給衍生類別之一個方法或一組方法的另一種做法。</span><span class="sxs-lookup"><span data-stu-id="b190f-138">An interface provides another way to define a method or set of methods whose implementation is left to derived classes.</span></span> <span data-ttu-id="b190f-139">如需詳細資訊，請參閱[介面](../interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b190f-139">For more information, see [Interfaces](../interfaces/index.md).</span></span>

### <a name="hide-base-class-members-with-new-members"></a><span data-ttu-id="b190f-140">使用新成員隱藏基類成員</span><span class="sxs-lookup"><span data-stu-id="b190f-140">Hide base class members with new members</span></span>

<span data-ttu-id="b190f-141">如果希望派生類具有與基類中成員同名的成員，則可以使用[new](../../language-reference/keywords/new-modifier.md)關鍵字隱藏基類成員。</span><span class="sxs-lookup"><span data-stu-id="b190f-141">If you want your derived class to have a member with the same name as a member in a base class, you can use the [new](../../language-reference/keywords/new-modifier.md) keyword to hide the base class member.</span></span> <span data-ttu-id="b190f-142">`new` 關鍵字會放置在要取代之類別成員的傳回類型前面。</span><span class="sxs-lookup"><span data-stu-id="b190f-142">The `new` keyword is put before the return type of a class member that is being replaced.</span></span> <span data-ttu-id="b190f-143">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="b190f-143">The following code provides an example:</span></span>

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

<span data-ttu-id="b190f-144">通過將派生類的實例強制轉換到基類的實例，可以從用戶端代碼訪問隱藏的基類成員。</span><span class="sxs-lookup"><span data-stu-id="b190f-144">Hidden base class members may be accessed from client code by casting the instance of the derived class to an instance of the base class.</span></span> <span data-ttu-id="b190f-145">例如：</span><span class="sxs-lookup"><span data-stu-id="b190f-145">For example:</span></span>

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a><span data-ttu-id="b190f-146">防止派生類覆蓋虛擬成員</span><span class="sxs-lookup"><span data-stu-id="b190f-146">Prevent derived classes from overriding virtual members</span></span>  

<span data-ttu-id="b190f-147">虛擬成員保持虛擬狀態，無論虛擬成員和最初聲明它的類之間已聲明多少個類。</span><span class="sxs-lookup"><span data-stu-id="b190f-147">Virtual members remain virtual, regardless of how many classes have been declared between the virtual member and the class that originally declared it.</span></span> <span data-ttu-id="b190f-148">如果類`A`聲明虛擬成員，並且類`B`派生自`A`，則類`C``B``C`繼承虛擬成員，並且可以重寫它，而不管類`B`是否聲明瞭該成員的重寫。</span><span class="sxs-lookup"><span data-stu-id="b190f-148">If class `A` declares a virtual member, and class `B` derives from `A`, and class `C` derives from `B`, class `C` inherits the virtual member, and may override it, regardless of whether class `B` declared an override for that member.</span></span> <span data-ttu-id="b190f-149">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="b190f-149">The following code provides an example:</span></span>

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

<span data-ttu-id="b190f-150">衍生類別可以透過將覆寫宣告為 [sealed](../../language-reference/keywords/sealed.md)，來停止虛擬繼承。</span><span class="sxs-lookup"><span data-stu-id="b190f-150">A derived class can stop virtual inheritance by declaring an override as [sealed](../../language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="b190f-151">停止繼承需要將`sealed`關鍵字放在類成員`override`聲明中的關鍵字之前。</span><span class="sxs-lookup"><span data-stu-id="b190f-151">Stopping inheritance requires putting the `sealed` keyword before the `override` keyword in the class member declaration.</span></span> <span data-ttu-id="b190f-152">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="b190f-152">The following code provides an example:</span></span>

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

<span data-ttu-id="b190f-153">在前面的示例中，該方法`DoWork`不再對派生自`C`的任何類具有虛擬性。</span><span class="sxs-lookup"><span data-stu-id="b190f-153">In the previous example, the method `DoWork` is no longer virtual to any class derived from `C`.</span></span> <span data-ttu-id="b190f-154">對於 的實例，即使它們被強制`C`轉換為鍵入`B`或鍵入`A`，它仍然是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="b190f-154">It's still virtual for instances of `C`, even if they're cast to type `B` or type `A`.</span></span> <span data-ttu-id="b190f-155">可以使用`new`關鍵字將密封方法替換為派生類，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="b190f-155">Sealed methods can be replaced by derived classes by using the `new` keyword, as the following example shows:</span></span>

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

<span data-ttu-id="b190f-156">`DoWork`在這種情況下，如果使用`D`類型的`D`變數調用 new， 則調用 new。 `DoWork`</span><span class="sxs-lookup"><span data-stu-id="b190f-156">In this case, if `DoWork` is called on `D` using a variable of type `D`, the new `DoWork` is called.</span></span> <span data-ttu-id="b190f-157">`C`如果類型 中的變數`B`、`A`或 用於訪問 的`D`實例， 調用`DoWork`將遵循虛擬繼承的規則，將這些調用路由到 類`DoWork``C`上的實現 。</span><span class="sxs-lookup"><span data-stu-id="b190f-157">If a variable of type `C`, `B`, or `A` is used to access an instance of `D`, a call to `DoWork` will follow the rules of virtual inheritance, routing those calls to the implementation of `DoWork` on class `C`.</span></span>

### <a name="access-base-class-virtual-members-from-derived-classes"></a><span data-ttu-id="b190f-158">從派生類訪問基類虛擬成員</span><span class="sxs-lookup"><span data-stu-id="b190f-158">Access base class virtual members from derived classes</span></span>

<span data-ttu-id="b190f-159">已取代或覆寫方法或屬性的衍生類別，仍可使用 `base` 關鍵字存取基底類別上的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="b190f-159">A derived class that has replaced or overridden a method or property can still access the method or property on the base class using the `base` keyword.</span></span> <span data-ttu-id="b190f-160">下列程式碼提供一個範例：</span><span class="sxs-lookup"><span data-stu-id="b190f-160">The following code provides an example:</span></span>

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

<span data-ttu-id="b190f-161">如需詳細資訊，請參閱 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="b190f-161">For more information, see [base](../../language-reference/keywords/base.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b190f-162">建議虛擬成員使用 `base`，在其所擁有的實作中呼叫其基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="b190f-162">It is recommended that virtual members use `base` to call the base class implementation of that member in their own implementation.</span></span> <span data-ttu-id="b190f-163">允許發生基底類別行為，可讓衍生類別集中實作衍生類別的特定行為。</span><span class="sxs-lookup"><span data-stu-id="b190f-163">Letting the base class behavior occur enables the derived class to concentrate on implementing behavior specific to the derived class.</span></span> <span data-ttu-id="b190f-164">如果不呼叫基底類別實作，則衍生類別可自行決定是否要讓其行為與基底類別的行為相容。</span><span class="sxs-lookup"><span data-stu-id="b190f-164">If the base class implementation is not called, it is up to the derived class to make their behavior compatible with the behavior of the base class.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b190f-165">本節內容</span><span class="sxs-lookup"><span data-stu-id="b190f-165">In this section</span></span>

- [<span data-ttu-id="b190f-166">使用 Override 和 New 關鍵字進行版本控制</span><span class="sxs-lookup"><span data-stu-id="b190f-166">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="b190f-167">了解使用 Override 和 New 關鍵字的時機</span><span class="sxs-lookup"><span data-stu-id="b190f-167">Knowing When to Use Override and New Keywords</span></span>](./knowing-when-to-use-override-and-new-keywords.md)
- [<span data-ttu-id="b190f-168">如何覆寫 ToString 方法</span><span class="sxs-lookup"><span data-stu-id="b190f-168">How to override the ToString method</span></span>](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a><span data-ttu-id="b190f-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b190f-169">See also</span></span>

- [<span data-ttu-id="b190f-170">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b190f-170">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b190f-171">繼承</span><span class="sxs-lookup"><span data-stu-id="b190f-171">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="b190f-172">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="b190f-172">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="b190f-173">方法</span><span class="sxs-lookup"><span data-stu-id="b190f-173">Methods</span></span>](./methods.md)
- [<span data-ttu-id="b190f-174">事件</span><span class="sxs-lookup"><span data-stu-id="b190f-174">Events</span></span>](../events/index.md)
- [<span data-ttu-id="b190f-175">屬性</span><span class="sxs-lookup"><span data-stu-id="b190f-175">Properties</span></span>](./properties.md)
- [<span data-ttu-id="b190f-176">索引子</span><span class="sxs-lookup"><span data-stu-id="b190f-176">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="b190f-177">型別</span><span class="sxs-lookup"><span data-stu-id="b190f-177">Types</span></span>](../types/index.md)
