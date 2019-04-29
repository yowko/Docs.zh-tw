---
title: 結構和類別 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3635729705520518d4c950f8a79da7d1249285bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751068"
---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="07d91-102">結構和類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07d91-102">Structures and Classes (Visual Basic)</span></span>
<span data-ttu-id="07d91-103">Visual Basic 統一的語法結構和類別，因為這兩個實體支援的大部分相同的功能。</span><span class="sxs-lookup"><span data-stu-id="07d91-103">Visual Basic unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="07d91-104">不過，還有結構和類別的重要差異。</span><span class="sxs-lookup"><span data-stu-id="07d91-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="07d91-105">類別具有的優點是參考型別，將參考傳遞的效率高於傳遞結構的變數，它的所有資料。</span><span class="sxs-lookup"><span data-stu-id="07d91-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="07d91-106">相反地，結構不需要全域堆積上的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="07d91-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="07d91-107">因為您無法從結構繼承，所以結構應該僅適用於不需要擴充的物件。</span><span class="sxs-lookup"><span data-stu-id="07d91-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="07d91-108">當您想要建立的物件具有小型執行個體的大小，並考慮類別與結構的效能特性，請使用結構。</span><span class="sxs-lookup"><span data-stu-id="07d91-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="07d91-109">相似之處</span><span class="sxs-lookup"><span data-stu-id="07d91-109">Similarities</span></span>  
 <span data-ttu-id="07d91-110">結構和類別是在下列方面類似：</span><span class="sxs-lookup"><span data-stu-id="07d91-110">Structures and classes are similar in the following respects:</span></span>  
  
- <span data-ttu-id="07d91-111">兩者都*容器*類型，這表示它們包含為成員的其他型別。</span><span class="sxs-lookup"><span data-stu-id="07d91-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
- <span data-ttu-id="07d91-112">兩者都有建構函式、 方法、 屬性、 欄位、 常數、 列舉型別、 事件和事件處理常式可以包含的成員。</span><span class="sxs-lookup"><span data-stu-id="07d91-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="07d91-113">不過，不會混淆與宣告這些成員*項目*的結構。</span><span class="sxs-lookup"><span data-stu-id="07d91-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
- <span data-ttu-id="07d91-114">兩者的成員都有各自的存取層級。</span><span class="sxs-lookup"><span data-stu-id="07d91-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="07d91-115">例如，可以宣告一個成員`Public`是另一個`Private`。</span><span class="sxs-lookup"><span data-stu-id="07d91-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
- <span data-ttu-id="07d91-116">兩者都可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="07d91-116">Both can implement interfaces.</span></span>  
  
- <span data-ttu-id="07d91-117">兩者都可以有共用的建構函式，使用或不含參數。</span><span class="sxs-lookup"><span data-stu-id="07d91-117">Both can have shared constructors, with or without parameters.</span></span>  
  
- <span data-ttu-id="07d91-118">兩者都可以公開*屬性預設*，前提是屬性會採用至少一個參數。</span><span class="sxs-lookup"><span data-stu-id="07d91-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
- <span data-ttu-id="07d91-119">兩者都可以宣告和引發事件，而兩者都可以宣告委派。</span><span class="sxs-lookup"><span data-stu-id="07d91-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="07d91-120">差異</span><span class="sxs-lookup"><span data-stu-id="07d91-120">Differences</span></span>  
 <span data-ttu-id="07d91-121">結構和類別的差異如下：</span><span class="sxs-lookup"><span data-stu-id="07d91-121">Structures and classes differ in the following particulars:</span></span>  
  
