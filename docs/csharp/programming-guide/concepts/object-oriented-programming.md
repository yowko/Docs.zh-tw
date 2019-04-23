---
title: 物件導向程式設計 (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: a7a3ce1b33d040b337087dfede90b58906c95cbd
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481167"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="cb23b-102">物件導向程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="cb23b-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="cb23b-103">C# 為包括封裝、繼承和多型在內的物件導向程式設計提供完整支援。</span><span class="sxs-lookup"><span data-stu-id="cb23b-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="cb23b-104">「封裝」指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。</span><span class="sxs-lookup"><span data-stu-id="cb23b-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="cb23b-105">「繼承」則是描述依據現有類別來建立新類別的能力。</span><span class="sxs-lookup"><span data-stu-id="cb23b-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="cb23b-106">「多型」指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="cb23b-107">本節將說明下列概念：</span><span class="sxs-lookup"><span data-stu-id="cb23b-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="cb23b-108">類別與物件</span><span class="sxs-lookup"><span data-stu-id="cb23b-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="cb23b-109">類別成員</span><span class="sxs-lookup"><span data-stu-id="cb23b-109">Class Members</span></span>](#Members)

        [Properties and Fields](#Properties)

        [Methods](#Methods)

        [Constructors](#Constructors)

        [Finalizers](#Finalizers)

        [Events](#Events)

        [Nested Classes](#NestedClasses)

  - [<span data-ttu-id="cb23b-110">存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="cb23b-110">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="cb23b-111">具現化類別</span><span class="sxs-lookup"><span data-stu-id="cb23b-111">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="cb23b-112">靜態類別與成員</span><span class="sxs-lookup"><span data-stu-id="cb23b-112">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="cb23b-113">匿名類型</span><span class="sxs-lookup"><span data-stu-id="cb23b-113">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="cb23b-114">繼承</span><span class="sxs-lookup"><span data-stu-id="cb23b-114">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="cb23b-115">覆寫成員</span><span class="sxs-lookup"><span data-stu-id="cb23b-115">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="cb23b-116">介面</span><span class="sxs-lookup"><span data-stu-id="cb23b-116">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="cb23b-117">泛型</span><span class="sxs-lookup"><span data-stu-id="cb23b-117">Generics</span></span>](#Generics)

- [<span data-ttu-id="cb23b-118">委派</span><span class="sxs-lookup"><span data-stu-id="cb23b-118">Delegates</span></span>](#Delegates)

## <a name="Classes"></a><span data-ttu-id="cb23b-119">類別與物件</span><span class="sxs-lookup"><span data-stu-id="cb23b-119">Classes and Objects</span></span>

<span data-ttu-id="cb23b-120">「類別」和「物件」有時會交換使用，但事實上，類別說的是物件的「型別」，而物件則是類別之可使用的「執行個體」。</span><span class="sxs-lookup"><span data-stu-id="cb23b-120">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="cb23b-121">因此，建立物件的動作稱為「具現化」。</span><span class="sxs-lookup"><span data-stu-id="cb23b-121">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="cb23b-122">再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。</span><span class="sxs-lookup"><span data-stu-id="cb23b-122">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="cb23b-123">若要定義類別：</span><span class="sxs-lookup"><span data-stu-id="cb23b-123">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="cb23b-124">C# 也會提供輕量版的類別，稱為「結構」，當您必須建立龐大物件陣列而不想要使用太多記憶體時，這個結構會很有用。</span><span class="sxs-lookup"><span data-stu-id="cb23b-124">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="cb23b-125">若要定義結構：</span><span class="sxs-lookup"><span data-stu-id="cb23b-125">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="cb23b-126">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-126">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-127">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="cb23b-127">class</span></span>](../../../csharp/language-reference/keywords/class.md)

- [<span data-ttu-id="cb23b-128">struct</span><span class="sxs-lookup"><span data-stu-id="cb23b-128">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)

### <a name="Members"></a> <span data-ttu-id="cb23b-129">類別成員</span><span class="sxs-lookup"><span data-stu-id="cb23b-129">Class Members</span></span>

<span data-ttu-id="cb23b-130">每個類別都有不同的「類別成員」，包括描述類別資料的屬性、定義類別行為的方法，以及提供不同類別與物件之間通訊的事件。</span><span class="sxs-lookup"><span data-stu-id="cb23b-130">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a> <span data-ttu-id="cb23b-131">屬性與欄位</span><span class="sxs-lookup"><span data-stu-id="cb23b-131">Properties and Fields</span></span>

<span data-ttu-id="cb23b-132">欄位和屬性表示物件包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="cb23b-132">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="cb23b-133">欄位就像是變數，可直接讀取或設定。</span><span class="sxs-lookup"><span data-stu-id="cb23b-133">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="cb23b-134">若要定義欄位：</span><span class="sxs-lookup"><span data-stu-id="cb23b-134">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="cb23b-135">屬性具有取得和設定程序，讓您更容易控制設定與傳回數值的方式。</span><span class="sxs-lookup"><span data-stu-id="cb23b-135">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="cb23b-136">C# 允許您建立私用欄位來儲存屬性值，或是使用所謂的自動實作屬性，自動在幕後建立此欄位並提供屬性程序的基本邏輯。</span><span class="sxs-lookup"><span data-stu-id="cb23b-136">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="cb23b-137">若要定義自動實作屬性：</span><span class="sxs-lookup"><span data-stu-id="cb23b-137">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="cb23b-138">如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：</span><span class="sxs-lookup"><span data-stu-id="cb23b-138">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

<span data-ttu-id="cb23b-139">大部分屬性都具有方法或程序，可以設定及取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="cb23b-139">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="cb23b-140">但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。</span><span class="sxs-lookup"><span data-stu-id="cb23b-140">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="cb23b-141">在 C# 中，則可以省略 `get` 或 `set` 屬性方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-141">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="cb23b-142">不過，自動實作的屬性不可以是唯讀或唯寫。</span><span class="sxs-lookup"><span data-stu-id="cb23b-142">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="cb23b-143">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-143">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-144">get</span><span class="sxs-lookup"><span data-stu-id="cb23b-144">get</span></span>](../../../csharp/language-reference/keywords/get.md)

- [<span data-ttu-id="cb23b-145">設定</span><span class="sxs-lookup"><span data-stu-id="cb23b-145">set</span></span>](../../../csharp/language-reference/keywords/set.md)

#### <a name="Methods"></a> <span data-ttu-id="cb23b-146">方法</span><span class="sxs-lookup"><span data-stu-id="cb23b-146">Methods</span></span>

<span data-ttu-id="cb23b-147">「方法」是物件可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="cb23b-147">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="cb23b-148">若要定義類別的方法：</span><span class="sxs-lookup"><span data-stu-id="cb23b-148">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="cb23b-149">類別可以有同一個方法的多個實作或「多載」，但是這些實作的參數個數和參數類型並不相同。</span><span class="sxs-lookup"><span data-stu-id="cb23b-149">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="cb23b-150">若要多載方法：</span><span class="sxs-lookup"><span data-stu-id="cb23b-150">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="cb23b-151">在多數情況下，您是在類別定義中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-151">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="cb23b-152">不過， C# 也支援「擴充方法」，允許您在現有類別的實際定義之外將方法新增至類別。</span><span class="sxs-lookup"><span data-stu-id="cb23b-152">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="cb23b-153">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-153">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-154">方法</span><span class="sxs-lookup"><span data-stu-id="cb23b-154">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="cb23b-155">擴充方法</span><span class="sxs-lookup"><span data-stu-id="cb23b-155">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> <span data-ttu-id="cb23b-156">建構函式</span><span class="sxs-lookup"><span data-stu-id="cb23b-156">Constructors</span></span>

<span data-ttu-id="cb23b-157">建構函式是類別方法，會在建立指定類型的物件時自動執行。</span><span class="sxs-lookup"><span data-stu-id="cb23b-157">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="cb23b-158">建構函式通常用來初始化新物件的資料成員，</span><span class="sxs-lookup"><span data-stu-id="cb23b-158">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="cb23b-159">而且只能在建立類別時執行一次。</span><span class="sxs-lookup"><span data-stu-id="cb23b-159">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="cb23b-160">此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="cb23b-160">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="cb23b-161">不過，就和其他任何方法一樣，您可以建立多個建構函式多載。</span><span class="sxs-lookup"><span data-stu-id="cb23b-161">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="cb23b-162">若要定義類別的建構函式：</span><span class="sxs-lookup"><span data-stu-id="cb23b-162">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="cb23b-163">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-163">For more information, see:</span></span>

<span data-ttu-id="cb23b-164">[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-164">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a> <span data-ttu-id="cb23b-165">完成項</span><span class="sxs-lookup"><span data-stu-id="cb23b-165">Finalizers</span></span>

<span data-ttu-id="cb23b-166">完成項是用來解構類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb23b-166">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="cb23b-167">在 .NET Framework 中，記憶體回收行程會自動管理應用程式中 Managed 物件的記憶體配置及釋放。</span><span class="sxs-lookup"><span data-stu-id="cb23b-167">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="cb23b-168">不過，您可能仍需要使用完成項來清除應用程式建立的任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="cb23b-168">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="cb23b-169">一個類別只能有一個完成項。</span><span class="sxs-lookup"><span data-stu-id="cb23b-169">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="cb23b-170">如需 .NET Framework 的完成項和記憶體回收的詳細資訊，請參閱[記憶體回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-170">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a> <span data-ttu-id="cb23b-171">事件</span><span class="sxs-lookup"><span data-stu-id="cb23b-171">Events</span></span>

<span data-ttu-id="cb23b-172">事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="cb23b-172">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="cb23b-173">傳送 (或引發) 事件的類別稱為「發行者」，而接收 (或處理) 事件的類別則稱為「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="cb23b-173">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="cb23b-174">如需事件的詳細資訊以及如何引發和處理事件，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-174">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="cb23b-175">若要宣告類別中的事件，請使用 [event](../../../csharp/language-reference/keywords/event.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cb23b-175">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="cb23b-176">要引發事件，請叫用事件委派。</span><span class="sxs-lookup"><span data-stu-id="cb23b-176">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="cb23b-177">若要訂閱事件，請使用 `+=` 運算子；若要取消訂閱事件，則使用 `-=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="cb23b-177">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a><span data-ttu-id="cb23b-178">巢狀類別</span><span class="sxs-lookup"><span data-stu-id="cb23b-178">Nested Classes</span></span>

<span data-ttu-id="cb23b-179">在類別中定義的另一個類別即稱為「巢狀」類別。</span><span class="sxs-lookup"><span data-stu-id="cb23b-179">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="cb23b-180">巢狀類別預設為私用。</span><span class="sxs-lookup"><span data-stu-id="cb23b-180">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="cb23b-181">若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb23b-181">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> <span data-ttu-id="cb23b-182">存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="cb23b-182">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="cb23b-183">所有類別及類別成員都可以使用「存取修飾詞」，指定要提供給其他類別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="cb23b-183">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="cb23b-184">下列為可用的存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="cb23b-184">The following access modifiers are available:</span></span>

|<span data-ttu-id="cb23b-185">C# 修飾詞</span><span class="sxs-lookup"><span data-stu-id="cb23b-185">C# Modifier</span></span>|<span data-ttu-id="cb23b-186">定義</span><span class="sxs-lookup"><span data-stu-id="cb23b-186">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="cb23b-187">public</span><span class="sxs-lookup"><span data-stu-id="cb23b-187">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="cb23b-188">類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="cb23b-188">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="cb23b-189">private</span><span class="sxs-lookup"><span data-stu-id="cb23b-189">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="cb23b-190">類型或成員只能由相同類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="cb23b-190">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="cb23b-191">protected</span><span class="sxs-lookup"><span data-stu-id="cb23b-191">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="cb23b-192">類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="cb23b-192">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="cb23b-193">internal</span><span class="sxs-lookup"><span data-stu-id="cb23b-193">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="cb23b-194">類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cb23b-194">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="cb23b-195">protected internal</span><span class="sxs-lookup"><span data-stu-id="cb23b-195">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="cb23b-196">類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="cb23b-196">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="cb23b-197">private protected</span><span class="sxs-lookup"><span data-stu-id="cb23b-197">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="cb23b-198">只有在基底類別組件中，於相同類別或衍生類別內的程式碼才能存取類型或成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-198">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="cb23b-199">如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-199">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a> <span data-ttu-id="cb23b-200">具現化類別</span><span class="sxs-lookup"><span data-stu-id="cb23b-200">Instantiating Classes</span></span>

<span data-ttu-id="cb23b-201">若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb23b-201">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="cb23b-202">將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-202">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="cb23b-203">若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="cb23b-203">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="cb23b-204">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-204">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-205">new 運算子</span><span class="sxs-lookup"><span data-stu-id="cb23b-205">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)

- [<span data-ttu-id="cb23b-206">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="cb23b-206">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> <span data-ttu-id="cb23b-207">靜態類別與成員</span><span class="sxs-lookup"><span data-stu-id="cb23b-207">Static Classes and Members</span></span>

<span data-ttu-id="cb23b-208">類別的靜態成員是類別所有執行個體共用的屬性、程序或欄位。</span><span class="sxs-lookup"><span data-stu-id="cb23b-208">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="cb23b-209">定義靜態成員：</span><span class="sxs-lookup"><span data-stu-id="cb23b-209">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="cb23b-210">若要存取靜態成員，請使用類別的名稱，但不要建立這個類別的物件：</span><span class="sxs-lookup"><span data-stu-id="cb23b-210">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="cb23b-211">C# 中的靜態類別只有靜態成員，且無法具現化。</span><span class="sxs-lookup"><span data-stu-id="cb23b-211">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="cb23b-212">靜態成員也無法存取非靜態屬性、欄位或方法</span><span class="sxs-lookup"><span data-stu-id="cb23b-212">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="cb23b-213">如需詳細資訊，請參閱[靜態](../../../csharp/language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-213">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a> <span data-ttu-id="cb23b-214">匿名型別</span><span class="sxs-lookup"><span data-stu-id="cb23b-214">Anonymous Types</span></span>

<span data-ttu-id="cb23b-215">使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義，</span><span class="sxs-lookup"><span data-stu-id="cb23b-215">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="cb23b-216">編譯器 (Compiler) 會自動幫您建立類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-216">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="cb23b-217">這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="cb23b-217">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="cb23b-218">若要建立匿名類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="cb23b-218">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="cb23b-219">如需詳細資訊，請參閱:[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-219">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a> <span data-ttu-id="cb23b-220">繼承</span><span class="sxs-lookup"><span data-stu-id="cb23b-220">Inheritance</span></span>

<span data-ttu-id="cb23b-221">繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。</span><span class="sxs-lookup"><span data-stu-id="cb23b-221">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="cb23b-222">成員被繼承的類別稱為「基底類別」，而繼承這種成員的類別即稱為「衍生類別」。</span><span class="sxs-lookup"><span data-stu-id="cb23b-222">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="cb23b-223">不過，C# 中的所有類別都隱含繼承 <xref:System.Object> 類別，這個類別會支援 .NET 類別階層架構，並為所有類別提供低階服務。</span><span class="sxs-lookup"><span data-stu-id="cb23b-223">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="cb23b-224">C# 不支援多重繼承。</span><span class="sxs-lookup"><span data-stu-id="cb23b-224">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="cb23b-225">也就是說，您只能為衍生類別指定一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="cb23b-225">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="cb23b-226">若要繼承基底類別：</span><span class="sxs-lookup"><span data-stu-id="cb23b-226">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="cb23b-227">所有類別預設都可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="cb23b-227">By default all classes can be inherited.</span></span> <span data-ttu-id="cb23b-228">不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="cb23b-228">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="cb23b-229">若要指定類別不得當做基底類別使用：</span><span class="sxs-lookup"><span data-stu-id="cb23b-229">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="cb23b-230">若要指定類別只能當做基底類別且無法執行個體化：</span><span class="sxs-lookup"><span data-stu-id="cb23b-230">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="cb23b-231">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-231">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-232">sealed</span><span class="sxs-lookup"><span data-stu-id="cb23b-232">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)

- [<span data-ttu-id="cb23b-233">abstract</span><span class="sxs-lookup"><span data-stu-id="cb23b-233">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)

### <a name="Overriding"></a> <span data-ttu-id="cb23b-234">覆寫成員</span><span class="sxs-lookup"><span data-stu-id="cb23b-234">Overriding Members</span></span>

<span data-ttu-id="cb23b-235">衍生類別預設會從其基底類別繼承所有成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-235">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="cb23b-236">如果想要變更所繼承成員的行為，您必須覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-236">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="cb23b-237">也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。</span><span class="sxs-lookup"><span data-stu-id="cb23b-237">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="cb23b-238">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="cb23b-238">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="cb23b-239">C# 修飾詞</span><span class="sxs-lookup"><span data-stu-id="cb23b-239">C# Modifier</span></span>|<span data-ttu-id="cb23b-240">定義</span><span class="sxs-lookup"><span data-stu-id="cb23b-240">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="cb23b-241">虛擬</span><span class="sxs-lookup"><span data-stu-id="cb23b-241">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="cb23b-242">允許在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-242">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="cb23b-243">override</span><span class="sxs-lookup"><span data-stu-id="cb23b-243">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="cb23b-244">覆寫在基底類別中定義的虛擬 (可覆寫) 成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-244">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="cb23b-245">abstract</span><span class="sxs-lookup"><span data-stu-id="cb23b-245">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="cb23b-246">要求在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-246">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="cb23b-247">new 修飾詞</span><span class="sxs-lookup"><span data-stu-id="cb23b-247">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="cb23b-248">隱藏繼承自基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="cb23b-248">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a> <span data-ttu-id="cb23b-249">介面</span><span class="sxs-lookup"><span data-stu-id="cb23b-249">Interfaces</span></span>

<span data-ttu-id="cb23b-250">介面就像類別，可定義屬性、方法和事件集。</span><span class="sxs-lookup"><span data-stu-id="cb23b-250">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="cb23b-251">但與類別不同的是，介面並不提供實作。</span><span class="sxs-lookup"><span data-stu-id="cb23b-251">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="cb23b-252">介面是由類別實作，並定義為與類別不同的實體。</span><span class="sxs-lookup"><span data-stu-id="cb23b-252">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="cb23b-253">介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。</span><span class="sxs-lookup"><span data-stu-id="cb23b-253">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="cb23b-254">若要定義介面：</span><span class="sxs-lookup"><span data-stu-id="cb23b-254">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="cb23b-255">若要在類別中實作介面：</span><span class="sxs-lookup"><span data-stu-id="cb23b-255">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="cb23b-256">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-256">For more information, see:</span></span>

[<span data-ttu-id="cb23b-257">介面</span><span class="sxs-lookup"><span data-stu-id="cb23b-257">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

[<span data-ttu-id="cb23b-258">interface</span><span class="sxs-lookup"><span data-stu-id="cb23b-258">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)

## <a name="Generics"></a> <span data-ttu-id="cb23b-259">泛型</span><span class="sxs-lookup"><span data-stu-id="cb23b-259">Generics</span></span>

<span data-ttu-id="cb23b-260">.NET Framework 中的類別、結構、介面和方法可以包括「型別參數」，這些參數會定義可儲存或使用之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="cb23b-260">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="cb23b-261">泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="cb23b-261">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="cb23b-262">若要定義泛型類別：</span><span class="sxs-lookup"><span data-stu-id="cb23b-262">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="cb23b-263">若要建立泛型類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="cb23b-263">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="cb23b-264">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-264">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-265">泛型</span><span class="sxs-lookup"><span data-stu-id="cb23b-265">Generics</span></span>](~/docs/standard/generics/index.md)

- [<span data-ttu-id="cb23b-266">泛型</span><span class="sxs-lookup"><span data-stu-id="cb23b-266">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

## <a name="Delegates"></a> <span data-ttu-id="cb23b-267">委派</span><span class="sxs-lookup"><span data-stu-id="cb23b-267">Delegates</span></span>

<span data-ttu-id="cb23b-268">「委派」是定義方法簽章的類型，可以提供任何具有相容簽章之方法的參考。</span><span class="sxs-lookup"><span data-stu-id="cb23b-268">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="cb23b-269">您可以透過委派叫用 (Invoke) 或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-269">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="cb23b-270">委派可以用來將方法當做引數傳遞給其他方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-270">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="cb23b-271">事件處理常式就是透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="cb23b-271">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="cb23b-272">如需使用委派處理事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="cb23b-272">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="cb23b-273">若要建立委派：</span><span class="sxs-lookup"><span data-stu-id="cb23b-273">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="cb23b-274">若要建立與委派所指定簽章相符之方法的參考：</span><span class="sxs-lookup"><span data-stu-id="cb23b-274">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
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

<span data-ttu-id="cb23b-275">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="cb23b-275">For more information, see:</span></span>

- [<span data-ttu-id="cb23b-276">委派</span><span class="sxs-lookup"><span data-stu-id="cb23b-276">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

- [<span data-ttu-id="cb23b-277">Delegate - 委派</span><span class="sxs-lookup"><span data-stu-id="cb23b-277">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)

## <a name="see-also"></a><span data-ttu-id="cb23b-278">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb23b-278">See also</span></span>

- [<span data-ttu-id="cb23b-279">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="cb23b-279">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
