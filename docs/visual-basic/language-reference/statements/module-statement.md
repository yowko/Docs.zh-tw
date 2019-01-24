---
title: Module 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 0503292dca81ef7b249b391f54c0aba2bba2cb10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524178"
---
# <a name="module-statement"></a><span data-ttu-id="e55dc-102">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="e55dc-102">Module Statement</span></span>
<span data-ttu-id="e55dc-103">宣告模組的名稱，並引進變數、 屬性、 事件和組成模組的程序的定義。</span><span class="sxs-lookup"><span data-stu-id="e55dc-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="e55dc-104">Syntax</span></span>  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="e55dc-105">組件</span><span class="sxs-lookup"><span data-stu-id="e55dc-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="e55dc-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e55dc-106">Optional.</span></span> <span data-ttu-id="e55dc-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="e55dc-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e55dc-108">Optional.</span></span> <span data-ttu-id="e55dc-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="e55dc-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="e55dc-110">Public</span><span class="sxs-lookup"><span data-stu-id="e55dc-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [<span data-ttu-id="e55dc-111">Friend</span><span class="sxs-lookup"><span data-stu-id="e55dc-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="e55dc-112">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="e55dc-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="e55dc-113">Required.</span></span> <span data-ttu-id="e55dc-114">此模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="e55dc-114">Name of this module.</span></span> <span data-ttu-id="e55dc-115">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="e55dc-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e55dc-116">Optional.</span></span> <span data-ttu-id="e55dc-117">定義的變數、 屬性、 事件、 程序和巢狀型別，此模組的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e55dc-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="e55dc-118">終止`Module`定義。</span><span class="sxs-lookup"><span data-stu-id="e55dc-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e55dc-119">備註</span><span class="sxs-lookup"><span data-stu-id="e55dc-119">Remarks</span></span>  
 <span data-ttu-id="e55dc-120">A`Module`陳述式會定義可在其命名空間的參考型別。</span><span class="sxs-lookup"><span data-stu-id="e55dc-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="e55dc-121">A*模組*(有時也稱為*標準模組*) 類似的類別，但有一些重要的差別。</span><span class="sxs-lookup"><span data-stu-id="e55dc-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="e55dc-122">每個模組都有一個執行個體，並不需要建立或指派給變數。</span><span class="sxs-lookup"><span data-stu-id="e55dc-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="e55dc-123">模組不支援繼承或實作介面。</span><span class="sxs-lookup"><span data-stu-id="e55dc-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="e55dc-124">請注意，模組不是*型別*意思是類別或結構，您不能宣告為具有模組的資料類型的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="e55dc-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="e55dc-125">您可以使用`Module`只能在命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="e55dc-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="e55dc-126">這表示*宣告內容*的模組必須是原始程式檔或命名空間，而且不得類別、 結構、 模組、 介面、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="e55dc-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="e55dc-127">您無法巢狀在另一個模組，或任何類型內的模組。</span><span class="sxs-lookup"><span data-stu-id="e55dc-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="e55dc-128">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="e55dc-129">模組具有相同的存留期，為您的程式。</span><span class="sxs-lookup"><span data-stu-id="e55dc-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="e55dc-130">因為它的成員全部都`Shared`，它們也有相同的程式的存留期。</span><span class="sxs-lookup"><span data-stu-id="e55dc-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="e55dc-131">模組預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。</span><span class="sxs-lookup"><span data-stu-id="e55dc-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="e55dc-132">您可以調整它們的存取層級，使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="e55dc-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="e55dc-133">如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="e55dc-134">模組的所有成員都是隱含`Shared`。</span><span class="sxs-lookup"><span data-stu-id="e55dc-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="e55dc-135">類別和模組</span><span class="sxs-lookup"><span data-stu-id="e55dc-135">Classes and Modules</span></span>  
 <span data-ttu-id="e55dc-136">這些項目有許多相似之處，但有一些重要的差異。</span><span class="sxs-lookup"><span data-stu-id="e55dc-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
-   <span data-ttu-id="e55dc-137">**術語。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-137">**Terminology.**</span></span> <span data-ttu-id="e55dc-138">舊版的 Visual Basic 會辨識兩種模組類型：*類別的模組*（.cls 檔案） 和*標準模組*（.bas 檔案）。</span><span class="sxs-lookup"><span data-stu-id="e55dc-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="e55dc-139">目前的版本會呼叫這些*類別*並*模組*分別。</span><span class="sxs-lookup"><span data-stu-id="e55dc-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
-   <span data-ttu-id="e55dc-140">**共用的成員。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-140">**Shared Members.**</span></span> <span data-ttu-id="e55dc-141">您可以控制類別的成員是否共用，或執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="e55dc-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
-   <span data-ttu-id="e55dc-142">**物件導向。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-142">**Object Orientation.**</span></span> <span data-ttu-id="e55dc-143">類別是物件導向，但模組不是。</span><span class="sxs-lookup"><span data-stu-id="e55dc-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="e55dc-144">因此唯一的類別可以具現化為物件。</span><span class="sxs-lookup"><span data-stu-id="e55dc-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="e55dc-145">如需詳細資訊，請參閱 <<c0> [ 物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e55dc-146">規則</span><span class="sxs-lookup"><span data-stu-id="e55dc-146">Rules</span></span>  
  
-   <span data-ttu-id="e55dc-147">**修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-147">**Modifiers.**</span></span> <span data-ttu-id="e55dc-148">模組的所有成員都是隱含[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="e55dc-149">您無法使用`Shared`關鍵字宣告成員，而且您無法改變任何成員的共用的狀態。</span><span class="sxs-lookup"><span data-stu-id="e55dc-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
-   <span data-ttu-id="e55dc-150">**繼承**：</span><span class="sxs-lookup"><span data-stu-id="e55dc-150">**Inheritance.**</span></span> <span data-ttu-id="e55dc-151">模組無法而非繼承自任何型別<xref:System.Object>，繼承的所有模組。</span><span class="sxs-lookup"><span data-stu-id="e55dc-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="e55dc-152">特別是，一個模組無法繼承自另一個。</span><span class="sxs-lookup"><span data-stu-id="e55dc-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="e55dc-153">您無法使用[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)在模組定義中，甚至指定<xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="e55dc-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="e55dc-154">**預設屬性。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-154">**Default Property.**</span></span> <span data-ttu-id="e55dc-155">您無法在模組中定義任何預設屬性。</span><span class="sxs-lookup"><span data-stu-id="e55dc-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="e55dc-156">如需詳細資訊，請參閱 <<c0> [ 預設](../../../visual-basic/language-reference/modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="e55dc-157">行為</span><span class="sxs-lookup"><span data-stu-id="e55dc-157">Behavior</span></span>  
  
-   <span data-ttu-id="e55dc-158">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-158">**Access Level.**</span></span> <span data-ttu-id="e55dc-159">在模組內，您可以宣告具有它自己的存取層級的每個成員。</span><span class="sxs-lookup"><span data-stu-id="e55dc-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="e55dc-160">模組成員預設為[公開金鑰](../../../visual-basic/language-reference/modifiers/public.md)變數和常數，除了存取哪些預設[私人](../../../visual-basic/language-reference/modifiers/private.md)存取。</span><span class="sxs-lookup"><span data-stu-id="e55dc-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="e55dc-161">當模組有限制存取比多個成員時，指定的模組的存取層級的優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="e55dc-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
-   <span data-ttu-id="e55dc-162">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-162">**Scope.**</span></span> <span data-ttu-id="e55dc-163">模組是在其命名空間的範圍中。</span><span class="sxs-lookup"><span data-stu-id="e55dc-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="e55dc-164">每個模組成員的範圍是整個模組。</span><span class="sxs-lookup"><span data-stu-id="e55dc-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="e55dc-165">請注意，所有成員都進行*類型提升*，因而導致其升級為包含模組的命名空間的範圍。</span><span class="sxs-lookup"><span data-stu-id="e55dc-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="e55dc-166">如需詳細資訊，請參閱 <<c0> [ 型別提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
-   <span data-ttu-id="e55dc-167">**限定性條件。**</span><span class="sxs-lookup"><span data-stu-id="e55dc-167">**Qualification.**</span></span> <span data-ttu-id="e55dc-168">您可以在專案中，有多個模組，您可以宣告具有相同名稱在兩個或多個模組中的成員。</span><span class="sxs-lookup"><span data-stu-id="e55dc-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="e55dc-169">不過，您必須限定這類成員的適當的模組名稱的任何參考，如果參考是從該模組外。</span><span class="sxs-lookup"><span data-stu-id="e55dc-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="e55dc-170">如需詳細資訊，請參閱 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="e55dc-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e55dc-171">範例</span><span class="sxs-lookup"><span data-stu-id="e55dc-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e55dc-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e55dc-172">See also</span></span>
- [<span data-ttu-id="e55dc-173">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="e55dc-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="e55dc-174">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="e55dc-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="e55dc-175">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="e55dc-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="e55dc-176">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="e55dc-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="e55dc-177">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="e55dc-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e55dc-178">型別提升</span><span class="sxs-lookup"><span data-stu-id="e55dc-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
