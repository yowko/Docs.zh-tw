---
title: 結構與類別
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: d252d9216a9b825ad0663a5779d7ce7f81fa9011
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393568"
---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="81557-102">結構和類別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81557-102">Structures and Classes (Visual Basic)</span></span>
<span data-ttu-id="81557-103">Visual Basic 會將結構和類別的語法統一，而且這兩個實體都支援相同的大部分功能。</span><span class="sxs-lookup"><span data-stu-id="81557-103">Visual Basic unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="81557-104">不過，結構與類別之間也有重要的差異。</span><span class="sxs-lookup"><span data-stu-id="81557-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="81557-105">類別的優點是參考型別，傳遞參考比傳遞結構變數及其所有資料更有效率。</span><span class="sxs-lookup"><span data-stu-id="81557-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="81557-106">另一方面，結構不需要在全域堆積上配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="81557-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="81557-107">因為您無法從結構繼承，所以結構應該僅用於不需要擴充的物件。</span><span class="sxs-lookup"><span data-stu-id="81557-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="81557-108">當您想要建立的物件具有小型實例大小時，請使用結構，並將類別與結構的效能特性納入考慮。</span><span class="sxs-lookup"><span data-stu-id="81557-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="81557-109">相似</span><span class="sxs-lookup"><span data-stu-id="81557-109">Similarities</span></span>  
 <span data-ttu-id="81557-110">結構和類別在下列方面很類似：</span><span class="sxs-lookup"><span data-stu-id="81557-110">Structures and classes are similar in the following respects:</span></span>  
  
- <span data-ttu-id="81557-111">兩者都是*容器*類型，這表示它們包含其他類型做為成員。</span><span class="sxs-lookup"><span data-stu-id="81557-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
- <span data-ttu-id="81557-112">兩者都有成員，其中可以包含函數、方法、屬性、欄位、常數、列舉、事件和事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="81557-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="81557-113">不過，請不要將這些成員與結構的宣告*元素*混淆。</span><span class="sxs-lookup"><span data-stu-id="81557-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
- <span data-ttu-id="81557-114">兩者的成員可以具有個人化的存取層級。</span><span class="sxs-lookup"><span data-stu-id="81557-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="81557-115">例如，一個成員可以宣告，另一個則是 `Public` `Private` 。</span><span class="sxs-lookup"><span data-stu-id="81557-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
- <span data-ttu-id="81557-116">兩者都可以執行介面。</span><span class="sxs-lookup"><span data-stu-id="81557-116">Both can implement interfaces.</span></span>  
  
- <span data-ttu-id="81557-117">兩者都可以有共用的處理函式，以及或不含參數。</span><span class="sxs-lookup"><span data-stu-id="81557-117">Both can have shared constructors, with or without parameters.</span></span>  
  
- <span data-ttu-id="81557-118">這兩者都可以公開*預設屬性*，前提是該屬性至少接受一個參數。</span><span class="sxs-lookup"><span data-stu-id="81557-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
- <span data-ttu-id="81557-119">兩者都可以宣告和引發事件，而且兩者都可以宣告委派。</span><span class="sxs-lookup"><span data-stu-id="81557-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="81557-120">差異</span><span class="sxs-lookup"><span data-stu-id="81557-120">Differences</span></span>  
 <span data-ttu-id="81557-121">結構和類別在下列細節方面有所不同：</span><span class="sxs-lookup"><span data-stu-id="81557-121">Structures and classes differ in the following particulars:</span></span>  
  
