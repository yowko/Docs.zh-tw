---
title: "結構和類別 (Visual Basic) |Microsoft 文件"
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
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c6874192a09db9ff5f247274247630d0bfa05ea3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="5999b-102">結構和類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5999b-102">Structures and Classes (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5999b-103">統一的語法結構和類別，因為這兩個實體支援的大部分相同的功能。</span><span class="sxs-lookup"><span data-stu-id="5999b-103"> unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="5999b-104">不過，還有結構和類別間的差異。</span><span class="sxs-lookup"><span data-stu-id="5999b-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="5999b-105">類別具有的優點是參考型別，傳遞參考會比將它的資料結構變數傳遞更有效率。</span><span class="sxs-lookup"><span data-stu-id="5999b-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="5999b-106">相反地，結構不需要全域堆積上的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="5999b-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="5999b-107">您無法從結構繼承，因為結構應該僅適用於不需要擴充的物件。</span><span class="sxs-lookup"><span data-stu-id="5999b-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="5999b-108">當您想要建立的物件有小型執行個體的大小，並納入類別與結構的效能特性，請使用結構。</span><span class="sxs-lookup"><span data-stu-id="5999b-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="5999b-109">相似之處</span><span class="sxs-lookup"><span data-stu-id="5999b-109">Similarities</span></span>  
 <span data-ttu-id="5999b-110">結構和類別是在下列方面類似︰</span><span class="sxs-lookup"><span data-stu-id="5999b-110">Structures and classes are similar in the following respects:</span></span>  
  
-   <span data-ttu-id="5999b-111">兩者都是*容器*型別，也就是說它們包含做為成員的其他類型。</span><span class="sxs-lookup"><span data-stu-id="5999b-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
-   <span data-ttu-id="5999b-112">兩者都有成員，可以包含建構函式、 方法、 屬性、 欄位、 常數、 列舉型別、 事件和事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5999b-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="5999b-113">不過，請勿混淆與宣告這些成員*項目*的結構。</span><span class="sxs-lookup"><span data-stu-id="5999b-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
-   <span data-ttu-id="5999b-114">兩者的成員都有各自的存取層級。</span><span class="sxs-lookup"><span data-stu-id="5999b-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="5999b-115">例如，可以宣告一個成員`Public`，另一個`Private`。</span><span class="sxs-lookup"><span data-stu-id="5999b-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
-   <span data-ttu-id="5999b-116">兩者都可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="5999b-116">Both can implement interfaces.</span></span>  
  
-   <span data-ttu-id="5999b-117">兩者都可以有共用的建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="5999b-117">Both can have shared constructors, with or without parameters.</span></span>  
  
-   <span data-ttu-id="5999b-118">兩者都可以公開*預設屬性*，可提供屬性採用一個以上的參數。</span><span class="sxs-lookup"><span data-stu-id="5999b-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
-   <span data-ttu-id="5999b-119">兩者都可以宣告和引發事件，而且兩者都可以宣告委派。</span><span class="sxs-lookup"><span data-stu-id="5999b-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="5999b-120">差異</span><span class="sxs-lookup"><span data-stu-id="5999b-120">Differences</span></span>  
 <span data-ttu-id="5999b-121">結構和類別，差異如下︰</span><span class="sxs-lookup"><span data-stu-id="5999b-121">Structures and classes differ in the following particulars:</span></span>  
  
