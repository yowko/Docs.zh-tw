---
title: Module 陳述式
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
ms.openlocfilehash: 24a27ba41f5ac889f2f2725a2852368a4292a6fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404446"
---
# <a name="module-statement"></a><span data-ttu-id="5d839-102">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d839-102">Module Statement</span></span>

<span data-ttu-id="5d839-103">宣告模組的名稱，並引進模組所組成之變數、屬性、事件和程式的定義。</span><span class="sxs-lookup"><span data-stu-id="5d839-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d839-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d839-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="5d839-105">組件</span><span class="sxs-lookup"><span data-stu-id="5d839-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="5d839-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5d839-106">Optional.</span></span> <span data-ttu-id="5d839-107">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-107">See [Attribute List](attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="5d839-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5d839-108">Optional.</span></span> <span data-ttu-id="5d839-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="5d839-109">Can be one of the following:</span></span>

- [<span data-ttu-id="5d839-110">公開</span><span class="sxs-lookup"><span data-stu-id="5d839-110">Public</span></span>](../modifiers/public.md)

- [<span data-ttu-id="5d839-111">給</span><span class="sxs-lookup"><span data-stu-id="5d839-111">Friend</span></span>](../modifiers/friend.md)

<span data-ttu-id="5d839-112">請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-112">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="5d839-113">必要。</span><span class="sxs-lookup"><span data-stu-id="5d839-113">Required.</span></span> <span data-ttu-id="5d839-114">此模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5d839-114">Name of this module.</span></span> <span data-ttu-id="5d839-115">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-115">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="5d839-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5d839-116">Optional.</span></span> <span data-ttu-id="5d839-117">定義此模組之變數、屬性、事件、程式和巢狀型別的語句。</span><span class="sxs-lookup"><span data-stu-id="5d839-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="5d839-118">結束 `Module` 定義。</span><span class="sxs-lookup"><span data-stu-id="5d839-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d839-119">備註</span><span class="sxs-lookup"><span data-stu-id="5d839-119">Remarks</span></span>

<span data-ttu-id="5d839-120">`Module`語句會定義其命名空間中可用的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5d839-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="5d839-121">*模組*（有時稱為*標準模組*）類似于類別，但有一些重要的區別。</span><span class="sxs-lookup"><span data-stu-id="5d839-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="5d839-122">每個模組只有一個實例，不需要建立或指派給變數。</span><span class="sxs-lookup"><span data-stu-id="5d839-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="5d839-123">模組不支援繼承或執行介面。</span><span class="sxs-lookup"><span data-stu-id="5d839-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="5d839-124">請注意，模組不是類別或結構所用的*型*別，您無法宣告程式設計專案來擁有模組的資料型別。</span><span class="sxs-lookup"><span data-stu-id="5d839-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="5d839-125">您 `Module` 只能在命名空間層級上使用。</span><span class="sxs-lookup"><span data-stu-id="5d839-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="5d839-126">這表示模組的宣告*內容*必須是原始程式檔或命名空間，而且不能是類別、結構、模組、介面、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="5d839-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="5d839-127">您不能將模組放在另一個模組中，或在任何類型內。</span><span class="sxs-lookup"><span data-stu-id="5d839-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="5d839-128">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-128">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="5d839-129">模組與您的程式具有相同的存留期。</span><span class="sxs-lookup"><span data-stu-id="5d839-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="5d839-130">因為其成員都是 `Shared` ，所以其存留期也會等於程式的存留期間。</span><span class="sxs-lookup"><span data-stu-id="5d839-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="5d839-131">模組預設為[Friend](../modifiers/friend.md)存取。</span><span class="sxs-lookup"><span data-stu-id="5d839-131">Modules default to [Friend](../modifiers/friend.md) access.</span></span> <span data-ttu-id="5d839-132">您可以使用存取修飾詞來調整其存取層級。</span><span class="sxs-lookup"><span data-stu-id="5d839-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="5d839-133">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-133">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="5d839-134">模組的所有成員都是隱含的 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="5d839-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="5d839-135">類別和模組</span><span class="sxs-lookup"><span data-stu-id="5d839-135">Classes and Modules</span></span>

