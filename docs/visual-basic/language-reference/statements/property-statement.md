---
title: Property Statement
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 558b62dd8c676532355ef12134ad8cb803b70796
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="property-statement"></a><span data-ttu-id="d165e-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="d165e-102">Property Statement</span></span>
<span data-ttu-id="d165e-103">宣告屬性，以及用來儲存及擷取屬性值的屬性程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="d165e-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d165e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d165e-104">Syntax</span></span>  
  
```vb  
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
  
## <a name="parts"></a><span data-ttu-id="d165e-105">組件</span><span class="sxs-lookup"><span data-stu-id="d165e-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="d165e-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-106">Optional.</span></span> <span data-ttu-id="d165e-107">適用於此屬性的屬性清單或`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="d165e-108">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="d165e-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-109">Optional.</span></span> <span data-ttu-id="d165e-110">指定這個屬性是類別或結構定義所在的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="d165e-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="d165e-111">預設屬性必須接受參數，可設定及擷取但沒有指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d165e-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="d165e-112">如果您宣告屬性做為`Default`，您不能使用`Private`屬性或其中一個屬性程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="d165e-113">選擇性在`Property`陳述式和上一個`Get`和`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d165e-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="d165e-114">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d165e-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d165e-115">Public</span><span class="sxs-lookup"><span data-stu-id="d165e-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="d165e-116">Protected</span><span class="sxs-lookup"><span data-stu-id="d165e-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="d165e-117">Friend</span><span class="sxs-lookup"><span data-stu-id="d165e-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="d165e-118">Private</span><span class="sxs-lookup"><span data-stu-id="d165e-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="d165e-119">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="d165e-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-120">Optional.</span></span> <span data-ttu-id="d165e-121">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d165e-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d165e-122">多載</span><span class="sxs-lookup"><span data-stu-id="d165e-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="d165e-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="d165e-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="d165e-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="d165e-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="d165e-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d165e-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="d165e-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d165e-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="d165e-127">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-127">Optional.</span></span> <span data-ttu-id="d165e-128">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="d165e-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-129">Optional.</span></span> <span data-ttu-id="d165e-130">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="d165e-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-131">Optional.</span></span> <span data-ttu-id="d165e-132">請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="d165e-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-133">Optional.</span></span> <span data-ttu-id="d165e-134">請參閱[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="d165e-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-135">Optional.</span></span> <span data-ttu-id="d165e-136">請參閱[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="d165e-137">必要。</span><span class="sxs-lookup"><span data-stu-id="d165e-137">Required.</span></span> <span data-ttu-id="d165e-138">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="d165e-138">Name of the property.</span></span> <span data-ttu-id="d165e-139">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="d165e-140">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-140">Optional.</span></span> <span data-ttu-id="d165e-141">本機變數的名稱，表示這個屬性的參數和可能的其他參數的清單`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="d165e-142">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="d165e-143">若`Option``Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="d165e-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="d165e-144">這個屬性所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d165e-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="d165e-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-145">Optional.</span></span> <span data-ttu-id="d165e-146">表示這個屬性會實作一個或多個屬性，每一個定義中包含這個屬性的類別或結構所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="d165e-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="d165e-147">請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="d165e-148">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="d165e-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d165e-149">要實作的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="d165e-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="d165e-150">每個 `implementedproperty` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="d165e-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="d165e-151">組件</span><span class="sxs-lookup"><span data-stu-id="d165e-151">Part</span></span>|<span data-ttu-id="d165e-152">描述</span><span class="sxs-lookup"><span data-stu-id="d165e-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="d165e-153">必要。</span><span class="sxs-lookup"><span data-stu-id="d165e-153">Required.</span></span> <span data-ttu-id="d165e-154">這個屬性所實作的介面名稱所含的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="d165e-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="d165e-155">必要。</span><span class="sxs-lookup"><span data-stu-id="d165e-155">Required.</span></span> <span data-ttu-id="d165e-156">屬性定義中依據名稱`interface`。</span><span class="sxs-lookup"><span data-stu-id="d165e-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="d165e-157">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-157">Optional.</span></span> <span data-ttu-id="d165e-158">必要屬性已標記為`WriteOnly`。</span><span class="sxs-lookup"><span data-stu-id="d165e-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="d165e-159">啟動`Get`屬性程序用來傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d165e-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="d165e-160">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-160">Optional.</span></span> <span data-ttu-id="d165e-161">在中執行的陳述式區塊`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="d165e-162">終止`Get`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="d165e-163">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d165e-163">Optional.</span></span> <span data-ttu-id="d165e-164">必要屬性已標記為`ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="d165e-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="d165e-165">啟動`Set`屬性程序用來儲存屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d165e-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="d165e-166">終止`Set`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="d165e-167">結束這個屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="d165e-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d165e-168">備註</span><span class="sxs-lookup"><span data-stu-id="d165e-168">Remarks</span></span>  
 <span data-ttu-id="d165e-169">`Property`陳述式會採用屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="d165e-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="d165e-170">屬性可以有`Get`程序 （唯讀），`Set`程序 （唯寫） 或這兩個 （可讀寫）。</span><span class="sxs-lookup"><span data-stu-id="d165e-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="d165e-171">您可以省略`Get`和`Set`程序時使用的自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="d165e-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="d165e-172">如需詳細資訊，請參閱[自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="d165e-173">您可以使用`Property`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="d165e-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="d165e-174">這表示*宣告內容*屬性必須是類別、 結構、 模組或介面，並且不能是原始程式檔、 命名空間、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="d165e-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="d165e-175">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d165e-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="d165e-176">根據預設，屬性會使用公用存取。</span><span class="sxs-lookup"><span data-stu-id="d165e-176">By default, properties use public access.</span></span> <span data-ttu-id="d165e-177">您可以調整屬性的存取層級的存取修飾詞在`Property`陳述式，而且您可以選擇性地調整為更具限制性的存取層級屬性程序的其中一個。</span><span class="sxs-lookup"><span data-stu-id="d165e-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="d165e-178">Visual Basic 會將傳遞的參數`Set`程序期間指派屬性。</span><span class="sxs-lookup"><span data-stu-id="d165e-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="d165e-179">如果您未提供的參數`Set`，整合式的開發環境 (IDE) 會使用名為的隱含參數`value`。</span><span class="sxs-lookup"><span data-stu-id="d165e-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="d165e-180">這個參數會保存要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d165e-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="d165e-181">通常這個值儲存在私用的本機變數，並將其傳回每當`Get`呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d165e-182">規則</span><span class="sxs-lookup"><span data-stu-id="d165e-182">Rules</span></span>  
  
