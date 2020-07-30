---
title: 物件導向程式設計 (C#)
description: 'C # 提供對面向物件程式設計的完整支援，包括抽象、封裝、繼承和多型。'
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 0c5495aefad73a2916ad6e2bd2bf3701d0868f24
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302811"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="0d34c-103">物件導向程式設計（c #）</span><span class="sxs-lookup"><span data-stu-id="0d34c-103">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="0d34c-104">C # 提供對面向物件程式設計的完整支援，包括抽象、封裝、繼承和多型。</span><span class="sxs-lookup"><span data-stu-id="0d34c-104">C# provides full support for object-oriented programming including abstraction, encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="0d34c-105">*抽象*表示隱藏型別取用者不必要的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0d34c-105">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="0d34c-106">「封裝」\*\* 指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。</span><span class="sxs-lookup"><span data-stu-id="0d34c-106">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="0d34c-107">「繼承」\*\* 則是描述依據現有類別來建立新類別的能力。</span><span class="sxs-lookup"><span data-stu-id="0d34c-107">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="0d34c-108">「多型」\*\* 指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-108">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="0d34c-109">類別與物件</span><span class="sxs-lookup"><span data-stu-id="0d34c-109">Classes and objects</span></span>

<span data-ttu-id="0d34c-110">詞彙*類別*和*物件*會分別描述物件的*類型*和類別的*實例*。</span><span class="sxs-lookup"><span data-stu-id="0d34c-110">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="0d34c-111">因此，建立物件的動作稱為「具現化」\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d34c-111">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="0d34c-112">再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。</span><span class="sxs-lookup"><span data-stu-id="0d34c-112">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="0d34c-113">若要定義類別：</span><span class="sxs-lookup"><span data-stu-id="0d34c-113">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="0d34c-114">C # 也提供稱為*結構*的類型，當您不需要對繼承或多型的支援時很有用。</span><span class="sxs-lookup"><span data-stu-id="0d34c-114">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span> <span data-ttu-id="0d34c-115">如需詳細資訊，請參閱[在類別和結構之間選擇](../../../standard/design-guidelines/choosing-between-class-and-struct.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-115">For more information, see [Choosing between class and struct](../../../standard/design-guidelines/choosing-between-class-and-struct.md).</span></span>

<span data-ttu-id="0d34c-116">若要定義結構：</span><span class="sxs-lookup"><span data-stu-id="0d34c-116">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="0d34c-117">如需詳細資訊，請參閱[類別](../../language-reference/keywords/class.md)和[結構](../../language-reference/builtin-types/struct.md)關鍵字上的文章。</span><span class="sxs-lookup"><span data-stu-id="0d34c-117">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="0d34c-118">類別成員</span><span class="sxs-lookup"><span data-stu-id="0d34c-118">Class members</span></span>

<span data-ttu-id="0d34c-119">每個類別都有不同的「類別成員」\*\*，包括描述類別資料的屬性、定義類別行為的方法，以及提供不同類別與物件之間通訊的事件。</span><span class="sxs-lookup"><span data-stu-id="0d34c-119">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="0d34c-120">屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="0d34c-120">Properties and fields</span></span>

<span data-ttu-id="0d34c-121">欄位和屬性表示物件包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="0d34c-121">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="0d34c-122">欄位就像變數一樣，因為它們可以直接讀取或設定，受限於適當的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0d34c-122">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="0d34c-123">若要定義可從類別的實例中存取的欄位：</span><span class="sxs-lookup"><span data-stu-id="0d34c-123">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="0d34c-124">屬性具有 `get` 和 `set` 存取子，可對設定或傳回值的方式提供更多的控制。</span><span class="sxs-lookup"><span data-stu-id="0d34c-124">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="0d34c-125">C # 可讓您建立私用欄位來儲存屬性值，或使用自動執行的屬性，在幕後自動建立此欄位，並提供屬性程式的基本邏輯。</span><span class="sxs-lookup"><span data-stu-id="0d34c-125">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="0d34c-126">若要定義自動實作屬性：</span><span class="sxs-lookup"><span data-stu-id="0d34c-126">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="0d34c-127">如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：</span><span class="sxs-lookup"><span data-stu-id="0d34c-127">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="0d34c-128">大部分屬性都具有方法或程序，可以設定及取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="0d34c-128">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="0d34c-129">但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。</span><span class="sxs-lookup"><span data-stu-id="0d34c-129">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="0d34c-130">在 C# 中，則可以省略 `get` 或 `set` 屬性方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-130">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="0d34c-131">不過，自動執行的屬性不能是寫入。</span><span class="sxs-lookup"><span data-stu-id="0d34c-131">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="0d34c-132">唯讀自動執行的屬性可以在包含類別的函式中設定。</span><span class="sxs-lookup"><span data-stu-id="0d34c-132">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="0d34c-133">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0d34c-133">For more information, see:</span></span>

- [<span data-ttu-id="0d34c-134">get</span><span class="sxs-lookup"><span data-stu-id="0d34c-134">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="0d34c-135">set</span><span class="sxs-lookup"><span data-stu-id="0d34c-135">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="0d34c-136">方法</span><span class="sxs-lookup"><span data-stu-id="0d34c-136">Methods</span></span>

<span data-ttu-id="0d34c-137">「方法」\*\* 是物件可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="0d34c-137">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="0d34c-138">若要定義類別的方法：</span><span class="sxs-lookup"><span data-stu-id="0d34c-138">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="0d34c-139">類別可以有同一個方法的多個實作或「多載」\*\*，但是這些實作的參數個數和參數類型並不相同。</span><span class="sxs-lookup"><span data-stu-id="0d34c-139">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="0d34c-140">若要多載方法：</span><span class="sxs-lookup"><span data-stu-id="0d34c-140">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="0d34c-141">在多數情況下，您是在類別定義中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-141">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="0d34c-142">不過， C# 也支援「擴充方法」\*\*，允許您在現有類別的實際定義之外將方法新增至類別。</span><span class="sxs-lookup"><span data-stu-id="0d34c-142">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="0d34c-143">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0d34c-143">For more information, see:</span></span>

- [<span data-ttu-id="0d34c-144">方法</span><span class="sxs-lookup"><span data-stu-id="0d34c-144">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="0d34c-145">擴充方法</span><span class="sxs-lookup"><span data-stu-id="0d34c-145">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="0d34c-146">建構函式</span><span class="sxs-lookup"><span data-stu-id="0d34c-146">Constructors</span></span>

<span data-ttu-id="0d34c-147">建構函式是類別方法，會在建立指定類型的物件時自動執行。</span><span class="sxs-lookup"><span data-stu-id="0d34c-147">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="0d34c-148">建構函式通常用來初始化新物件的資料成員，</span><span class="sxs-lookup"><span data-stu-id="0d34c-148">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="0d34c-149">而且只能在建立類別時執行一次。</span><span class="sxs-lookup"><span data-stu-id="0d34c-149">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="0d34c-150">此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="0d34c-150">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="0d34c-151">不過，就和其他任何方法一樣，您可以建立多個建構函式多載。</span><span class="sxs-lookup"><span data-stu-id="0d34c-151">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="0d34c-152">若要定義類別的建構函式：</span><span class="sxs-lookup"><span data-stu-id="0d34c-152">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="0d34c-153">如需詳細資訊，請參閱[建構函式](../classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-153">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="0d34c-154">完成項</span><span class="sxs-lookup"><span data-stu-id="0d34c-154">Finalizers</span></span>

<span data-ttu-id="0d34c-155">完成項是用來終結類別的實例。</span><span class="sxs-lookup"><span data-stu-id="0d34c-155">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="0d34c-156">在 .NET 中，垃圾收集行程會自動管理應用程式中受管理物件的記憶體配置和釋放。</span><span class="sxs-lookup"><span data-stu-id="0d34c-156">In .NET, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="0d34c-157">不過，您可能仍需要使用完成項來清除應用程式建立的任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="0d34c-157">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="0d34c-158">一個類別只能有一個完成項。</span><span class="sxs-lookup"><span data-stu-id="0d34c-158">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="0d34c-159">如需 .NET 中完成項和垃圾收集的詳細資訊，請參閱[垃圾收集](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-159">For more information about finalizers and garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="0d34c-160">事件</span><span class="sxs-lookup"><span data-stu-id="0d34c-160">Events</span></span>

<span data-ttu-id="0d34c-161">事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="0d34c-161">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="0d34c-162">傳送 (或引發) 事件的類別稱為「發行者」**，而接收 (或處理) 事件的類別則稱為「訂閱者」**。</span><span class="sxs-lookup"><span data-stu-id="0d34c-162">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="0d34c-163">如需事件的詳細資訊以及如何引發和處理事件，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-163">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="0d34c-164">若要宣告類別中的事件，請使用 [event](../../language-reference/keywords/event.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0d34c-164">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="0d34c-165">要引發事件，請叫用事件委派。</span><span class="sxs-lookup"><span data-stu-id="0d34c-165">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="0d34c-166">若要訂閱事件，請使用 `+=` 運算子；若要取消訂閱事件，則使用 `-=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="0d34c-166">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="0d34c-167">嵌套類別</span><span class="sxs-lookup"><span data-stu-id="0d34c-167">Nested classes</span></span>

<span data-ttu-id="0d34c-168">在類別中定義的另一個類別即稱為「巢狀」\*\* 類別。</span><span class="sxs-lookup"><span data-stu-id="0d34c-168">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="0d34c-169">巢狀類別預設為私用。</span><span class="sxs-lookup"><span data-stu-id="0d34c-169">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="0d34c-170">若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0d34c-170">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="0d34c-171">存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="0d34c-171">Access modifiers and access levels</span></span>

<span data-ttu-id="0d34c-172">所有類別及類別成員都可以使用「存取修飾詞」\*\*，指定要提供給其他類別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="0d34c-172">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="0d34c-173">下列為可用的存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="0d34c-173">The following access modifiers are available:</span></span>

| <span data-ttu-id="0d34c-174">C# 修飾詞</span><span class="sxs-lookup"><span data-stu-id="0d34c-174">C# Modifier</span></span> | <span data-ttu-id="0d34c-175">定義</span><span class="sxs-lookup"><span data-stu-id="0d34c-175">Definition</span></span> |
|--|--|
| [<span data-ttu-id="0d34c-176">public</span><span class="sxs-lookup"><span data-stu-id="0d34c-176">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="0d34c-177">類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0d34c-177">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="0d34c-178">私人</span><span class="sxs-lookup"><span data-stu-id="0d34c-178">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="0d34c-179">類型或成員只能由相同類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0d34c-179">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="0d34c-180">受保護</span><span class="sxs-lookup"><span data-stu-id="0d34c-180">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="0d34c-181">類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0d34c-181">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="0d34c-182">內部</span><span class="sxs-lookup"><span data-stu-id="0d34c-182">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="0d34c-183">類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0d34c-183">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="0d34c-184">protected internal</span><span class="sxs-lookup"><span data-stu-id="0d34c-184">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="0d34c-185">類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="0d34c-185">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="0d34c-186">private protected</span><span class="sxs-lookup"><span data-stu-id="0d34c-186">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="0d34c-187">只有在基底類別組件中，於相同類別或衍生類別內的程式碼才能存取類型或成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-187">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="0d34c-188">如需詳細資訊，請參閱[存取修飾詞](../classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-188">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="0d34c-189">具現化類別</span><span class="sxs-lookup"><span data-stu-id="0d34c-189">Instantiating classes</span></span>

<span data-ttu-id="0d34c-190">若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d34c-190">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="0d34c-191">將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-191">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="0d34c-192">若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="0d34c-192">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="0d34c-193">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0d34c-193">For more information, see:</span></span>

- [<span data-ttu-id="0d34c-194">new 運算子</span><span class="sxs-lookup"><span data-stu-id="0d34c-194">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="0d34c-195">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="0d34c-195">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="0d34c-196">靜態類別與成員</span><span class="sxs-lookup"><span data-stu-id="0d34c-196">Static Classes and Members</span></span>

<span data-ttu-id="0d34c-197">類別的靜態成員是類別所有執行個體共用的屬性、程序或欄位。</span><span class="sxs-lookup"><span data-stu-id="0d34c-197">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="0d34c-198">定義靜態成員：</span><span class="sxs-lookup"><span data-stu-id="0d34c-198">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="0d34c-199">若要存取靜態成員，請使用類別的名稱，但不要建立這個類別的物件：</span><span class="sxs-lookup"><span data-stu-id="0d34c-199">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="0d34c-200">C# 中的靜態類別只有靜態成員，且無法具現化。</span><span class="sxs-lookup"><span data-stu-id="0d34c-200">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="0d34c-201">靜態成員也無法存取非靜態屬性、欄位或方法</span><span class="sxs-lookup"><span data-stu-id="0d34c-201">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="0d34c-202">如需詳細資訊，請參閱[靜態](../../language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-202">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="0d34c-203">匿名型別</span><span class="sxs-lookup"><span data-stu-id="0d34c-203">Anonymous types</span></span>

<span data-ttu-id="0d34c-204">使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義，</span><span class="sxs-lookup"><span data-stu-id="0d34c-204">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="0d34c-205">編譯器 (Compiler) 會自動幫您建立類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-205">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="0d34c-206">這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="0d34c-206">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="0d34c-207">若要建立匿名類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="0d34c-207">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="0d34c-208">如需詳細資訊，請參閱[匿名型別](../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-208">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="0d34c-209">繼承</span><span class="sxs-lookup"><span data-stu-id="0d34c-209">Inheritance</span></span>

<span data-ttu-id="0d34c-210">繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。</span><span class="sxs-lookup"><span data-stu-id="0d34c-210">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="0d34c-211">成員被繼承的類別稱為「基底類別」**，而繼承這種成員的類別即稱為「衍生類別」**。</span><span class="sxs-lookup"><span data-stu-id="0d34c-211">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="0d34c-212">不過，C# 中的所有類別都隱含繼承 <xref:System.Object> 類別，這個類別會支援 .NET 類別階層架構，並為所有類別提供低階服務。</span><span class="sxs-lookup"><span data-stu-id="0d34c-212">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="0d34c-213">C# 不支援多重繼承。</span><span class="sxs-lookup"><span data-stu-id="0d34c-213">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="0d34c-214">也就是說，您只能為衍生類別指定一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="0d34c-214">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="0d34c-215">若要繼承基底類別：</span><span class="sxs-lookup"><span data-stu-id="0d34c-215">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="0d34c-216">所有類別預設都可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="0d34c-216">By default all classes can be inherited.</span></span> <span data-ttu-id="0d34c-217">不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="0d34c-217">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="0d34c-218">若要指定類別不得當做基底類別使用：</span><span class="sxs-lookup"><span data-stu-id="0d34c-218">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="0d34c-219">若要指定類別只能當做基底類別且無法執行個體化：</span><span class="sxs-lookup"><span data-stu-id="0d34c-219">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="0d34c-220">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0d34c-220">For more information, see:</span></span>

- [<span data-ttu-id="0d34c-221">sealed</span><span class="sxs-lookup"><span data-stu-id="0d34c-221">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="0d34c-222">概要</span><span class="sxs-lookup"><span data-stu-id="0d34c-222">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="0d34c-223">覆寫成員</span><span class="sxs-lookup"><span data-stu-id="0d34c-223">Overriding Members</span></span>

<span data-ttu-id="0d34c-224">衍生類別預設會從其基底類別繼承所有成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-224">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="0d34c-225">如果想要變更所繼承成員的行為，您必須覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-225">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="0d34c-226">也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。</span><span class="sxs-lookup"><span data-stu-id="0d34c-226">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="0d34c-227">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="0d34c-227">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="0d34c-228">C# 修飾詞</span><span class="sxs-lookup"><span data-stu-id="0d34c-228">C# Modifier</span></span> | <span data-ttu-id="0d34c-229">定義</span><span class="sxs-lookup"><span data-stu-id="0d34c-229">Definition</span></span> |
|--|--|
| [<span data-ttu-id="0d34c-230">虛擬</span><span class="sxs-lookup"><span data-stu-id="0d34c-230">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="0d34c-231">允許在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-231">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="0d34c-232">override</span><span class="sxs-lookup"><span data-stu-id="0d34c-232">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="0d34c-233">覆寫在基底類別中定義的虛擬 (可覆寫) 成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-233">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="0d34c-234">概要</span><span class="sxs-lookup"><span data-stu-id="0d34c-234">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="0d34c-235">要求在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-235">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="0d34c-236">new 修飾詞</span><span class="sxs-lookup"><span data-stu-id="0d34c-236">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="0d34c-237">隱藏繼承自基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="0d34c-237">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="0d34c-238">介面</span><span class="sxs-lookup"><span data-stu-id="0d34c-238">Interfaces</span></span>

<span data-ttu-id="0d34c-239">介面就像類別，可定義屬性、方法和事件集。</span><span class="sxs-lookup"><span data-stu-id="0d34c-239">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="0d34c-240">但與類別不同的是，介面並不提供實作。</span><span class="sxs-lookup"><span data-stu-id="0d34c-240">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="0d34c-241">介面是由類別實作，並定義為與類別不同的實體。</span><span class="sxs-lookup"><span data-stu-id="0d34c-241">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="0d34c-242">介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。</span><span class="sxs-lookup"><span data-stu-id="0d34c-242">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="0d34c-243">若要定義介面：</span><span class="sxs-lookup"><span data-stu-id="0d34c-243">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="0d34c-244">若要在類別中實作介面：</span><span class="sxs-lookup"><span data-stu-id="0d34c-244">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="0d34c-245">如需詳細資訊，請[參閱介面上](../interfaces/index.md)的程式設計指南一文和[interface](../../language-reference/keywords/interface.md)關鍵字上的語言參考文章。</span><span class="sxs-lookup"><span data-stu-id="0d34c-245">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="0d34c-246">泛型</span><span class="sxs-lookup"><span data-stu-id="0d34c-246">Generics</span></span>

<span data-ttu-id="0d34c-247">.NET 中的類別、結構、介面和方法可以包含定義可儲存或使用之物件類型的*類型參數*。</span><span class="sxs-lookup"><span data-stu-id="0d34c-247">Classes, structures, interfaces, and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="0d34c-248">泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="0d34c-248">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="0d34c-249">若要定義泛型類別：</span><span class="sxs-lookup"><span data-stu-id="0d34c-249">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="0d34c-250">若要建立泛型類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="0d34c-250">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="0d34c-251">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0d34c-251">For more information, see:</span></span>

- [<span data-ttu-id="0d34c-252">.NET 的泛型</span><span class="sxs-lookup"><span data-stu-id="0d34c-252">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="0d34c-253">泛型 - C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="0d34c-253">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="0d34c-254">委派</span><span class="sxs-lookup"><span data-stu-id="0d34c-254">Delegates</span></span>

<span data-ttu-id="0d34c-255">「委派」\*\* 是定義方法簽章的類型，可以提供任何具有相容簽章之方法的參考。</span><span class="sxs-lookup"><span data-stu-id="0d34c-255">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="0d34c-256">您可以透過委派叫用 (Invoke) 或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-256">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="0d34c-257">委派可以用來將方法當做引數傳遞給其他方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-257">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="0d34c-258">事件處理常式就是透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="0d34c-258">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="0d34c-259">如需使用委派處理事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d34c-259">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="0d34c-260">若要建立委派：</span><span class="sxs-lookup"><span data-stu-id="0d34c-260">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="0d34c-261">若要建立與委派所指定簽章相符之方法的參考：</span><span class="sxs-lookup"><span data-stu-id="0d34c-261">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
    {
        // Add code here.
    }

    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="0d34c-262">如需詳細資訊，請[參閱委派](../../language-reference/builtin-types/reference-types.md)關鍵字上的程式設計指南[文章和語言](../delegates/index.md)參考文章。</span><span class="sxs-lookup"><span data-stu-id="0d34c-262">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d34c-263">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d34c-263">See also</span></span>

- [<span data-ttu-id="0d34c-264">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0d34c-264">C# Programming Guide</span></span>](../index.md)