<span data-ttu-id="5d839-136">這些元素有許多相似之處，但也有一些重要的差異。</span><span class="sxs-lookup"><span data-stu-id="5d839-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="5d839-137">**庫.**</span><span class="sxs-lookup"><span data-stu-id="5d839-137">**Terminology.**</span></span> <span data-ttu-id="5d839-138">舊版的 Visual Basic 會辨識兩種類型的模組：*類別模組*（cls 檔）和*標準模組*（bas 檔案）。</span><span class="sxs-lookup"><span data-stu-id="5d839-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="5d839-139">目前的版本會分別呼叫這些*類別*和*模組*。</span><span class="sxs-lookup"><span data-stu-id="5d839-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="5d839-140">**共用成員。**</span><span class="sxs-lookup"><span data-stu-id="5d839-140">**Shared Members.**</span></span> <span data-ttu-id="5d839-141">您可以控制類別的成員是否為共用或實例成員。</span><span class="sxs-lookup"><span data-stu-id="5d839-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="5d839-142">**物件方向。**</span><span class="sxs-lookup"><span data-stu-id="5d839-142">**Object Orientation.**</span></span> <span data-ttu-id="5d839-143">類別是物件導向，但模組則不是。</span><span class="sxs-lookup"><span data-stu-id="5d839-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="5d839-144">因此，只有類別可以具現化為物件。</span><span class="sxs-lookup"><span data-stu-id="5d839-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="5d839-145">如需詳細資訊，請參閱[物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-145">For more information, see [Objects and Classes](../../programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="5d839-146">規則</span><span class="sxs-lookup"><span data-stu-id="5d839-146">Rules</span></span>

- <span data-ttu-id="5d839-147">**修改.**</span><span class="sxs-lookup"><span data-stu-id="5d839-147">**Modifiers.**</span></span> <span data-ttu-id="5d839-148">所有模組成員都是隱含[共用](../modifiers/shared.md)的。</span><span class="sxs-lookup"><span data-stu-id="5d839-148">All module members are implicitly [Shared](../modifiers/shared.md).</span></span> <span data-ttu-id="5d839-149">您不能在宣告 `Shared` 成員時使用關鍵字，而且也不能改變任何成員的共用狀態。</span><span class="sxs-lookup"><span data-stu-id="5d839-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="5d839-150">**繼承性.**</span><span class="sxs-lookup"><span data-stu-id="5d839-150">**Inheritance.**</span></span> <span data-ttu-id="5d839-151">模組無法繼承自所有模組所繼承之以外的任何類型 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="5d839-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="5d839-152">特別是一個模組無法繼承自另一個模組。</span><span class="sxs-lookup"><span data-stu-id="5d839-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="5d839-153">您不能在模組定義中使用[Inherits 語句](inherits-statement.md)，即使指定了亦然 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="5d839-153">You cannot use the [Inherits Statement](inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="5d839-154">**Default 屬性。**</span><span class="sxs-lookup"><span data-stu-id="5d839-154">**Default Property.**</span></span> <span data-ttu-id="5d839-155">您不能在模組中定義任何預設屬性。</span><span class="sxs-lookup"><span data-stu-id="5d839-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="5d839-156">如需詳細資訊，請參閱[Default](../modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-156">For more information, see [Default](../modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="5d839-157">行為</span><span class="sxs-lookup"><span data-stu-id="5d839-157">Behavior</span></span>

- <span data-ttu-id="5d839-158">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="5d839-158">**Access Level.**</span></span> <span data-ttu-id="5d839-159">在模組中，您可以使用自己的存取層級來宣告每個成員。</span><span class="sxs-lookup"><span data-stu-id="5d839-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="5d839-160">模組成員預設為[公用](../modifiers/public.md)存取，但變數和常數除外，預設為[私](../modifiers/private.md)用存取。</span><span class="sxs-lookup"><span data-stu-id="5d839-160">Module members default to [Public](../modifiers/public.md) access, except variables and constants, which default to [Private](../modifiers/private.md) access.</span></span> <span data-ttu-id="5d839-161">當模組的存取權高於其中一個成員時，會優先使用指定的模組存取層級。</span><span class="sxs-lookup"><span data-stu-id="5d839-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="5d839-162">**範圍.**</span><span class="sxs-lookup"><span data-stu-id="5d839-162">**Scope.**</span></span> <span data-ttu-id="5d839-163">模組在整個命名空間的範圍內。</span><span class="sxs-lookup"><span data-stu-id="5d839-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="5d839-164">每個模組成員的範圍都是整個模組。</span><span class="sxs-lookup"><span data-stu-id="5d839-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="5d839-165">請注意，所有成員都會經歷*型別提升*，使其範圍升級為包含模組的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5d839-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="5d839-166">如需詳細資訊，請參閱[型別提升](../../programming-guide/language-features/declared-elements/type-promotion.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-166">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="5d839-167">**加.**</span><span class="sxs-lookup"><span data-stu-id="5d839-167">**Qualification.**</span></span> <span data-ttu-id="5d839-168">專案中可以有多個模組，而且可以在兩個或多個模組中宣告具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="5d839-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="5d839-169">不過，如果參考來自于該模組之外，則您必須使用適當的模組名稱來限定這類成員的任何參考。</span><span class="sxs-lookup"><span data-stu-id="5d839-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="5d839-170">如需詳細資訊，請參閱 [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d839-170">For more information, see [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d839-171">範例</span><span class="sxs-lookup"><span data-stu-id="5d839-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="5d839-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d839-172">See also</span></span>

- [<span data-ttu-id="5d839-173">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d839-173">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="5d839-174">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d839-174">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="5d839-175">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d839-175">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="5d839-176">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="5d839-176">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="5d839-177">Property Statement</span><span class="sxs-lookup"><span data-stu-id="5d839-177">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="5d839-178">型別提升</span><span class="sxs-lookup"><span data-stu-id="5d839-178">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
