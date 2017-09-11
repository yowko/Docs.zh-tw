---
title: "物件導向程式設計 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5491b3bd5a25908194d02063f688a319509bb77
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="ea65f-102">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea65f-102">Object-Oriented Programming (Visual Basic)</span></span>
<span data-ttu-id="ea65f-103">Visual Basic 提供包括封裝、 繼承和多型的物件導向程式設計的完整支援。</span><span class="sxs-lookup"><span data-stu-id="ea65f-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="ea65f-104">*封裝*指一群相關的屬性、 方法和其他成員，視為單一單位或物件。</span><span class="sxs-lookup"><span data-stu-id="ea65f-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="ea65f-105">*繼承*描述來建立新的類別，根據現有類別的能力。</span><span class="sxs-lookup"><span data-stu-id="ea65f-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="ea65f-106">*多型*表示，您就可以有多個可以互換，使用的類別，即使每個類別會以不同的方式實作相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="ea65f-107">本節將說明下列概念：</span><span class="sxs-lookup"><span data-stu-id="ea65f-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="ea65f-108">類別和物件</span><span class="sxs-lookup"><span data-stu-id="ea65f-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="ea65f-109">類別成員</span><span class="sxs-lookup"><span data-stu-id="ea65f-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="ea65f-110">屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="ea65f-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="ea65f-111">方法</span><span class="sxs-lookup"><span data-stu-id="ea65f-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="ea65f-112">建構函式</span><span class="sxs-lookup"><span data-stu-id="ea65f-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="ea65f-113">解構函式</span><span class="sxs-lookup"><span data-stu-id="ea65f-113">Destructors</span></span>](#Destructors)  
  
         [<span data-ttu-id="ea65f-114">事件</span><span class="sxs-lookup"><span data-stu-id="ea65f-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="ea65f-115">巢狀的類別</span><span class="sxs-lookup"><span data-stu-id="ea65f-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="ea65f-116">存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="ea65f-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="ea65f-117">執行個體化類別</span><span class="sxs-lookup"><span data-stu-id="ea65f-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="ea65f-118">共用的類別和成員</span><span class="sxs-lookup"><span data-stu-id="ea65f-118">Shared Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="ea65f-119">匿名類型</span><span class="sxs-lookup"><span data-stu-id="ea65f-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="ea65f-120">繼承</span><span class="sxs-lookup"><span data-stu-id="ea65f-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="ea65f-121">覆寫成員</span><span class="sxs-lookup"><span data-stu-id="ea65f-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="ea65f-122">介面</span><span class="sxs-lookup"><span data-stu-id="ea65f-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="ea65f-123">泛型</span><span class="sxs-lookup"><span data-stu-id="ea65f-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="ea65f-124">委派</span><span class="sxs-lookup"><span data-stu-id="ea65f-124">Delegates</span></span>](#Delegates)  
  
##  <span data-ttu-id="ea65f-125"><a name="Classes"></a>類別和物件</span><span class="sxs-lookup"><span data-stu-id="ea65f-125"><a name="Classes"></a> Classes and Objects</span></span>  
 <span data-ttu-id="ea65f-126">條款*類別*和*物件*有時會用於交換，但事實上，類別說*類型*的物件，而物件則是使用*執行個體*的類別。</span><span class="sxs-lookup"><span data-stu-id="ea65f-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="ea65f-127">因此，建立物件的動作稱為*具現化*。</span><span class="sxs-lookup"><span data-stu-id="ea65f-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="ea65f-128">再以藍圖作比喻，若類別是藍圖，物件就是根據藍圖所蓋的建築物。</span><span class="sxs-lookup"><span data-stu-id="ea65f-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="ea65f-129">若要定義類別：</span><span class="sxs-lookup"><span data-stu-id="ea65f-129">To define a class:</span></span>  
  
```vb  
Class SampleClass  
End Class  
```  
  
 <span data-ttu-id="ea65f-130">Visual Basic 也提供輕量版的類別，稱為*結構*，可在當您需要建立龐大物件陣列，而且不想要使用太多記憶體時，這個。</span><span class="sxs-lookup"><span data-stu-id="ea65f-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="ea65f-131">若要定義結構：</span><span class="sxs-lookup"><span data-stu-id="ea65f-131">To define a structure:</span></span>  
  
```vb  
Structure SampleStructure  
End Structure  
```  
  
 <span data-ttu-id="ea65f-132">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-133">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="ea65f-134">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
###  <span data-ttu-id="ea65f-135"><a name="Members"></a>類別成員</span><span class="sxs-lookup"><span data-stu-id="ea65f-135"><a name="Members"></a> Class Members</span></span>  
 <span data-ttu-id="ea65f-136">每個類別都有不同*類別成員*，包括描述類別資料、 定義類別行為的方法和事件提供不同類別與物件之間通訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea65f-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <span data-ttu-id="ea65f-137"><a name="Properties"></a>屬性和欄位</span><span class="sxs-lookup"><span data-stu-id="ea65f-137"><a name="Properties"></a> Properties and Fields</span></span>  
 <span data-ttu-id="ea65f-138">欄位和屬性表示物件包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="ea65f-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="ea65f-139">欄位就像是變數，可直接讀取或設定。</span><span class="sxs-lookup"><span data-stu-id="ea65f-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="ea65f-140">若要定義欄位：</span><span class="sxs-lookup"><span data-stu-id="ea65f-140">To define a field:</span></span>  
  
```vb  
Class SampleClass  
    Public SampleField As String  
End Class  
```  
  
 <span data-ttu-id="ea65f-141">屬性具有取得和設定程序，讓您更容易控制設定與傳回數值的方式。</span><span class="sxs-lookup"><span data-stu-id="ea65f-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="ea65f-142">Visual Basic 可讓您建立私用欄位來儲存屬性值，或是使用所謂自動實作屬性，建立此欄位，自動在幕後，並提供屬性程序的基本邏輯。</span><span class="sxs-lookup"><span data-stu-id="ea65f-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="ea65f-143">若要定義自動實作屬性：</span><span class="sxs-lookup"><span data-stu-id="ea65f-143">To define an auto-implemented property:</span></span>  
  
```vb  
Class SampleClass  
    Public Property SampleProperty as String  
End Class  
```  
  
 <span data-ttu-id="ea65f-144">如果您需要執行某些額外作業來讀取和寫入屬性值，請定義用來儲存屬性值的欄位，並提供儲存和擷取這個欄位的基本邏輯：</span><span class="sxs-lookup"><span data-stu-id="ea65f-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="ea65f-145">大部分屬性都具有方法或程序，可以設定及取得屬性值。</span><span class="sxs-lookup"><span data-stu-id="ea65f-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="ea65f-146">但是您可以建立唯讀或唯寫屬性來限制不得修改或讀取。</span><span class="sxs-lookup"><span data-stu-id="ea65f-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="ea65f-147">在 Visual Basic 中，您可以使用 `ReadOnly` 和 `WriteOnly` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ea65f-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="ea65f-148">不過，自動實作屬性不得為唯讀或唯寫的。</span><span class="sxs-lookup"><span data-stu-id="ea65f-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="ea65f-149">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-150">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="ea65f-151">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [<span data-ttu-id="ea65f-152">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [<span data-ttu-id="ea65f-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="ea65f-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [<span data-ttu-id="ea65f-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="ea65f-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
####  <span data-ttu-id="ea65f-155"><a name="Methods"></a>方法</span><span class="sxs-lookup"><span data-stu-id="ea65f-155"><a name="Methods"></a> Methods</span></span>  
 <span data-ttu-id="ea65f-156">A*方法*是物件可執行的動作。</span><span class="sxs-lookup"><span data-stu-id="ea65f-156">A *method* is an action that an object can perform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea65f-157">在 Visual Basic 中，有兩個建立方法的方式：如果方法沒有傳回值，即使用 `Sub` 陳述式；如果有傳回值，則使用 `Function` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ea65f-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>  
  
 <span data-ttu-id="ea65f-158">若要定義類別的方法：</span><span class="sxs-lookup"><span data-stu-id="ea65f-158">To define a method of a class:</span></span>  
  
```vb  
Class SampleClass  
    Public Function SampleFunc(ByVal SampleParam As String)  
        ' Add code here  
    End Function  
End Class  
```  
  
 <span data-ttu-id="ea65f-159">類別可以有數種實作方式，或*多載*，不同的參數個數和參數型別中的相同方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="ea65f-160">若要多載方法：</span><span class="sxs-lookup"><span data-stu-id="ea65f-160">To overload a method:</span></span>  
  
```vb  
Overloads Sub Display(ByVal theChar As Char)  
    ' Add code that displays Char data.  
End Sub  
Overloads Sub Display(ByVal theInteger As Integer)  
    ' Add code that displays Integer data.  
End Sub  
```  
  
 <span data-ttu-id="ea65f-161">在多數情況下，您是在類別定義中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="ea65f-162">不過，Visual Basic 也支援*擴充方法*可讓您將方法加入至現有的類別之類別的實際定義之外。</span><span class="sxs-lookup"><span data-stu-id="ea65f-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="ea65f-163">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-163">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-164">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="ea65f-165">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="ea65f-166">多載</span><span class="sxs-lookup"><span data-stu-id="ea65f-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
-   [<span data-ttu-id="ea65f-167">擴充方法</span><span class="sxs-lookup"><span data-stu-id="ea65f-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
  
####  <span data-ttu-id="ea65f-168"><a name="Constructors"></a>建構函式</span><span class="sxs-lookup"><span data-stu-id="ea65f-168"><a name="Constructors"></a> Constructors</span></span>  
 <span data-ttu-id="ea65f-169">建構函式是類別方法，會在建立指定類型的物件時自動執行。</span><span class="sxs-lookup"><span data-stu-id="ea65f-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="ea65f-170">建構函式通常用來初始化新物件的資料成員，</span><span class="sxs-lookup"><span data-stu-id="ea65f-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="ea65f-171">而且只能在建立類別時執行一次。</span><span class="sxs-lookup"><span data-stu-id="ea65f-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="ea65f-172">此外，建構函式中的程式碼永遠會在類別中的任何其他程式碼執行之前執行。</span><span class="sxs-lookup"><span data-stu-id="ea65f-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="ea65f-173">不過，就和其他任何方法一樣，您可以建立多個建構函式多載。</span><span class="sxs-lookup"><span data-stu-id="ea65f-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="ea65f-174">若要定義類別的建構函式：</span><span class="sxs-lookup"><span data-stu-id="ea65f-174">To define a constructor for a class:</span></span>  
  
```vb  
Class SampleClass  
    Sub New(ByVal s As String)  
        // Add code here.  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="ea65f-175">如需詳細資訊，請參閱︰[物件存留期︰ 物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
####  <span data-ttu-id="ea65f-176"><a name="Destructors"></a>解構函式</span><span class="sxs-lookup"><span data-stu-id="ea65f-176"><a name="Destructors"></a> Destructors</span></span>  
 <span data-ttu-id="ea65f-177">解構函式是用來解構類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea65f-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="ea65f-178">在 .NET Framework 中，記憶體回收行程會自動管理應用程式中 Managed 物件的記憶體配置及釋放。</span><span class="sxs-lookup"><span data-stu-id="ea65f-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="ea65f-179">不過，您可能仍然需要解構函式來清除應用程式建立的任何 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="ea65f-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="ea65f-180">一個類別只能有一個解構函式。</span><span class="sxs-lookup"><span data-stu-id="ea65f-180">There can be only one destructor for a class.</span></span>  
  
 <span data-ttu-id="ea65f-181">如需解構函式和在.NET Framework 記憶體回收的詳細資訊，請參閱[回收](../../../standard/garbagecollection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbagecollection/index.md).</span></span>  
  
####  <span data-ttu-id="ea65f-182"><a name="Events"></a>事件</span><span class="sxs-lookup"><span data-stu-id="ea65f-182"><a name="Events"></a> Events</span></span>  
 <span data-ttu-id="ea65f-183">事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="ea65f-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="ea65f-184">傳送 （或引發） 事件的類別稱為*發行者*和接收 （或處理） 事件的類別則稱為*「 訂閱者 」*。</span><span class="sxs-lookup"><span data-stu-id="ea65f-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="ea65f-185">如需事件的詳細資訊，如何引發和處理，請參閱[事件](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-185">For more information about events, how they are raised and handled, see [Events](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).</span></span>  
  
-   <span data-ttu-id="ea65f-186">若要宣告事件，請使用[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
-   <span data-ttu-id="ea65f-187">若要引發事件，請使用[RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
-   <span data-ttu-id="ea65f-188">若要指定事件處理常式以宣告方式，使用[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)陳述式和[處理](../../../visual-basic/language-reference/statements/handles-clause.md)子句。</span><span class="sxs-lookup"><span data-stu-id="ea65f-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>  
  
-   <span data-ttu-id="ea65f-189">若要能夠以動態方式新增、 移除及變更與事件相關聯的事件處理常式，使用[AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)和[RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)搭配[AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>  
  
####  <span data-ttu-id="ea65f-190"><a name="NestedClasses"></a>巢狀的類別</span><span class="sxs-lookup"><span data-stu-id="ea65f-190"><a name="NestedClasses"></a> Nested Classes</span></span>  
 <span data-ttu-id="ea65f-191">在另一個類別中定義的類別稱為*巢狀*。</span><span class="sxs-lookup"><span data-stu-id="ea65f-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="ea65f-192">巢狀類別預設為私用。</span><span class="sxs-lookup"><span data-stu-id="ea65f-192">By default, the nested class is private.</span></span>  
  
```vb  
Class Container  
    Class Nested  
    ' Add code here.  
    End Class  
End Class  
```  
  
 <span data-ttu-id="ea65f-193">若要建立巢狀類別的執行個體，請使用容器類別名稱，後面加上點號，再接著巢狀類別名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea65f-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```vb  
Dim nestedInstance As Container.Nested = New Container.Nested()  
```  
  
###  <span data-ttu-id="ea65f-194"><a name="AccessModifiers"></a>存取修飾詞與存取層級</span><span class="sxs-lookup"><span data-stu-id="ea65f-194"><a name="AccessModifiers"></a> Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="ea65f-195">所有類別和類別成員可以都指定使用提供給其他類別存取層級*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="ea65f-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="ea65f-196">下列為可用的存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="ea65f-196">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="ea65f-197">Visual Basic 修飾詞</span><span class="sxs-lookup"><span data-stu-id="ea65f-197">Visual Basic Modifier</span></span>|<span data-ttu-id="ea65f-198">定義</span><span class="sxs-lookup"><span data-stu-id="ea65f-198">Definition</span></span>|  
|---------------------------|----------------|  
|[<span data-ttu-id="ea65f-199">Public</span><span class="sxs-lookup"><span data-stu-id="ea65f-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="ea65f-200">類型或成員可由相同組件或參考該組件的另一個組件中的任何其他程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="ea65f-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="ea65f-201">Private</span><span class="sxs-lookup"><span data-stu-id="ea65f-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="ea65f-202">類型或成員只能由相同類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="ea65f-202">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="ea65f-203">Protected</span><span class="sxs-lookup"><span data-stu-id="ea65f-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="ea65f-204">類型或成員只能由相同類別中，或是衍生類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="ea65f-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="ea65f-205">Friend</span><span class="sxs-lookup"><span data-stu-id="ea65f-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="ea65f-206">類型或成員可由相同組件中的任何程式碼存取，但是不包括其他組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea65f-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|`Protected Friend`|<span data-ttu-id="ea65f-207">類型或成員可由相同組件中的任何程式碼，或是其他組件中的任何衍生類別存取。</span><span class="sxs-lookup"><span data-stu-id="ea65f-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
  
 <span data-ttu-id="ea65f-208">如需詳細資訊，請參閱[在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-208">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
###  <span data-ttu-id="ea65f-209"><a name="InstantiatingClasses"></a>執行個體化類別</span><span class="sxs-lookup"><span data-stu-id="ea65f-209"><a name="InstantiatingClasses"></a> Instantiating Classes</span></span>  
 <span data-ttu-id="ea65f-210">若要建立物件，您必須將類別執行個體化，或是建立類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea65f-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```vb  
Dim sampleObject as New SampleClass()  
```  
  
 <span data-ttu-id="ea65f-211">將類別執行個體化之後，您就可以將值指派給執行個體的屬性和欄位，並叫用類別方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```vb  
' Set a property value.  
sampleObject.SampleProperty = "Sample String"  
' Call a method.  
sampleObject.SampleMethod()  
```  
  
 <span data-ttu-id="ea65f-212">若要在類別執行個體化期間將值指派給屬性，請使用物件初始設定式：</span><span class="sxs-lookup"><span data-stu-id="ea65f-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```vb  
Dim sampleObject = New SampleClass With   
    {.FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 <span data-ttu-id="ea65f-213">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-213">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-214">New 運算子</span><span class="sxs-lookup"><span data-stu-id="ea65f-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
  
-   [<span data-ttu-id="ea65f-215">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="ea65f-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
  
###  <span data-ttu-id="ea65f-216"><a name="Static"></a>共用的類別和成員</span><span class="sxs-lookup"><span data-stu-id="ea65f-216"><a name="Static"></a> Shared Classes and Members</span></span>  
 <span data-ttu-id="ea65f-217">共用成員是類別的屬性、 程序或共用的所有類別的執行個體的欄位。</span><span class="sxs-lookup"><span data-stu-id="ea65f-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="ea65f-218">若要定義共用的成員︰</span><span class="sxs-lookup"><span data-stu-id="ea65f-218">To define a shared member:</span></span>  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 <span data-ttu-id="ea65f-219">若要存取共用的成員，請使用類別的名稱而不需建立這個類別的物件︰</span><span class="sxs-lookup"><span data-stu-id="ea65f-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 <span data-ttu-id="ea65f-220">在 Visual Basic 中的共用的模組共享僅包含成員，且無法具現化。</span><span class="sxs-lookup"><span data-stu-id="ea65f-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="ea65f-221">共用的成員也無法存取非共用的屬性、 欄位或方法</span><span class="sxs-lookup"><span data-stu-id="ea65f-221">Shared members also cannot access non-shared properties, fields or methods</span></span>  
  
 <span data-ttu-id="ea65f-222">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-222">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-223">Shared</span><span class="sxs-lookup"><span data-stu-id="ea65f-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [<span data-ttu-id="ea65f-224">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
###  <span data-ttu-id="ea65f-225"><a name="AnonymousTypes"></a>匿名型別</span><span class="sxs-lookup"><span data-stu-id="ea65f-225"><a name="AnonymousTypes"></a> Anonymous Types</span></span>  
 <span data-ttu-id="ea65f-226">使用匿名類型建立物件時，您不需要撰寫資料類型的類別定義，</span><span class="sxs-lookup"><span data-stu-id="ea65f-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="ea65f-227">編譯器 (Compiler) 會自動幫您建立類別 (Class)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="ea65f-228">這個類別沒有可使用的名稱，但是包含您在宣告物件時指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea65f-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="ea65f-229">若要建立匿名類型的執行個體：</span><span class="sxs-lookup"><span data-stu-id="ea65f-229">To create an instance of an anonymous type:</span></span>  
  
```vb  
' sampleObject is an instance of a simple anonymous type.  
Dim sampleObject =   
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 <span data-ttu-id="ea65f-230">如需詳細資訊，請參閱︰[匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
##  <span data-ttu-id="ea65f-231"><a name="Inheritance"></a>繼承</span><span class="sxs-lookup"><span data-stu-id="ea65f-231"><a name="Inheritance"></a> Inheritance</span></span>  
 <span data-ttu-id="ea65f-232">繼承可讓您建立新類別以重複使用、擴充和修改其他類別中定義的行為。</span><span class="sxs-lookup"><span data-stu-id="ea65f-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="ea65f-233">其成員都繼承的類別稱為*基底類別*，而繼承這種成員的類別稱為*衍生的類別*。</span><span class="sxs-lookup"><span data-stu-id="ea65f-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="ea65f-234">不過，在 Visual Basic 中的所有類別隱含都繼承自<xref:System.Object>類別來支援.NET 類別階層架構，並為所有類別提供低階服務。</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ea65f-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea65f-235">Visual Basic 不支援多重繼承。</span><span class="sxs-lookup"><span data-stu-id="ea65f-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="ea65f-236">也就是說，您可以指定只有一個基底類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="ea65f-236">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="ea65f-237">若要繼承基底類別：</span><span class="sxs-lookup"><span data-stu-id="ea65f-237">To inherit from a base class:</span></span>  
  
```vb  
Class DerivedClass  
    Inherits BaseClass  
End Class  
```  
  
 <span data-ttu-id="ea65f-238">所有類別預設都可以被繼承。</span><span class="sxs-lookup"><span data-stu-id="ea65f-238">By default all classes can be inherited.</span></span> <span data-ttu-id="ea65f-239">不過，您可以指定類別是否不得當做基底類別，或是建立只能當做基底類別的類別。</span><span class="sxs-lookup"><span data-stu-id="ea65f-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="ea65f-240">若要指定類別不得當做基底類別使用：</span><span class="sxs-lookup"><span data-stu-id="ea65f-240">To specify that a class cannot be used as a base class:</span></span>  
  
```vb  
NotInheritable Class SampleClass  
End Class  
```  
  
 <span data-ttu-id="ea65f-241">若要指定類別只能當做基底類別且無法執行個體化：</span><span class="sxs-lookup"><span data-stu-id="ea65f-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```vb  
MustInherit Class BaseClass  
End Class  
```  
  
 <span data-ttu-id="ea65f-242">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-242">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-243">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
  
-   [<span data-ttu-id="ea65f-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="ea65f-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
  
-   [<span data-ttu-id="ea65f-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="ea65f-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
  
###  <span data-ttu-id="ea65f-246"><a name="Overriding"></a>覆寫成員</span><span class="sxs-lookup"><span data-stu-id="ea65f-246"><a name="Overriding"></a> Overriding Members</span></span>  
 <span data-ttu-id="ea65f-247">衍生類別預設會從其基底類別繼承所有成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="ea65f-248">如果想要變更所繼承成員的行為，您必須覆寫這個成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="ea65f-249">也就是說，您可以定義衍生類別中方法、屬性或事件的新實作。</span><span class="sxs-lookup"><span data-stu-id="ea65f-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="ea65f-250">下列修飾詞是用來控制如何覆寫屬性及方法：</span><span class="sxs-lookup"><span data-stu-id="ea65f-250">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="ea65f-251">Visual Basic 修飾詞</span><span class="sxs-lookup"><span data-stu-id="ea65f-251">Visual Basic Modifier</span></span>|<span data-ttu-id="ea65f-252">定義</span><span class="sxs-lookup"><span data-stu-id="ea65f-252">Definition</span></span>|  
|---------------------------|----------------|  
|[<span data-ttu-id="ea65f-253">Overridable</span><span class="sxs-lookup"><span data-stu-id="ea65f-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="ea65f-254">允許在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-254">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="ea65f-255">Overrides</span><span class="sxs-lookup"><span data-stu-id="ea65f-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="ea65f-256">覆寫在基底類別中定義的虛擬 (可覆寫) 成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="ea65f-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ea65f-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="ea65f-258">防止在繼承的類別中覆寫成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-258">Prevents a member from being overridden in an inheriting class.</span></span>|  
|[<span data-ttu-id="ea65f-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ea65f-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="ea65f-260">要求在衍生類別中覆寫類別成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-260">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="ea65f-261">Shadows</span><span class="sxs-lookup"><span data-stu-id="ea65f-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="ea65f-262">隱藏繼承自基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="ea65f-262">Hides a member inherited from a base class</span></span>|  
  
##  <span data-ttu-id="ea65f-263"><a name="Interfaces"></a>介面</span><span class="sxs-lookup"><span data-stu-id="ea65f-263"><a name="Interfaces"></a> Interfaces</span></span>  
 <span data-ttu-id="ea65f-264">介面就像類別，可定義屬性、方法和事件集。</span><span class="sxs-lookup"><span data-stu-id="ea65f-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="ea65f-265">但與類別不同的是，介面並不提供實作。</span><span class="sxs-lookup"><span data-stu-id="ea65f-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="ea65f-266">介面是由類別實作，並定義為與類別不同的實體。</span><span class="sxs-lookup"><span data-stu-id="ea65f-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="ea65f-267">介面就代表著一種合約，因為實作介面的類別必須完全依介面的定義來實作這個介面的各個方面。</span><span class="sxs-lookup"><span data-stu-id="ea65f-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="ea65f-268">若要定義介面：</span><span class="sxs-lookup"><span data-stu-id="ea65f-268">To define an interface:</span></span>  
  
```vb  
Public Interface ISampleInterface  
    Sub DoSomething()  
End Interface  
```  
  
 <span data-ttu-id="ea65f-269">若要在類別中實作介面：</span><span class="sxs-lookup"><span data-stu-id="ea65f-269">To implement an interface in a class:</span></span>  
  
```vb  
Class SampleClass  
    Implements ISampleInterface  
    Sub DoSomething  
        ' Method implementation.  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="ea65f-270">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-271">介面</span><span class="sxs-lookup"><span data-stu-id="ea65f-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
  
-   [<span data-ttu-id="ea65f-272">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   [<span data-ttu-id="ea65f-273">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
  
##  <span data-ttu-id="ea65f-274"><a name="Generics"></a>泛型</span><span class="sxs-lookup"><span data-stu-id="ea65f-274"><a name="Generics"></a> Generics</span></span>  
 <span data-ttu-id="ea65f-275">類別、 結構、 介面和.NET Framework 中的方法可以包括*型別參數*定義類型的物件，而且可以儲存或使用。</span><span class="sxs-lookup"><span data-stu-id="ea65f-275">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="ea65f-276">泛型最常見的範例是集合，您可以在其中指定要儲存於集合之物件的類型。</span><span class="sxs-lookup"><span data-stu-id="ea65f-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="ea65f-277">若要定義泛型類別：</span><span class="sxs-lookup"><span data-stu-id="ea65f-277">To define a generic class:</span></span>  
  
```vb  
Class SampleGeneric(Of T)  
    Public Field As T  
End Class  
```  
  
 <span data-ttu-id="ea65f-278">若要建立泛型類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="ea65f-278">To create an instance of a generic class:</span></span>  
  
```vb  
Dim sampleObject As New SampleGeneric(Of String)  
sampleObject.Field = "Sample string"  
```  
  
 <span data-ttu-id="ea65f-279">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-279">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-280">泛型</span><span class="sxs-lookup"><span data-stu-id="ea65f-280">Generics</span></span>](https://msdn.microsoft.com/library/ms172192)  
  
-   [<span data-ttu-id="ea65f-281">在 Visual Basic 中的泛型型別</span><span class="sxs-lookup"><span data-stu-id="ea65f-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
  
##  <span data-ttu-id="ea65f-282"><a name="Delegates"></a>委派</span><span class="sxs-lookup"><span data-stu-id="ea65f-282"><a name="Delegates"></a> Delegates</span></span>  
 <span data-ttu-id="ea65f-283">A*委派*是定義方法簽章的類型，而且可以具有相容簽章提供任何方法的參考。</span><span class="sxs-lookup"><span data-stu-id="ea65f-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="ea65f-284">您可以透過委派叫用 (Invoke) 或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="ea65f-285">委派可以用來將方法當做引數傳遞給其他方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-285">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea65f-286">事件處理常式就是透過委派叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="ea65f-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="ea65f-287">如需事件處理中使用委派的詳細資訊，請參閱[事件](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)。</span><span class="sxs-lookup"><span data-stu-id="ea65f-287">For more information about using delegates in event handling, see [Events](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).</span></span>  
  
 <span data-ttu-id="ea65f-288">若要建立委派：</span><span class="sxs-lookup"><span data-stu-id="ea65f-288">To create a delegate:</span></span>  
  
```vb  
Delegate Sub SampleDelegate(ByVal str As String)  
```  
  
 <span data-ttu-id="ea65f-289">若要建立與委派所指定簽章相符之方法的參考：</span><span class="sxs-lookup"><span data-stu-id="ea65f-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="ea65f-290">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="ea65f-290">For more information, see:</span></span>  
  
-   [<span data-ttu-id="ea65f-291">委派</span><span class="sxs-lookup"><span data-stu-id="ea65f-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
  
-   [<span data-ttu-id="ea65f-292">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea65f-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
-   [<span data-ttu-id="ea65f-293">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="ea65f-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea65f-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea65f-294">See Also</span></span>  
 [<span data-ttu-id="ea65f-295">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ea65f-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
