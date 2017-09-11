---
title: "Property 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
dev_langs:
- VB
helpviewer_keywords:
- Property statement
- default modifier
- property procedures, Property statements
- Property keyword
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: dbd779b4b6a1dd167e8581066b0fbe034cd2d8f2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="property-statement"></a><span data-ttu-id="4acdd-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="4acdd-102">Property Statement</span></span>
<span data-ttu-id="4acdd-103">宣告屬性的名稱，以及用以儲存及擷取屬性值的屬性程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4acdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="4acdd-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4acdd-105">組件</span><span class="sxs-lookup"><span data-stu-id="4acdd-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="4acdd-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-106">Optional.</span></span> <span data-ttu-id="4acdd-107">適用於此屬性的屬性清單或`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="4acdd-108">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="4acdd-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-109">Optional.</span></span> <span data-ttu-id="4acdd-110">指定這個屬性是類別或結構定義所在的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="4acdd-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="4acdd-111">預設屬性不能接受參數，並可以設定和擷取而不指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4acdd-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="4acdd-112">如果您宣告屬性做為`Default`，您不能使用`Private`屬性或其中一個屬性程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="4acdd-113">選擇性在`Property`陳述式和上一個`Get`和`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4acdd-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="4acdd-114">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4acdd-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4acdd-115">Public</span><span class="sxs-lookup"><span data-stu-id="4acdd-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="4acdd-116">Protected</span><span class="sxs-lookup"><span data-stu-id="4acdd-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="4acdd-117">Friend</span><span class="sxs-lookup"><span data-stu-id="4acdd-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="4acdd-118">Private</span><span class="sxs-lookup"><span data-stu-id="4acdd-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="4acdd-119">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-119">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="4acdd-120">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-120">Optional.</span></span> <span data-ttu-id="4acdd-121">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4acdd-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4acdd-122">多載</span><span class="sxs-lookup"><span data-stu-id="4acdd-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="4acdd-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="4acdd-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="4acdd-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="4acdd-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="4acdd-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4acdd-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="4acdd-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4acdd-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="4acdd-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-127">Optional.</span></span> <span data-ttu-id="4acdd-128">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="4acdd-129">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-129">Optional.</span></span> <span data-ttu-id="4acdd-130">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="4acdd-131">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-131">Optional.</span></span> <span data-ttu-id="4acdd-132">請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="4acdd-133">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-133">Optional.</span></span> <span data-ttu-id="4acdd-134">請參閱[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="4acdd-135">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-135">Optional.</span></span> <span data-ttu-id="4acdd-136">請參閱[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="4acdd-137">必要項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-137">Required.</span></span> <span data-ttu-id="4acdd-138">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4acdd-138">Name of the property.</span></span> <span data-ttu-id="4acdd-139">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="4acdd-140">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-140">Optional.</span></span> <span data-ttu-id="4acdd-141">表示這個屬性的參數和可能的額外參數的變數名稱清單`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="4acdd-142">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="4acdd-143">只有在`Option``Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="4acdd-144">這個屬性所傳回之值的資料型別。</span><span class="sxs-lookup"><span data-stu-id="4acdd-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="4acdd-145">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-145">Optional.</span></span> <span data-ttu-id="4acdd-146">表示這個屬性會實作一個或多個屬性，每一個定義中包含這個屬性的類別或結構所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="4acdd-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="4acdd-147">請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="4acdd-148">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="4acdd-149">要實作的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="4acdd-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="4acdd-150">每個 `implementedproperty` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="4acdd-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="4acdd-151">組件</span><span class="sxs-lookup"><span data-stu-id="4acdd-151">Part</span></span>|<span data-ttu-id="4acdd-152">描述</span><span class="sxs-lookup"><span data-stu-id="4acdd-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="4acdd-153">必要項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-153">Required.</span></span> <span data-ttu-id="4acdd-154">這個屬性所實作的介面名稱的包含類別或結構。</span><span class="sxs-lookup"><span data-stu-id="4acdd-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="4acdd-155">必要項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-155">Required.</span></span> <span data-ttu-id="4acdd-156">此屬性定義中的名稱`interface`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="4acdd-157">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-157">Optional.</span></span> <span data-ttu-id="4acdd-158">必要屬性標示為`WriteOnly`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="4acdd-159">啟動`Get`屬性用來傳回屬性值的程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="4acdd-160">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-160">Optional.</span></span> <span data-ttu-id="4acdd-161">在執行陳述式區塊`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="4acdd-162">終止`Get`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="4acdd-163">選擇項。</span><span class="sxs-lookup"><span data-stu-id="4acdd-163">Optional.</span></span> <span data-ttu-id="4acdd-164">必要屬性標示為`ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="4acdd-165">啟動`Set`屬性用來儲存屬性值的程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="4acdd-166">終止`Set`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="4acdd-167">結束這個屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="4acdd-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4acdd-168">備註</span><span class="sxs-lookup"><span data-stu-id="4acdd-168">Remarks</span></span>  
 <span data-ttu-id="4acdd-169">`Property`陳述式會採用屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="4acdd-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="4acdd-170">屬性可以有`Get`程序 （唯讀），`Set`程序 （唯寫） 或這兩個 （讀 / 寫）。</span><span class="sxs-lookup"><span data-stu-id="4acdd-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="4acdd-171">您可以省略`Get`和`Set`程序時使用自動實作的屬性。</span><span class="sxs-lookup"><span data-stu-id="4acdd-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="4acdd-172">如需詳細資訊，請參閱[Auto-Implemented 屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="4acdd-173">您可以使用`Property`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="4acdd-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="4acdd-174">這表示*宣告內容*屬性必須是類別、 結構、 模組或介面，而且不能是原始程式檔、 命名空間、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="4acdd-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="4acdd-175">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="4acdd-176">根據預設，屬性會使用公用存取。</span><span class="sxs-lookup"><span data-stu-id="4acdd-176">By default, properties use public access.</span></span> <span data-ttu-id="4acdd-177">您可以調整屬性的存取層級的存取修飾詞在`Property`陳述式，而且您可以選擇是否要調整其中一個屬性程序更嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="4acdd-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="4acdd-178">Visual Basic 會將傳遞的參數`Set`期間屬性指派的程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="4acdd-179">如果您未提供的參數`Set`，整合式的開發環境 (IDE) 會使用名為的隱含參數`value`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="4acdd-180">這個參數會保存要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4acdd-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="4acdd-181">通常這個值儲存在私用的本機變數，並將它傳回每當`Get`呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4acdd-182">規則</span><span class="sxs-lookup"><span data-stu-id="4acdd-182">Rules</span></span>  
  
-   <span data-ttu-id="4acdd-183">**混合的存取層級。**</span><span class="sxs-lookup"><span data-stu-id="4acdd-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="4acdd-184">如果您正在定義的讀寫屬性，您可以選擇其中一個指定不同的存取層級`Get`或`Set`程序，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="4acdd-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="4acdd-185">如果您這麼做時，程序的存取層級必須是屬性的存取層級更具限制性。</span><span class="sxs-lookup"><span data-stu-id="4acdd-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="4acdd-186">例如，如果屬性宣告`Friend`，您可以宣告`Set`程序`Private`，但不是`Public`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="4acdd-187">如果您要定義`ReadOnly`或`WriteOnly`屬性中的單一屬性程序 (`Get`或`Set`分別) 代表所有的屬性。</span><span class="sxs-lookup"><span data-stu-id="4acdd-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="4acdd-188">因為，則會設定屬性的兩個存取層級，您無法宣告此類的程序，不同的存取層級。</span><span class="sxs-lookup"><span data-stu-id="4acdd-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="4acdd-189">**傳回型別。**</span><span class="sxs-lookup"><span data-stu-id="4acdd-189">**Return Type.**</span></span> <span data-ttu-id="4acdd-190">`Property`陳述式可以宣告其傳回值的資料型別。</span><span class="sxs-lookup"><span data-stu-id="4acdd-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="4acdd-191">您可以指定任何資料型別或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="4acdd-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="4acdd-192">如果您未指定`returntype`，該屬性傳回`Object`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="4acdd-193">**實作。**</span><span class="sxs-lookup"><span data-stu-id="4acdd-193">**Implementation.**</span></span> <span data-ttu-id="4acdd-194">如果這個屬性會使用`Implements`關鍵字、 包含類別或結構必須`Implements`陳述式之後立即其`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4acdd-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="4acdd-195">`Implements`陳述式必須包含在指定的每個介面`implementslist`。</span><span class="sxs-lookup"><span data-stu-id="4acdd-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="4acdd-196">不過，介面定義的名稱`Property`(在`definedname`) 並沒有這個屬性的名稱相同 (在`name`)。</span><span class="sxs-lookup"><span data-stu-id="4acdd-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4acdd-197">行為</span><span class="sxs-lookup"><span data-stu-id="4acdd-197">Behavior</span></span>  
  