- <span data-ttu-id="81557-122">結構是實*數值型別*;類別是*參考型別*。</span><span class="sxs-lookup"><span data-stu-id="81557-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="81557-123">結構類型的變數包含結構的資料，而不是包含資料的參考做為類別類型。</span><span class="sxs-lookup"><span data-stu-id="81557-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
- <span data-ttu-id="81557-124">結構使用堆疊配置;類別會使用堆積配置。</span><span class="sxs-lookup"><span data-stu-id="81557-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
- <span data-ttu-id="81557-125">所有結構專案 `Public` 預設為; 類別變數和常數預設為 `Private` ，其他類別成員則 `Public` 預設為。</span><span class="sxs-lookup"><span data-stu-id="81557-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="81557-126">類別成員的這個行為會提供與 Visual Basic 6.0 系統預設值的相容性。</span><span class="sxs-lookup"><span data-stu-id="81557-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
- <span data-ttu-id="81557-127">結構必須至少有一個非共用的變數或非共用的 noncustom 事件元素;類別可以完全空白。</span><span class="sxs-lookup"><span data-stu-id="81557-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
- <span data-ttu-id="81557-128">結構元素不能宣告為 `Protected` ; 類別成員可以。</span><span class="sxs-lookup"><span data-stu-id="81557-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
- <span data-ttu-id="81557-129">結構程式只能處理事件（如果它是共用程式[Shared](../../../language-reference/modifiers/shared.md) `Sub` ），而且只能透過[AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)來處理; 任何類別程式都可以使用 handle 關鍵字或語句來處理[Handles](../../../language-reference/statements/handles-clause.md)事件 `AddHandler` 。</span><span class="sxs-lookup"><span data-stu-id="81557-129">A structure procedure can handle events only if it is a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="81557-130">如需詳細資訊，請參閱[事件](../events/index.md)。</span><span class="sxs-lookup"><span data-stu-id="81557-130">For more information, see [Events](../events/index.md).</span></span>  
  
- <span data-ttu-id="81557-131">結構變數宣告不能指定陣列的初始化運算式或初始大小;類別變數宣告可以。</span><span class="sxs-lookup"><span data-stu-id="81557-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
- <span data-ttu-id="81557-132">結構會隱含繼承自 <xref:System.ValueType?displayProperty=nameWithType> 類別，而且無法繼承自任何其他類型; 類別可以繼承自以外的任何類別或類別 <xref:System.ValueType?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="81557-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=nameWithType> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="81557-133">結構不可繼承;類別為。</span><span class="sxs-lookup"><span data-stu-id="81557-133">Structures are not inheritable; classes are.</span></span>  
  
- <span data-ttu-id="81557-134">結構永遠不會終止，因此 common language runtime （CLR）永遠不會 <xref:System.Object.Finalize%2A> 在任何結構上呼叫方法; 類別會由垃圾收集行程（GC）終止， <xref:System.Object.Finalize%2A> 當它偵測到沒有任何使用中的參考時，就會在類別上呼叫。</span><span class="sxs-lookup"><span data-stu-id="81557-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
- <span data-ttu-id="81557-135">結構不需要使用函數，類別會執行。</span><span class="sxs-lookup"><span data-stu-id="81557-135">A structure does not require a constructor; a class does.</span></span>  
  
- <span data-ttu-id="81557-136">結構只有在接受參數時，才可以有非共用的函式;類別可以有或不使用參數。</span><span class="sxs-lookup"><span data-stu-id="81557-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="81557-137">每個結構都有一個不含參數的隱含公用函數。</span><span class="sxs-lookup"><span data-stu-id="81557-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="81557-138">此函式會將所有結構的資料元素初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="81557-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="81557-139">您無法重新定義此行為。</span><span class="sxs-lookup"><span data-stu-id="81557-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="81557-140">實例和變數</span><span class="sxs-lookup"><span data-stu-id="81557-140">Instances and Variables</span></span>  
 <span data-ttu-id="81557-141">因為結構是實值型別，所以每個結構變數都會永久系結至個別的結構實例。</span><span class="sxs-lookup"><span data-stu-id="81557-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="81557-142">但是類別是參考型別，而物件變數可以在不同的時間參考各種類別實例。</span><span class="sxs-lookup"><span data-stu-id="81557-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="81557-143">這項區別會以下列方式影響您對結構和類別的使用：</span><span class="sxs-lookup"><span data-stu-id="81557-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
