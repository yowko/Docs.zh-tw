---
title: "物件 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a2a23d02e4ea95e908f97bc7264ee64d6899aee8
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="objects-c-programming-guide"></a><span data-ttu-id="935de-102">物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="935de-102">Objects (C# Programming Guide)</span></span>
<span data-ttu-id="935de-103">類別或結構定義就像是指定型別可以做什麼的藍圖。</span><span class="sxs-lookup"><span data-stu-id="935de-103">A class or struct definition is like a blueprint that specifies what the type can do.</span></span> <span data-ttu-id="935de-104">物件基本上是根據藍圖配置和設定的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="935de-104">An object is basically a block of memory that has been allocated and configured according to the blueprint.</span></span> <span data-ttu-id="935de-105">程式可建立許多同類別的物件。</span><span class="sxs-lookup"><span data-stu-id="935de-105">A program may create many objects of the same class.</span></span> <span data-ttu-id="935de-106">物件也稱為執行個體，可儲存在具名變數或陣列或集合中。</span><span class="sxs-lookup"><span data-stu-id="935de-106">Objects are also called instances, and they can be stored in either a named variable or in an array or collection.</span></span> <span data-ttu-id="935de-107">用戶端程式碼是使用這些變數呼叫方法，並存取物件公用屬性的程式碼。</span><span class="sxs-lookup"><span data-stu-id="935de-107">Client code is the code that uses these variables to call the methods and access the public properties of the object.</span></span> <span data-ttu-id="935de-108">在 C# 之類的物件導向語言中，一般程式包含多個動態互動的物件。</span><span class="sxs-lookup"><span data-stu-id="935de-108">In an object-oriented language such as C#, a typical program consists of multiple objects interacting dynamically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="935de-109">靜態型別的行為會和此處描述的不同。</span><span class="sxs-lookup"><span data-stu-id="935de-109">Static types behave differently than what is described here.</span></span> <span data-ttu-id="935de-110">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="935de-110">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="struct-instances-vs-class-instances"></a><span data-ttu-id="935de-111">結構執行個體與類別執行個體</span><span class="sxs-lookup"><span data-stu-id="935de-111">Struct Instances vs. Class Instances</span></span>  
 <span data-ttu-id="935de-112">因為類別是參考型別，所以類別物件的變數會將參考保留在 Managed 堆積上的物件位址中。</span><span class="sxs-lookup"><span data-stu-id="935de-112">Because classes are reference types, a variable of a class object holds a reference to the address of the object on the managed heap.</span></span> <span data-ttu-id="935de-113">如果同型別的第二個物件指派給第一個物件，則這兩個變數都會參考位於該位址的物件。</span><span class="sxs-lookup"><span data-stu-id="935de-113">If a second object of the same type is assigned to the first object, then both variables refer to the object at that address.</span></span> <span data-ttu-id="935de-114">本主題稍後會詳細討論這一點。</span><span class="sxs-lookup"><span data-stu-id="935de-114">This point is discussed in more detail later in this topic.</span></span>  
  
 <span data-ttu-id="935de-115">使用 [new 運算子](../../../csharp/language-reference/keywords/new-operator.md) 建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="935de-115">Instances of classes are created by using the [new operator](../../../csharp/language-reference/keywords/new-operator.md).</span></span> <span data-ttu-id="935de-116">在下例中，`Person` 是型別，而 `person1` 和 `person 2` 則是該型別的執行個體或物件。</span><span class="sxs-lookup"><span data-stu-id="935de-116">In the following example, `Person` is the type and `person1` and `person 2` are instances, or objects, of that type.</span></span>  
  
 <span data-ttu-id="935de-117">[!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="935de-117">[!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]</span></span>  
  
 <span data-ttu-id="935de-118">因為結構是實值型別，所以結構物件的變數會保留完整物件的複本。</span><span class="sxs-lookup"><span data-stu-id="935de-118">Because structs are value types, a variable of a struct object holds a copy of the entire object.</span></span> <span data-ttu-id="935de-119">結構的執行個體也可以使用 `new` 運算子建立，但這不是必要項目，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="935de-119">Instances of structs can also be created by using the `new` operator, but this is not required, as shown in the following example:</span></span>  
  
 <span data-ttu-id="935de-120">[!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="935de-120">[!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]</span></span>  
  
 <span data-ttu-id="935de-121">`p1` 和 `p2` 的記憶體都配置在執行緒堆疊上。</span><span class="sxs-lookup"><span data-stu-id="935de-121">The memory for both `p1` and `p2` is allocated on the thread stack.</span></span> <span data-ttu-id="935de-122">該記憶體會和其宣告所在的型別或方法一起回收。</span><span class="sxs-lookup"><span data-stu-id="935de-122">That memory is reclaimed along with the type or method in which it is declared.</span></span> <span data-ttu-id="935de-123">這是在指派時複製結構的原因之一。</span><span class="sxs-lookup"><span data-stu-id="935de-123">This is one reason why structs are copied on assignment.</span></span> <span data-ttu-id="935de-124">相較之下，當物件的所有參考都超出範圍時，通用語言執行平台會自動回收為類別執行個體配置的記憶體 (記憶體回收)。</span><span class="sxs-lookup"><span data-stu-id="935de-124">By contrast, the memory that is allocated for a class instance is automatically reclaimed (garbage collected) by the common language runtime when all references to the object have gone out of scope.</span></span> <span data-ttu-id="935de-125">您不可能像在 C++ 中一樣決定性終結類別物件。</span><span class="sxs-lookup"><span data-stu-id="935de-125">It is not possible to deterministically destroy a class object like you can in C++.</span></span> <span data-ttu-id="935de-126">如需 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 記憶體回收的詳細資訊，請參閱[記憶體回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="935de-126">For more information about garbage collection in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="935de-127">通用語言執行平台中，已高度最佳化 Managed 堆積上的記憶體配置和解除配置。</span><span class="sxs-lookup"><span data-stu-id="935de-127">The allocation and deallocation of memory on the managed heap is highly optimized in the common language runtime.</span></span> <span data-ttu-id="935de-128">在大部分情況下，在堆積上配置類別執行個體與在堆疊上配置結構執行個體，效能成本沒有任何重大差異。</span><span class="sxs-lookup"><span data-stu-id="935de-128">In most cases there is no significant difference in the performance cost of allocating a class instance on the heap versus allocating a struct instance on the stack.</span></span>  
  
## <a name="object-identity-vs-value-equality"></a><span data-ttu-id="935de-129">物件識別與實值相等</span><span class="sxs-lookup"><span data-stu-id="935de-129">Object Identity vs. Value Equality</span></span>  
 <span data-ttu-id="935de-130">當您比較兩個物件是否相等時，您必須先區別是否想要知道這兩個變數在記憶體中是否代表相同的物件，或者其欄位的一或多個值是否相等。</span><span class="sxs-lookup"><span data-stu-id="935de-130">When you compare two objects for equality, you must first distinguish whether you want to know whether the two variables represent the same object in memory, or whether the values of one or more of their fields are equivalent.</span></span> <span data-ttu-id="935de-131">如果您打算比較值，就必須考慮物件是實值型別 (結構) 還是參考型別 (類別、委派、陣列) 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="935de-131">If you are intending to compare values, you must consider whether the objects are instances of value types (structs) or reference types (classes, delegates, arrays).</span></span>  
  
-   <span data-ttu-id="935de-132">若要判斷兩個類別執行個體在記憶體中是否參考相同的位置 (表示它們具有相同的「身分識別」)，請使用靜態 <xref:System.Object.Equals%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="935de-132">To determine whether two class instances refer to the same location in memory (which means that they have the same *identity*), use the static <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="935de-133">(<xref:System.Object?displayProperty=fullName> 是所有實值型別和參考型別的隱含基底類別，包括使用者定義的結構和類別。)</span><span class="sxs-lookup"><span data-stu-id="935de-133">(<xref:System.Object?displayProperty=fullName> is the implicit base class for all value types and reference types, including user-defined structs and classes.)</span></span>  
  
-   <span data-ttu-id="935de-134">若要判斷兩個結構執行個體中的執行個體欄位是否有相同的值，請使用 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 方法。</span><span class="sxs-lookup"><span data-stu-id="935de-134">To determine whether the instance fields in two struct instances have the same values, use the <xref:System.ValueType.Equals%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="935de-135">因為所有結構都是隱含繼承 <xref:System.ValueType?displayProperty=fullName>，所以您可以直接在物件上呼叫方法，如以下範例︰</span><span class="sxs-lookup"><span data-stu-id="935de-135">Because all structs implicitly inherit from <xref:System.ValueType?displayProperty=fullName>, you call the method directly on your object as shown in the following example:</span></span>  
  
 <span data-ttu-id="935de-136">[!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="935de-136">[!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]</span></span>  
  
 <span data-ttu-id="935de-137">由於 `Equals` 的 <xref:System.ValueType?displayProperty=fullName> 實作必須能夠判斷結構中有哪些欄位，因此會使用反映。</span><span class="sxs-lookup"><span data-stu-id="935de-137">The <xref:System.ValueType?displayProperty=fullName> implementation of `Equals` uses reflection because it must be able to determine what the fields are in any struct.</span></span> <span data-ttu-id="935de-138">建立您自己的結構時，請覆寫 `Equals` 方法以提供型別專屬的有效相等演算法。</span><span class="sxs-lookup"><span data-stu-id="935de-138">When creating your own structs, override the `Equals` method to provide an efficient equality algorithm that is specific to your type.</span></span>  
  
-   <span data-ttu-id="935de-139">若要判斷兩個類別執行個體中的欄位值是否相等，您或許可以使用 <xref:System.Object.Equals%2A> 方法或 [== 運算子](../../../csharp/language-reference/operators/equality-comparison-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="935de-139">To determine whether the values of the fields in two class instances are equal, you might be able to use the <xref:System.Object.Equals%2A> method or the [== operator](../../../csharp/language-reference/operators/equality-comparison-operator.md).</span></span> <span data-ttu-id="935de-140">但請只有當類別覆寫或多載它們，以提供「相等」表示的型別物件的自訂定義時，才使用它們。</span><span class="sxs-lookup"><span data-stu-id="935de-140">However, only use them if the class has overridden or overloaded them to provide a custom definition of what "equality" means for objects of that type.</span></span> <span data-ttu-id="935de-141">此類別可能也會實作 <xref:System.IEquatable%601> 介面或 <xref:System.Collections.Generic.IEqualityComparer%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="935de-141">The class might also implement the <xref:System.IEquatable%601> interface or the <xref:System.Collections.Generic.IEqualityComparer%601> interface.</span></span> <span data-ttu-id="935de-142">這兩個介面都會提供可用以測試值相等的方法。</span><span class="sxs-lookup"><span data-stu-id="935de-142">Both interfaces provide methods that can be used to test value equality.</span></span> <span data-ttu-id="935de-143">若要設計自己的類別以覆寫 `Equals`，請務必遵循[如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)和 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 所述的指導方針。</span><span class="sxs-lookup"><span data-stu-id="935de-143">When designing your own classes that override `Equals`, make sure to follow the guidelines stated in [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) and <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="935de-144">相關章節</span><span class="sxs-lookup"><span data-stu-id="935de-144">Related Sections</span></span>  
 <span data-ttu-id="935de-145">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="935de-145">For more information:</span></span>  
  
-   [<span data-ttu-id="935de-146">類別</span><span class="sxs-lookup"><span data-stu-id="935de-146">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [<span data-ttu-id="935de-147">結構</span><span class="sxs-lookup"><span data-stu-id="935de-147">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [<span data-ttu-id="935de-148">建構函式</span><span class="sxs-lookup"><span data-stu-id="935de-148">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="935de-149">完成項</span><span class="sxs-lookup"><span data-stu-id="935de-149">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [<span data-ttu-id="935de-150">事件</span><span class="sxs-lookup"><span data-stu-id="935de-150">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="935de-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="935de-151">See Also</span></span>  
 <span data-ttu-id="935de-152">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="935de-152">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="935de-153">[object](../../../csharp/language-reference/keywords/object.md) </span><span class="sxs-lookup"><span data-stu-id="935de-153">[object](../../../csharp/language-reference/keywords/object.md) </span></span>  
 <span data-ttu-id="935de-154">[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="935de-154">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="935de-155">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="935de-155">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="935de-156">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="935de-156">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 <span data-ttu-id="935de-157">[ew 運算子](../../../csharp/language-reference/keywords/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="935de-157">[new Operator](../../../csharp/language-reference/keywords/new-operator.md) </span></span>  
 [<span data-ttu-id="935de-158">一般類型系統</span><span class="sxs-lookup"><span data-stu-id="935de-158">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)

