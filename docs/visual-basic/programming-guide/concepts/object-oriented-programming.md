---
title: 物件導向程式設計
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: f7e222cde8ce80d4c52cc8b4b111c576eb4041b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413189"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="4a6bd-102">物件導向程式設計（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4a6bd-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="4a6bd-103">Visual Basic 提供物件導向程式設計的完整支援，包括封裝、繼承和多型。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="4a6bd-104">「封裝」\*\* 指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="4a6bd-105">「繼承」\*\* 則是描述依據現有類別來建立新類別的能力。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="4a6bd-106">「多型」\*\* 指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="4a6bd-107">本節將說明下列概念：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="4a6bd-108">類別與物件</span><span class="sxs-lookup"><span data-stu-id="4a6bd-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="4a6bd-109">類別成員</span><span class="sxs-lookup"><span data-stu-id="4a6bd-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="4a6bd-110">屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="4a6bd-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="4a6bd-111">方法</span><span class="sxs-lookup"><span data-stu-id="4a6bd-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="4a6bd-112">建構函式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="4a6bd-113">解構函式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="4a6bd-114">事件</span><span class="sxs-lookup"><span data-stu-id="4a6bd-114">Events</span></span>](#events)
    - [<span data-ttu-id="4a6bd-115">嵌套類別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="4a6bd-116">存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="4a6bd-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="4a6bd-117">具現化類別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="4a6bd-118">共用類別和成員</span><span class="sxs-lookup"><span data-stu-id="4a6bd-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="4a6bd-119">匿名型別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="4a6bd-120">繼承</span><span class="sxs-lookup"><span data-stu-id="4a6bd-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="4a6bd-121">覆寫成員</span><span class="sxs-lookup"><span data-stu-id="4a6bd-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="4a6bd-122">介面</span><span class="sxs-lookup"><span data-stu-id="4a6bd-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="4a6bd-123">泛型</span><span class="sxs-lookup"><span data-stu-id="4a6bd-123">Generics</span></span>](#generics)
- [<span data-ttu-id="4a6bd-124">委派</span><span class="sxs-lookup"><span data-stu-id="4a6bd-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="4a6bd-125">類別與物件</span><span class="sxs-lookup"><span data-stu-id="4a6bd-125">Classes and objects</span></span>

<span data-ttu-id="4a6bd-126">「類別」\*\* 和「物件」\*\* 有時會交換使用，但事實上，類別說的是物件的「型別」**，而物件則是類別之可使用的「執行個體」**。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="4a6bd-127">因此，建立物件的動作稱為「具現化」\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="4a6bd-128">再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="4a6bd-129">若要定義類別：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="4a6bd-130">Visual Basic 也提供名為「*結構*」的輕量版本，當您需要建立大型物件陣列，而且不想要使用太多記憶體時，這種類別就很有用。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="4a6bd-131">若要定義結構：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="4a6bd-132">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-132">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-133">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-133">Class Statement</span></span>](../../language-reference/statements/class-statement.md)
- [<span data-ttu-id="4a6bd-134">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-134">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="4a6bd-135">類別成員</span><span class="sxs-lookup"><span data-stu-id="4a6bd-135">Class members</span></span>

<span data-ttu-id="4a6bd-136">每個類別都有不同的「類別成員」\*\*，包括描述類別資料的屬性、定義類別行為的方法，以及提供不同類別與物件之間通訊的事件。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="4a6bd-137">屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="4a6bd-137">Properties and fields</span></span>

<span data-ttu-id="4a6bd-138">欄位和屬性表示物件包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="4a6bd-139">欄位就像是變數，可直接讀取或設定。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="4a6bd-140">若要定義欄位：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="4a6bd-141">屬性具有取得和設定程序，讓您更容易控制設定與傳回數值的方式。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="4a6bd-142">Visual Basic 可讓您建立私用欄位來儲存屬性值，或是使用所謂的自動執行屬性，在幕後自動建立此欄位，並提供屬性程式的基本邏輯。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="4a6bd-143">若要定義自動實作屬性：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="4a6bd-144">如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="4a6bd-145">大部分屬性都具有方法或程序，可以設定及取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="4a6bd-146">但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="4a6bd-147">在 Visual Basic 中，您可以使用 `ReadOnly` 和 `WriteOnly` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="4a6bd-148">不過，自動實作的屬性不可以是唯讀或唯寫。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="4a6bd-149">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-149">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-150">Property Statement</span><span class="sxs-lookup"><span data-stu-id="4a6bd-150">Property Statement</span></span>](../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="4a6bd-151">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-151">Get Statement</span></span>](../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="4a6bd-152">Set 語句</span><span class="sxs-lookup"><span data-stu-id="4a6bd-152">Set Statement</span></span>](../../language-reference/statements/set-statement.md)
- [<span data-ttu-id="4a6bd-153">唯讀</span><span class="sxs-lookup"><span data-stu-id="4a6bd-153">ReadOnly</span></span>](../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="4a6bd-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="4a6bd-154">WriteOnly</span></span>](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="4a6bd-155">方法</span><span class="sxs-lookup"><span data-stu-id="4a6bd-155">Methods</span></span>

 <span data-ttu-id="4a6bd-156">「方法」\*\* 是物件可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="4a6bd-157">在 Visual Basic 中，有兩個建立方法的方式：如果方法沒有傳回值，即使用 `Sub` 陳述式；如果有傳回值，則使用 `Function` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="4a6bd-158">若要定義類別的方法：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="4a6bd-159">類別可以有同一個方法的多個實作或「多載」\*\*，但是這些實作的參數個數和參數類型並不相同。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="4a6bd-160">若要多載方法：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="4a6bd-161">在多數情況下，您是在類別定義中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="4a6bd-162">不過，Visual Basic 也支援*擴充方法*，可讓您將方法加入至類別的實際定義之外的現有類別。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="4a6bd-163">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-163">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-164">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-164">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="4a6bd-165">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-165">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4a6bd-166">多載</span><span class="sxs-lookup"><span data-stu-id="4a6bd-166">Overloads</span></span>](../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="4a6bd-167">擴充方法</span><span class="sxs-lookup"><span data-stu-id="4a6bd-167">Extension Methods</span></span>](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="4a6bd-168">建構函式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-168">Constructors</span></span>

<span data-ttu-id="4a6bd-169">建構函式是類別方法，會在建立指定類型的物件時自動執行。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="4a6bd-170">建構函式通常用來初始化新物件的資料成員，</span><span class="sxs-lookup"><span data-stu-id="4a6bd-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="4a6bd-171">而且只能在建立類別時執行一次。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="4a6bd-172">此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="4a6bd-173">不過，就和其他任何方法一樣，您可以建立多個建構函式多載。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="4a6bd-174">若要定義類別的建構函式：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="4a6bd-175">如需詳細資訊，請參閱：[物件存留期：物件的建立和終結方式](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="4a6bd-176">解構函式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-176">Destructors</span></span>

<span data-ttu-id="4a6bd-177">解構函式是用來解構類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="4a6bd-178">在 .NET Framework 中，記憶體回收行程會自動管理應用程式中 Managed 物件的記憶體配置及釋放。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="4a6bd-179">不過，您可能仍然需要解構函式來清除應用程式建立的任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="4a6bd-180">一個類別只能有一個解構函式。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="4a6bd-181">如需 .NET Framework 中之解構函式和記憶體回收的詳細資訊，請參閱[記憶體回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="4a6bd-182">事件</span><span class="sxs-lookup"><span data-stu-id="4a6bd-182">Events</span></span>

<span data-ttu-id="4a6bd-183">事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="4a6bd-184">傳送 (或引發) 事件的類別稱為「發行者」**，而接收 (或處理) 事件的類別則稱為「訂閱者」**。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="4a6bd-185">如需事件的詳細資訊以及如何引發和處理事件，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="4a6bd-186">若要宣告事件，請使用[事件語句](../../language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-186">To declare events, use the [Event Statement](../../language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="4a6bd-187">若要引發事件，請使用[RaiseEvent 語句](../../language-reference/statements/raiseevent-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-187">To raise events, use the [RaiseEvent Statement](../../language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="4a6bd-188">若要使用宣告式方式來指定事件處理常式，請使用[WithEvents](../../language-reference/modifiers/withevents.md)語句和[Handles](../../language-reference/statements/handles-clause.md)子句。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-188">To specify event handlers using a declarative way, use the [WithEvents](../../language-reference/modifiers/withevents.md) statement and the [Handles](../../language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="4a6bd-189">若要能夠動態加入、移除及變更與事件相關聯的事件處理常式，請搭配使用[AddHandler 語句](../../language-reference/statements/addhandler-statement.md)和[RemoveHandler 語句](../../language-reference/statements/removehandler-statement.md)和[AddressOf 運算子](../../language-reference/operators/addressof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="4a6bd-190">嵌套類別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-190">Nested classes</span></span>

<span data-ttu-id="4a6bd-191">在類別中定義的另一個類別即稱為「巢狀」\*\* 類別。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="4a6bd-192">巢狀類別預設為私用。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="4a6bd-193">若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="4a6bd-194">存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="4a6bd-194">Access modifiers and access levels</span></span>

<span data-ttu-id="4a6bd-195">所有類別及類別成員都可以使用「存取修飾詞」\*\*，指定要提供給其他類別的存取層級。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="4a6bd-196">下列為可用的存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="4a6bd-197">Visual Basic 修飾詞</span><span class="sxs-lookup"><span data-stu-id="4a6bd-197">Visual Basic Modifier</span></span>|<span data-ttu-id="4a6bd-198">定義</span><span class="sxs-lookup"><span data-stu-id="4a6bd-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="4a6bd-199">公開</span><span class="sxs-lookup"><span data-stu-id="4a6bd-199">Public</span></span>](../../language-reference/modifiers/public.md)|<span data-ttu-id="4a6bd-200">類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="4a6bd-201">私用</span><span class="sxs-lookup"><span data-stu-id="4a6bd-201">Private</span></span>](../../language-reference/modifiers/private.md)|<span data-ttu-id="4a6bd-202">類型或成員只能由相同類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="4a6bd-203">免受</span><span class="sxs-lookup"><span data-stu-id="4a6bd-203">Protected</span></span>](../../language-reference/modifiers/protected.md)|<span data-ttu-id="4a6bd-204">類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="4a6bd-205">給</span><span class="sxs-lookup"><span data-stu-id="4a6bd-205">Friend</span></span>](../../language-reference/modifiers/friend.md)|<span data-ttu-id="4a6bd-206">類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="4a6bd-207">類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="4a6bd-208">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-208">For more information, see [Access levels in Visual Basic](../language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="4a6bd-209">具現化類別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-209">Instantiating classes</span></span>

<span data-ttu-id="4a6bd-210">若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="4a6bd-211">將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="4a6bd-212">若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="4a6bd-213">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-213">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-214">New 運算子</span><span class="sxs-lookup"><span data-stu-id="4a6bd-214">New Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="4a6bd-215">物件初始設定式：具名和匿名型別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-215">Object Initializers: Named and Anonymous Types</span></span>](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="4a6bd-216">共用類別和成員</span><span class="sxs-lookup"><span data-stu-id="4a6bd-216">Shared classes and members</span></span>

 <span data-ttu-id="4a6bd-217">類別的共用成員是由類別的所有實例共用的屬性、程式或欄位。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="4a6bd-218">若要定義共用成員：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="4a6bd-219">若要存取共用成員，請使用類別的名稱，而不需建立這個類別的物件：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="4a6bd-220">Visual Basic 中的共用模組只有共用成員，無法具現化。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="4a6bd-221">共用成員也無法存取非共用的屬性、欄位或方法</span><span class="sxs-lookup"><span data-stu-id="4a6bd-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="4a6bd-222">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-222">For more information, see:</span></span>

- <span data-ttu-id="4a6bd-223">[共用][](../../language-reference/modifiers/shared.md)</span><span class="sxs-lookup"><span data-stu-id="4a6bd-223">[Shared](../../language-reference/modifiers/shared.md)</span></span>
- [<span data-ttu-id="4a6bd-224">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-224">Module Statement</span></span>](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="4a6bd-225">匿名型別</span><span class="sxs-lookup"><span data-stu-id="4a6bd-225">Anonymous types</span></span>

<span data-ttu-id="4a6bd-226">使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義，</span><span class="sxs-lookup"><span data-stu-id="4a6bd-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="4a6bd-227">編譯器 (Compiler) 會自動幫您建立類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="4a6bd-228">這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="4a6bd-229">若要建立匿名類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="4a6bd-230">如需詳細資訊，請參閱[匿名型別](../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-230">For more information, see: [Anonymous Types](../language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="4a6bd-231">繼承</span><span class="sxs-lookup"><span data-stu-id="4a6bd-231">Inheritance</span></span>

<span data-ttu-id="4a6bd-232">繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="4a6bd-233">成員被繼承的類別稱為「基底類別」**，而繼承這種成員的類別即稱為「衍生類別」**。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="4a6bd-234">不過，Visual Basic 中的所有類別都會隱含繼承自 <xref:System.Object> 支援 .net 類別階層的類別，並為所有類別提供低層級的服務。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="4a6bd-235">Visual Basic 不支援多重繼承。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="4a6bd-236">也就是說，您只能為衍生類別指定一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="4a6bd-237">若要繼承基底類別：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="4a6bd-238">所有類別預設都可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-238">By default all classes can be inherited.</span></span> <span data-ttu-id="4a6bd-239">不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="4a6bd-240">若要指定類別不得當做基底類別使用：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="4a6bd-241">若要指定類別只能當做基底類別且無法執行個體化：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="4a6bd-242">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-242">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-243">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="4a6bd-243">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="4a6bd-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="4a6bd-244">NotInheritable</span></span>](../../language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="4a6bd-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="4a6bd-245">MustInherit</span></span>](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="4a6bd-246">覆寫成員</span><span class="sxs-lookup"><span data-stu-id="4a6bd-246">Overriding members</span></span>

<span data-ttu-id="4a6bd-247">衍生類別預設會從其基底類別繼承所有成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="4a6bd-248">如果想要變更所繼承成員的行為，您必須覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="4a6bd-249">也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="4a6bd-250">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="4a6bd-251">Visual Basic 修飾詞</span><span class="sxs-lookup"><span data-stu-id="4a6bd-251">Visual Basic Modifier</span></span>|<span data-ttu-id="4a6bd-252">定義</span><span class="sxs-lookup"><span data-stu-id="4a6bd-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="4a6bd-253">Overrides</span><span class="sxs-lookup"><span data-stu-id="4a6bd-253">Overridable</span></span>](../../language-reference/modifiers/overridable.md)|<span data-ttu-id="4a6bd-254">允許在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="4a6bd-255">覆寫</span><span class="sxs-lookup"><span data-stu-id="4a6bd-255">Overrides</span></span>](../../language-reference/modifiers/overrides.md)|<span data-ttu-id="4a6bd-256">覆寫在基底類別中定義的虛擬 (可覆寫) 成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="4a6bd-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4a6bd-257">NotOverridable</span></span>](../../language-reference/modifiers/notoverridable.md)|<span data-ttu-id="4a6bd-258">防止在繼承的類別中覆寫成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="4a6bd-259">New</span><span class="sxs-lookup"><span data-stu-id="4a6bd-259">MustOverride</span></span>](../../language-reference/modifiers/mustoverride.md)|<span data-ttu-id="4a6bd-260">要求在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="4a6bd-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="4a6bd-261">Shadows</span></span>](../../language-reference/modifiers/shadows.md)|<span data-ttu-id="4a6bd-262">隱藏繼承自基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="4a6bd-263">介面</span><span class="sxs-lookup"><span data-stu-id="4a6bd-263">Interfaces</span></span>

<span data-ttu-id="4a6bd-264">介面就像類別，可定義屬性、方法和事件集。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="4a6bd-265">但與類別不同的是，介面並不提供實作。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="4a6bd-266">介面是由類別實作，並定義為與類別不同的實體。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="4a6bd-267">介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="4a6bd-268">若要定義介面：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="4a6bd-269">若要在類別中實作介面：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="4a6bd-270">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-270">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-271">介面</span><span class="sxs-lookup"><span data-stu-id="4a6bd-271">Interfaces</span></span>](../language-features/interfaces/index.md)
- [<span data-ttu-id="4a6bd-272">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-272">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="4a6bd-273">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-273">Implements Statement</span></span>](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="4a6bd-274">泛型</span><span class="sxs-lookup"><span data-stu-id="4a6bd-274">Generics</span></span>

<span data-ttu-id="4a6bd-275">.NET 中的類別、結構、介面和方法可以包含定義可儲存或使用之物件類型的*類型參數*。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="4a6bd-276">泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="4a6bd-277">若要定義泛型類別：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="4a6bd-278">若要建立泛型類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="4a6bd-279">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-279">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-280">泛型</span><span class="sxs-lookup"><span data-stu-id="4a6bd-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="4a6bd-281">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a6bd-281">Generic Types in Visual Basic</span></span>](../language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="4a6bd-282">委派</span><span class="sxs-lookup"><span data-stu-id="4a6bd-282">Delegates</span></span>

 <span data-ttu-id="4a6bd-283">「委派」\*\* 是定義方法簽章的類型，可以提供任何具有相容簽章之方法的參考。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="4a6bd-284">您可以透過委派叫用 (Invoke) 或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="4a6bd-285">委派可以用來將方法當做引數傳遞給其他方法。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="4a6bd-286">事件處理常式就是透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="4a6bd-287">如需使用委派處理事件的詳細資訊，請參閱[處理和引發事件](../../../standard/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4a6bd-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="4a6bd-288">若要建立委派：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="4a6bd-289">若要建立與委派所指定簽章相符之方法的參考：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="4a6bd-290">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4a6bd-290">For more information, see:</span></span>

- [<span data-ttu-id="4a6bd-291">委派</span><span class="sxs-lookup"><span data-stu-id="4a6bd-291">Delegates</span></span>](../language-features/delegates/index.md)
- [<span data-ttu-id="4a6bd-292">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="4a6bd-292">Delegate Statement</span></span>](../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="4a6bd-293">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="4a6bd-293">AddressOf Operator</span></span>](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="4a6bd-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a6bd-294">See also</span></span>

- [<span data-ttu-id="4a6bd-295">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4a6bd-295">Visual Basic Programming Guide</span></span>](../index.md)