-   <span data-ttu-id="4acdd-198">**從屬性程序傳回。**</span><span class="sxs-lookup"><span data-stu-id="4acdd-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="4acdd-199">當`Get`或`Set`程序會傳回呼叫程式碼，以叫用它的陳述式之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4acdd-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="4acdd-200">`Exit Property`和`Return`陳述式而造成屬性程序立即結束。</span><span class="sxs-lookup"><span data-stu-id="4acdd-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="4acdd-201">任何數目的`Exit Property`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Property`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4acdd-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="4acdd-202">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="4acdd-202">**Return Value.**</span></span> <span data-ttu-id="4acdd-203">若要傳回值，以從`Get`程序中，您可以將值指派給屬性的名稱，或將它併入`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4acdd-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="4acdd-204">下列範例將傳回值指派給屬性名稱`quoteForTheDay`，然後使用`Exit Property`陳述式來傳回。</span><span class="sxs-lookup"><span data-stu-id="4acdd-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     <span data-ttu-id="4acdd-205">[!code-vb[VbVbalrStatements #&27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4acdd-205">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="4acdd-206">[!code-vb[VbVbalrStatements #&28;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4acdd-206">[!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span></span>  
  
     <span data-ttu-id="4acdd-207">如果您使用`Exit Property`而不指派值給`name`、`Get`程序會傳回屬性的資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="4acdd-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="4acdd-208">`Return`陳述式同時指派`Get`程序傳回值，並結束程序。</span><span class="sxs-lookup"><span data-stu-id="4acdd-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="4acdd-209">下列範例示範這點。</span><span class="sxs-lookup"><span data-stu-id="4acdd-209">The following example shows this.</span></span>  
  
     <span data-ttu-id="4acdd-210">[!code-vb[VbVbalrStatements #&27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4acdd-210">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="4acdd-211">[!code-vb[VbVbalrStatements #&29;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4acdd-211">[!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4acdd-212">範例</span><span class="sxs-lookup"><span data-stu-id="4acdd-212">Example</span></span>  
 <span data-ttu-id="4acdd-213">下列範例會宣告類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="4acdd-213">The following example declares a property in a class.</span></span>  
  
 <span data-ttu-id="4acdd-214">[!code-vb[VbVbalrStatements #&51;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4acdd-214">[!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4acdd-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4acdd-215">See Also</span></span>  
 <span data-ttu-id="4acdd-216">[自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4acdd-216">[Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span></span>  
<span data-ttu-id="4acdd-217"> [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="4acdd-217"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="4acdd-218"> [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4acdd-218"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="4acdd-219"> [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4acdd-219"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) </span></span>  
<span data-ttu-id="4acdd-220"> [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="4acdd-220"> [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) </span></span>  
<span data-ttu-id="4acdd-221"> [Default](../../../visual-basic/language-reference/modifiers/default.md)</span><span class="sxs-lookup"><span data-stu-id="4acdd-221"> [Default](../../../visual-basic/language-reference/modifiers/default.md)</span></span>