- <span data-ttu-id="81557-144">**初始.**</span><span class="sxs-lookup"><span data-stu-id="81557-144">**Initialization.**</span></span> <span data-ttu-id="81557-145">結構變數會使用結構的無參數的函式，隱含地包含初始化元素。</span><span class="sxs-lookup"><span data-stu-id="81557-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="81557-146">因此， `Dim s As struct1` 相當於 `Dim s As struct1 = New struct1()` 。</span><span class="sxs-lookup"><span data-stu-id="81557-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
- <span data-ttu-id="81557-147">**指派變數。**</span><span class="sxs-lookup"><span data-stu-id="81557-147">**Assigning Variables.**</span></span> <span data-ttu-id="81557-148">當您將某個結構變數指派給另一個，或將結構實例傳遞給程式引數時，所有變數元素的目前值都會複製到新的結構。</span><span class="sxs-lookup"><span data-stu-id="81557-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="81557-149">當您將某個物件變數指派給另一個，或將物件變數傳遞至程式時，只會複製參考指標。</span><span class="sxs-lookup"><span data-stu-id="81557-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
- <span data-ttu-id="81557-150">**不指派任何內容。**</span><span class="sxs-lookup"><span data-stu-id="81557-150">**Assigning Nothing.**</span></span> <span data-ttu-id="81557-151">您可以將值 [[無](../../../language-reference/nothing.md)] 指派給結構變數，但是實例會繼續與變數相關聯。</span><span class="sxs-lookup"><span data-stu-id="81557-151">You can assign the value [Nothing](../../../language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="81557-152">您仍然可以呼叫其方法並存取其資料元素，雖然指派會重新初始化變數元素。</span><span class="sxs-lookup"><span data-stu-id="81557-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="81557-153">相反地，如果您將物件變數設為 `Nothing` ，則會中斷其與任何類別實例的關聯，而且您無法透過變數存取任何成員，除非您將另一個實例指派給它。</span><span class="sxs-lookup"><span data-stu-id="81557-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
- <span data-ttu-id="81557-154">**多個實例。**</span><span class="sxs-lookup"><span data-stu-id="81557-154">**Multiple Instances.**</span></span> <span data-ttu-id="81557-155">物件變數可以在不同時間指派不同的類別實例，而且有數個物件變數可以同時參考相同的類別實例。</span><span class="sxs-lookup"><span data-stu-id="81557-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="81557-156">當您對類別成員的值所做的變更，會在透過指向相同實例的另一個變數存取時，影響這些成員。</span><span class="sxs-lookup"><span data-stu-id="81557-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="81557-157">不過，結構專案會隔離在自己的實例中。</span><span class="sxs-lookup"><span data-stu-id="81557-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="81557-158">對其值所做的變更不會反映在其他任何結構變數中，即使在相同宣告的其他實例中也一樣 `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="81557-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
- <span data-ttu-id="81557-159">**等效.**</span><span class="sxs-lookup"><span data-stu-id="81557-159">**Equality.**</span></span> <span data-ttu-id="81557-160">兩個結構的相等測試必須以元素 by 元素測試來執行。</span><span class="sxs-lookup"><span data-stu-id="81557-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="81557-161">您可以使用方法來比較兩個物件變數 <xref:System.Object.Equals%2A> 。</span><span class="sxs-lookup"><span data-stu-id="81557-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="81557-162"><xref:System.Object.Equals%2A>指出兩個變數是否指向相同的實例。</span><span class="sxs-lookup"><span data-stu-id="81557-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81557-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81557-163">See also</span></span>

- [<span data-ttu-id="81557-164">資料類型</span><span class="sxs-lookup"><span data-stu-id="81557-164">Data Types</span></span>](index.md)
- [<span data-ttu-id="81557-165">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="81557-165">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="81557-166">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="81557-166">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="81557-167">結構</span><span class="sxs-lookup"><span data-stu-id="81557-167">Structures</span></span>](structures.md)
- [<span data-ttu-id="81557-168">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="81557-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="81557-169">結構與其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="81557-169">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="81557-170">物件和類別</span><span class="sxs-lookup"><span data-stu-id="81557-170">Objects and Classes</span></span>](../objects-and-classes/index.md)