-   <span data-ttu-id="5999b-122">結構是*實值型別的*; 類別是*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="5999b-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="5999b-123">結構類型的變數包含結構的資料，而不是未包含的資料做為類別類型的參考。</span><span class="sxs-lookup"><span data-stu-id="5999b-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
-   <span data-ttu-id="5999b-124">結構會使用堆疊配置。類別會使用堆積配置。</span><span class="sxs-lookup"><span data-stu-id="5999b-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
-   <span data-ttu-id="5999b-125">所有的結構項目都`Public`依預設，類別變數和常數是`Private`根據預設，其他類別成員時`Public`預設。</span><span class="sxs-lookup"><span data-stu-id="5999b-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="5999b-126">類別成員的這個行為可提供與 Visual Basic 6.0 系統的預設值的相容性。</span><span class="sxs-lookup"><span data-stu-id="5999b-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
-   <span data-ttu-id="5999b-127">結構必須至少一個非共用變數或非共用、 非自訂事件項目。類別可以完全空白。</span><span class="sxs-lookup"><span data-stu-id="5999b-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
-   <span data-ttu-id="5999b-128">結構項目不能宣告為`Protected`; 可以類別成員。</span><span class="sxs-lookup"><span data-stu-id="5999b-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
-   <span data-ttu-id="5999b-129">結構的程序可以處理事件，才[共用](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`程序，並只透過的方式來[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 類別中的任何程序可以處理事件，使用[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)關鍵字或`AddHandler`陳述式。</span><span class="sxs-lookup"><span data-stu-id="5999b-129">A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="5999b-130">如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5999b-130">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
-   <span data-ttu-id="5999b-131">結構變數宣告不能指定初始設定式或初始陣列的大小。可以類別變數的宣告。</span><span class="sxs-lookup"><span data-stu-id="5999b-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
-   <span data-ttu-id="5999b-132">結構隱含繼承自<xref:System.ValueType?displayProperty=fullName>類別，並與任何其他類型; 無法繼承類別可以繼承自任何類別或類別以外<xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5999b-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=fullName> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=fullName>.</span></span>  
  
-   <span data-ttu-id="5999b-133">結構是無法繼承。類別是。</span><span class="sxs-lookup"><span data-stu-id="5999b-133">Structures are not inheritable; classes are.</span></span>  
  
-   <span data-ttu-id="5999b-134">結構會永遠不會終止，因此 common language runtime (CLR) 永遠不會呼叫<xref:System.Object.Finalize%2A>方法上的任何結構; 類別會由記憶體回收行程 (GC)，它會呼叫終止<xref:System.Object.Finalize%2A>上時偵測到沒有剩餘的作用中參考的類別。</xref:System.Object.Finalize%2A> </xref:System.Object.Finalize%2A></span><span class="sxs-lookup"><span data-stu-id="5999b-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
-   <span data-ttu-id="5999b-135">結構不需要建構函式。類別會執行。</span><span class="sxs-lookup"><span data-stu-id="5999b-135">A structure does not require a constructor; a class does.</span></span>  
  
-   <span data-ttu-id="5999b-136">結構可以具有非共用的建構函式才會顯示參數。類別可以讓他們無論有參數。</span><span class="sxs-lookup"><span data-stu-id="5999b-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="5999b-137">每個結構具有不含參數的隱含公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="5999b-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="5999b-138">這個建構函式會初始化成為其預設值結構的所有資料項目。</span><span class="sxs-lookup"><span data-stu-id="5999b-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="5999b-139">您無法重新定義此行為。</span><span class="sxs-lookup"><span data-stu-id="5999b-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="5999b-140">執行個體和變數</span><span class="sxs-lookup"><span data-stu-id="5999b-140">Instances and Variables</span></span>  
 <span data-ttu-id="5999b-141">結構是實值型別，因為每個結構變數會永久繫結到個別的結構執行個體。</span><span class="sxs-lookup"><span data-stu-id="5999b-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="5999b-142">但類別是參考型別，而且物件變數可以參考各種類別執行個體在不同的時間。</span><span class="sxs-lookup"><span data-stu-id="5999b-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="5999b-143">這項區別會以下列方式影響結構和類別的使用方式︰</span><span class="sxs-lookup"><span data-stu-id="5999b-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
-   <span data-ttu-id="5999b-144">**初始化。**</span><span class="sxs-lookup"><span data-stu-id="5999b-144">**Initialization.**</span></span> <span data-ttu-id="5999b-145">結構變數隱含地包含使用結構的無參數建構函式的元素初始化。</span><span class="sxs-lookup"><span data-stu-id="5999b-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="5999b-146">因此，`Dim s As struct1`相當於`Dim s As struct1 = New struct1()`。</span><span class="sxs-lookup"><span data-stu-id="5999b-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
-   <span data-ttu-id="5999b-147">**指派變數。**</span><span class="sxs-lookup"><span data-stu-id="5999b-147">**Assigning Variables.**</span></span> <span data-ttu-id="5999b-148">當您將一個結構變數指派給另一個，或將結構執行個體傳遞至程序引數時，目前的值的所有變數的項目會複製到新的結構。</span><span class="sxs-lookup"><span data-stu-id="5999b-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="5999b-149">當您將一個物件變數指派給另一個，或將物件變數傳遞至程序時，只會複製參考指標。</span><span class="sxs-lookup"><span data-stu-id="5999b-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
-   <span data-ttu-id="5999b-150">**指派執行任何動作。**</span><span class="sxs-lookup"><span data-stu-id="5999b-150">**Assigning Nothing.**</span></span> <span data-ttu-id="5999b-151">您可以將值指派[Nothing](../../../../visual-basic/language-reference/nothing.md)結構變數，但執行個體仍可繼續與變數相關聯。</span><span class="sxs-lookup"><span data-stu-id="5999b-151">You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="5999b-152">您仍可以呼叫其方法及存取資料元素，但藉由指派的變數項目都會重新初始化。</span><span class="sxs-lookup"><span data-stu-id="5999b-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="5999b-153">相反地，如果您將物件變數設定為`Nothing`中斷關聯從任何類別執行個體，您無法透過變數存取任何成員，直到您指派給它的另一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5999b-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
-   <span data-ttu-id="5999b-154">**多個執行個體。**</span><span class="sxs-lookup"><span data-stu-id="5999b-154">**Multiple Instances.**</span></span> <span data-ttu-id="5999b-155">物件變數可以有不同的類別執行個體指派給不同的時間和數個物件變數可以參考相同的類別執行個體在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="5999b-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="5999b-156">您對類別成員的值的變更會影響當透過指向相同的執行個體的另一個變數來存取這些成員。</span><span class="sxs-lookup"><span data-stu-id="5999b-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="5999b-157">不過，結構項目，是放在自己的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5999b-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="5999b-158">其值的變更不會反映在任何其他結構變數，即使是在相同的其他執行個體`Structure`宣告。</span><span class="sxs-lookup"><span data-stu-id="5999b-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
-   <span data-ttu-id="5999b-159">**相等。**</span><span class="sxs-lookup"><span data-stu-id="5999b-159">**Equality.**</span></span> <span data-ttu-id="5999b-160">必須與項目依項目測試執行的兩個結構相等測試。</span><span class="sxs-lookup"><span data-stu-id="5999b-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="5999b-161">可以使用比較兩個物件變數<xref:System.Object.Equals%2A>方法。</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="5999b-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="5999b-162"><xref:System.Object.Equals%2A>表示兩個變數是否指向相同的執行個體。</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="5999b-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5999b-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5999b-163">See Also</span></span>  
 <span data-ttu-id="5999b-164">[資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="5999b-164">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="5999b-165"> [複合資料型別](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="5999b-165"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="5999b-166"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="5999b-166"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="5999b-167"> [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="5999b-167"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="5999b-168"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="5999b-168"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="5999b-169"> [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span><span class="sxs-lookup"><span data-stu-id="5999b-169"> [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span></span>  
<span data-ttu-id="5999b-170"> [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="5999b-170"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