- <span data-ttu-id="07d91-122">結構*實值型別*; 類別是*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="07d91-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="07d91-123">結構類型的變數包含的結構資料，而不是未包含的資料做為類別類型的參考。</span><span class="sxs-lookup"><span data-stu-id="07d91-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
- <span data-ttu-id="07d91-124">結構會使用堆疊配置;類別會使用堆積配置。</span><span class="sxs-lookup"><span data-stu-id="07d91-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
- <span data-ttu-id="07d91-125">所有的結構項目都`Public`根據預設，類別變數和常數`Private`根據預設，其他類別成員時`Public`預設。</span><span class="sxs-lookup"><span data-stu-id="07d91-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="07d91-126">類別成員的此行為可提供與 Visual Basic 6.0 系統的預設值的相容性。</span><span class="sxs-lookup"><span data-stu-id="07d91-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
- <span data-ttu-id="07d91-127">結構必須有至少一個非共用變數，或將非共用，非自訂事件項目;類別可以是完全空白的。</span><span class="sxs-lookup"><span data-stu-id="07d91-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
- <span data-ttu-id="07d91-128">結構項目不可以宣告為`Protected`; 類別的成員可以。</span><span class="sxs-lookup"><span data-stu-id="07d91-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
- <span data-ttu-id="07d91-129">結構的程序可以處理事件時才[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`程序，並只利用[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md); 類別中的任何程序可以處理事件，使用任一[會處理](../../../../visual-basic/language-reference/statements/handles-clause.md)關鍵字或`AddHandler`陳述式。</span><span class="sxs-lookup"><span data-stu-id="07d91-129">A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="07d91-130">如需詳細資訊，請參閱[事件](../../../../visual-basic/programming-guide/language-features/events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="07d91-130">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
- <span data-ttu-id="07d91-131">結構變數宣告不能指定初始設定式或陣列; 的初始大小可以類別變數的宣告。</span><span class="sxs-lookup"><span data-stu-id="07d91-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
- <span data-ttu-id="07d91-132">結構會隱含地繼承自<xref:System.ValueType?displayProperty=nameWithType>類別，並無法繼承自任何其他型別，而非類別繼承自任何類別或類別<xref:System.ValueType?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="07d91-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=nameWithType> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="07d91-133">結構是無法繼承;類別是。</span><span class="sxs-lookup"><span data-stu-id="07d91-133">Structures are not inheritable; classes are.</span></span>  
  
- <span data-ttu-id="07d91-134">結構永遠不會終止，因此 common language runtime (CLR) 永遠不會呼叫<xref:System.Object.Finalize%2A>上的任何結構; 方法類別會由記憶體回收行程 (GC)，它會呼叫終止<xref:System.Object.Finalize%2A>上時偵測到沒有作用中參考的類別剩餘的。</span><span class="sxs-lookup"><span data-stu-id="07d91-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
- <span data-ttu-id="07d91-135">結構不需要建構函式類別會執行。</span><span class="sxs-lookup"><span data-stu-id="07d91-135">A structure does not require a constructor; a class does.</span></span>  
  
- <span data-ttu-id="07d91-136">結構可以具有非共用的建構函式才會顯示參數;類別可以讓它們使用或不加任何參數。</span><span class="sxs-lookup"><span data-stu-id="07d91-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="07d91-137">每個結構會有不含參數的隱含公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="07d91-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="07d91-138">這個建構函式會初始化為其預設值的所有結構的資料元素。</span><span class="sxs-lookup"><span data-stu-id="07d91-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="07d91-139">您無法重新定義此行為。</span><span class="sxs-lookup"><span data-stu-id="07d91-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="07d91-140">執行個體與變數</span><span class="sxs-lookup"><span data-stu-id="07d91-140">Instances and Variables</span></span>  
 <span data-ttu-id="07d91-141">因為結構是實值型別，則每個結構變數是永久繫結至個別的結構執行個體中。</span><span class="sxs-lookup"><span data-stu-id="07d91-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="07d91-142">類別是參考型別，但物件變數時，可以參考到各種不同的類別執行個體上，在不同的時間。</span><span class="sxs-lookup"><span data-stu-id="07d91-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="07d91-143">這項區別會以下列方式影響結構和類別的使用方式：</span><span class="sxs-lookup"><span data-stu-id="07d91-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
- <span data-ttu-id="07d91-144">**初始化。**</span><span class="sxs-lookup"><span data-stu-id="07d91-144">**Initialization.**</span></span> <span data-ttu-id="07d91-145">結構變數隱含包含項目使用該結構的無參數建構函式的初始化。</span><span class="sxs-lookup"><span data-stu-id="07d91-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="07d91-146">因此，`Dim s As struct1`相當於`Dim s As struct1 = New struct1()`。</span><span class="sxs-lookup"><span data-stu-id="07d91-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
- <span data-ttu-id="07d91-147">**指派變數。**</span><span class="sxs-lookup"><span data-stu-id="07d91-147">**Assigning Variables.**</span></span> <span data-ttu-id="07d91-148">當您將一個結構變數指派給另一個，或結構執行個體傳遞給程序引數時，就會將目前值的所有變數的項目複製到新的結構。</span><span class="sxs-lookup"><span data-stu-id="07d91-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="07d91-149">當您將一個物件變數指派給另一個，或傳遞至程序的物件變數時，只會複製參考指標。</span><span class="sxs-lookup"><span data-stu-id="07d91-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
- <span data-ttu-id="07d91-150">**指派執行任何動作。**</span><span class="sxs-lookup"><span data-stu-id="07d91-150">**Assigning Nothing.**</span></span> <span data-ttu-id="07d91-151">您可以將值指派[Nothing](../../../../visual-basic/language-reference/nothing.md)結構變數，但執行個體將繼續與變數相關聯。</span><span class="sxs-lookup"><span data-stu-id="07d91-151">You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="07d91-152">您仍然可以呼叫其方法，並存取其資料元素，但變數的項目會藉由指派而重新初始化。</span><span class="sxs-lookup"><span data-stu-id="07d91-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="07d91-153">相反地，如果您設定物件變數`Nothing`中斷任何類別執行個體中，且您無法透過變數存取的任何成員，直到您指派給它的另一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="07d91-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
- <span data-ttu-id="07d91-154">**多個執行個體。**</span><span class="sxs-lookup"><span data-stu-id="07d91-154">**Multiple Instances.**</span></span> <span data-ttu-id="07d91-155">物件變數可以有不同的類別執行個體指派給它，在不同的時間和數個物件變數時，可以參考相同的類別執行個體上，在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="07d91-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="07d91-156">您對類別成員的值變更會影響時透過指向相同的執行個體的另一個變數來存取這些成員。</span><span class="sxs-lookup"><span data-stu-id="07d91-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="07d91-157">不過，結構項目，都隔離在自己的執行個體。</span><span class="sxs-lookup"><span data-stu-id="07d91-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="07d91-158">其值的變更不會反映在任何其他結構變數，即使是在相同的其他執行個體`Structure`宣告。</span><span class="sxs-lookup"><span data-stu-id="07d91-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
- <span data-ttu-id="07d91-159">**相等。**</span><span class="sxs-lookup"><span data-stu-id="07d91-159">**Equality.**</span></span> <span data-ttu-id="07d91-160">與項目依項目測試必須執行兩個結構的等號比較測試。</span><span class="sxs-lookup"><span data-stu-id="07d91-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="07d91-161">可以比較兩個物件變數，使用<xref:System.Object.Equals%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="07d91-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="07d91-162"><xref:System.Object.Equals%2A> 指出兩個變數是否指向相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="07d91-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d91-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07d91-163">See also</span></span>

- [<span data-ttu-id="07d91-164">資料類型</span><span class="sxs-lookup"><span data-stu-id="07d91-164">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="07d91-165">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="07d91-165">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="07d91-166">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="07d91-166">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="07d91-167">結構</span><span class="sxs-lookup"><span data-stu-id="07d91-167">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="07d91-168">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="07d91-168">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="07d91-169">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="07d91-169">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="07d91-170">物件和類別</span><span class="sxs-lookup"><span data-stu-id="07d91-170">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