-   <span data-ttu-id="d165e-183">**混合的存取層級。**</span><span class="sxs-lookup"><span data-stu-id="d165e-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="d165e-184">如果您要定義讀 / 寫屬性，您可以選擇其中一個指定的不同存取層`Get`或`Set`程序，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="d165e-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="d165e-185">如果您這麼做時，程序的存取層級必須比屬性存取層級更受限。</span><span class="sxs-lookup"><span data-stu-id="d165e-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="d165e-186">例如，如果屬性宣告`Friend`，您可以宣告`Set`程序`Private`，但不是`Public`。</span><span class="sxs-lookup"><span data-stu-id="d165e-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="d165e-187">如果您要定義`ReadOnly`或`WriteOnly`屬性，則單一屬性程序 (`Get`或`Set`分別) 代表所有屬性。</span><span class="sxs-lookup"><span data-stu-id="d165e-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="d165e-188">您無法宣告這類程序中，不同的存取層級，因為，則會設定兩個屬性的存取層級。</span><span class="sxs-lookup"><span data-stu-id="d165e-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="d165e-189">**傳回型別。**</span><span class="sxs-lookup"><span data-stu-id="d165e-189">**Return Type.**</span></span> <span data-ttu-id="d165e-190">`Property`陳述式可以宣告其傳回的值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d165e-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="d165e-191">您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="d165e-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="d165e-192">如果您未指定`returntype`，該屬性傳回`Object`。</span><span class="sxs-lookup"><span data-stu-id="d165e-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="d165e-193">**實作。**</span><span class="sxs-lookup"><span data-stu-id="d165e-193">**Implementation.**</span></span> <span data-ttu-id="d165e-194">如果這個屬性會使用`Implements`關鍵字、 包含的類別或結構必須`Implements`陳述式緊接著其`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d165e-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d165e-195">`Implements`陳述式必須包含每個介面中指定`implementslist`。</span><span class="sxs-lookup"><span data-stu-id="d165e-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="d165e-196">不過，介面定義的名稱`Property`(在`definedname`) 沒有為這個屬性的名稱相同 (在`name`)。</span><span class="sxs-lookup"><span data-stu-id="d165e-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d165e-197">行為</span><span class="sxs-lookup"><span data-stu-id="d165e-197">Behavior</span></span>  
  
-   <span data-ttu-id="d165e-198">**傳回從屬性程序。**</span><span class="sxs-lookup"><span data-stu-id="d165e-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="d165e-199">當`Get`或`Set`程序傳回呼叫程式碼，執行會繼續進行叫用它的陳述式之後的陳述式。</span><span class="sxs-lookup"><span data-stu-id="d165e-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="d165e-200">`Exit Property`和`Return`陳述式會導致屬性程序立即結束。</span><span class="sxs-lookup"><span data-stu-id="d165e-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="d165e-201">任何數目的`Exit Property`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Property`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d165e-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="d165e-202">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="d165e-202">**Return Value.**</span></span> <span data-ttu-id="d165e-203">若要傳回值，以從`Get`程序中，您可以將值指派給屬性名稱，或將它併入`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d165e-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="d165e-204">下列範例將傳回的值指派給屬性名稱`quoteForTheDay`，然後使用`Exit Property`陳述式來傳回。</span><span class="sxs-lookup"><span data-stu-id="d165e-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="d165e-205">如果您使用`Exit Property`而不指派值給`name`、`Get`程序會傳回屬性的資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="d165e-205">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="d165e-206">`Return`陳述式同時指派`Get`程序傳回值，然後結束程序。</span><span class="sxs-lookup"><span data-stu-id="d165e-206">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="d165e-207">下列範例顯示這點。</span><span class="sxs-lookup"><span data-stu-id="d165e-207">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="d165e-208">範例</span><span class="sxs-lookup"><span data-stu-id="d165e-208">Example</span></span>  
 <span data-ttu-id="d165e-209">下列範例會宣告類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d165e-209">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d165e-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d165e-210">See Also</span></span>  
 [<span data-ttu-id="d165e-211">自動實作的屬性</span><span class="sxs-lookup"><span data-stu-id="d165e-211">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="d165e-212">物件和類別</span><span class="sxs-lookup"><span data-stu-id="d165e-212">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="d165e-213">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="d165e-213">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="d165e-214">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="d165e-214">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="d165e-215">參數清單</span><span class="sxs-lookup"><span data-stu-id="d165e-215">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="d165e-216">Default</span><span class="sxs-lookup"><span data-stu-id="d165e-216">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
