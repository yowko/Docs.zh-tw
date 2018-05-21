---
title: Property Statement
ms.date: 05/12/2018
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
ms.openlocfilehash: 3f3ced3f0c441518594820f75243c71fb0c3babd
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="property-statement"></a><span data-ttu-id="3005b-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="3005b-102">Property Statement</span></span>
<span data-ttu-id="3005b-103">宣告屬性，以及用來儲存及擷取屬性值的屬性程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="3005b-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3005b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3005b-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="3005b-105">組件</span><span class="sxs-lookup"><span data-stu-id="3005b-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="3005b-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-106">Optional.</span></span> <span data-ttu-id="3005b-107">適用於此屬性的屬性清單或`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="3005b-108">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="3005b-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-109">Optional.</span></span> <span data-ttu-id="3005b-110">指定這個屬性是類別或結構定義所在的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="3005b-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="3005b-111">預設屬性必須接受參數，可設定及擷取但沒有指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3005b-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="3005b-112">如果您宣告屬性做為`Default`，您不能使用`Private`屬性或其中一個屬性程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="3005b-113">選擇性在`Property`陳述式和上一個`Get`和`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3005b-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="3005b-114">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3005b-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3005b-115">Public</span><span class="sxs-lookup"><span data-stu-id="3005b-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="3005b-116">Protected</span><span class="sxs-lookup"><span data-stu-id="3005b-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="3005b-117">Friend</span><span class="sxs-lookup"><span data-stu-id="3005b-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="3005b-118">Private</span><span class="sxs-lookup"><span data-stu-id="3005b-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="3005b-119">Protected 的 Friend</span><span class="sxs-lookup"><span data-stu-id="3005b-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md) 

    - [<span data-ttu-id="3005b-120">受保護的私用</span><span class="sxs-lookup"><span data-stu-id="3005b-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="3005b-121">請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="3005b-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-122">Optional.</span></span> <span data-ttu-id="3005b-123">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="3005b-123">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3005b-124">多載</span><span class="sxs-lookup"><span data-stu-id="3005b-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="3005b-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="3005b-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="3005b-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="3005b-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="3005b-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3005b-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="3005b-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3005b-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="3005b-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-129">Optional.</span></span> <span data-ttu-id="3005b-130">請參閱[共用](../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="3005b-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-131">Optional.</span></span> <span data-ttu-id="3005b-132">請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="3005b-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-133">Optional.</span></span> <span data-ttu-id="3005b-134">請參閱[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="3005b-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-135">Optional.</span></span> <span data-ttu-id="3005b-136">請參閱[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="3005b-137">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-137">Optional.</span></span> <span data-ttu-id="3005b-138">請參閱[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="3005b-139">必要。</span><span class="sxs-lookup"><span data-stu-id="3005b-139">Required.</span></span> <span data-ttu-id="3005b-140">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3005b-140">Name of the property.</span></span> <span data-ttu-id="3005b-141">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="3005b-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-142">Optional.</span></span> <span data-ttu-id="3005b-143">本機變數的名稱，表示這個屬性的參數和可能的其他參數的清單`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="3005b-144">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="3005b-145">若`Option``Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="3005b-145">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="3005b-146">這個屬性所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3005b-146">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="3005b-147">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-147">Optional.</span></span> <span data-ttu-id="3005b-148">表示這個屬性會實作一個或多個屬性，每一個定義中包含這個屬性的類別或結構所實作的介面。</span><span class="sxs-lookup"><span data-stu-id="3005b-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="3005b-149">請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="3005b-150">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="3005b-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="3005b-151">要實作的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="3005b-151">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="3005b-152">每個 `implementedproperty` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="3005b-152">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="3005b-153">組件</span><span class="sxs-lookup"><span data-stu-id="3005b-153">Part</span></span>|<span data-ttu-id="3005b-154">描述</span><span class="sxs-lookup"><span data-stu-id="3005b-154">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="3005b-155">必要。</span><span class="sxs-lookup"><span data-stu-id="3005b-155">Required.</span></span> <span data-ttu-id="3005b-156">這個屬性所實作的介面名稱所含的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="3005b-156">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="3005b-157">必要。</span><span class="sxs-lookup"><span data-stu-id="3005b-157">Required.</span></span> <span data-ttu-id="3005b-158">屬性定義中依據名稱`interface`。</span><span class="sxs-lookup"><span data-stu-id="3005b-158">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="3005b-159">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-159">Optional.</span></span> <span data-ttu-id="3005b-160">必要屬性已標記為`WriteOnly`。</span><span class="sxs-lookup"><span data-stu-id="3005b-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="3005b-161">啟動`Get`屬性程序用來傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3005b-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="3005b-162">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-162">Optional.</span></span> <span data-ttu-id="3005b-163">在中執行的陳述式區塊`Get`或`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="3005b-164">終止`Get`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-164">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="3005b-165">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3005b-165">Optional.</span></span> <span data-ttu-id="3005b-166">必要屬性已標記為`ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="3005b-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="3005b-167">啟動`Set`屬性程序用來儲存屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3005b-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="3005b-168">終止`Set`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-168">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="3005b-169">結束這個屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="3005b-169">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3005b-170">備註</span><span class="sxs-lookup"><span data-stu-id="3005b-170">Remarks</span></span>  
 <span data-ttu-id="3005b-171">`Property`陳述式會採用屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="3005b-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="3005b-172">屬性可以有`Get`程序 （唯讀），`Set`程序 （唯寫） 或這兩個 （可讀寫）。</span><span class="sxs-lookup"><span data-stu-id="3005b-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="3005b-173">您可以省略`Get`和`Set`程序時使用的自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="3005b-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="3005b-174">如需詳細資訊，請參閱[自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="3005b-175">您可以使用`Property`只能在類別層級。</span><span class="sxs-lookup"><span data-stu-id="3005b-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="3005b-176">這表示*宣告內容*屬性必須是類別、 結構、 模組或介面，並且不能是原始程式檔、 命名空間、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="3005b-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="3005b-177">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="3005b-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3005b-178">根據預設，屬性會使用公用存取。</span><span class="sxs-lookup"><span data-stu-id="3005b-178">By default, properties use public access.</span></span> <span data-ttu-id="3005b-179">您可以調整屬性的存取層級的存取修飾詞在`Property`陳述式，而且您可以選擇性地調整為更具限制性的存取層級屬性程序的其中一個。</span><span class="sxs-lookup"><span data-stu-id="3005b-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="3005b-180">Visual Basic 會將傳遞的參數`Set`程序期間指派屬性。</span><span class="sxs-lookup"><span data-stu-id="3005b-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="3005b-181">如果您未提供的參數`Set`，整合式的開發環境 (IDE) 會使用名為的隱含參數`value`。</span><span class="sxs-lookup"><span data-stu-id="3005b-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="3005b-182">這個參數會保存要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3005b-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="3005b-183">通常這個值儲存在私用的本機變數，並將其傳回每當`Get`呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3005b-184">規則</span><span class="sxs-lookup"><span data-stu-id="3005b-184">Rules</span></span>  
  
-   <span data-ttu-id="3005b-185">**混合的存取層級。**</span><span class="sxs-lookup"><span data-stu-id="3005b-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="3005b-186">如果您要定義讀 / 寫屬性，您可以選擇其中一個指定的不同存取層`Get`或`Set`程序，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="3005b-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3005b-187">如果您這麼做時，程序的存取層級必須比屬性存取層級更受限。</span><span class="sxs-lookup"><span data-stu-id="3005b-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3005b-188">例如，如果屬性宣告`Friend`，您可以宣告`Set`程序`Private`，但不是`Public`。</span><span class="sxs-lookup"><span data-stu-id="3005b-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="3005b-189">如果您要定義`ReadOnly`或`WriteOnly`屬性，則單一屬性程序 (`Get`或`Set`分別) 代表所有屬性。</span><span class="sxs-lookup"><span data-stu-id="3005b-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="3005b-190">您無法宣告這類程序中，不同的存取層級，因為，則會設定兩個屬性的存取層級。</span><span class="sxs-lookup"><span data-stu-id="3005b-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="3005b-191">**傳回型別。**</span><span class="sxs-lookup"><span data-stu-id="3005b-191">**Return Type.**</span></span> <span data-ttu-id="3005b-192">`Property`陳述式可以宣告其傳回的值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3005b-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="3005b-193">您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="3005b-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="3005b-194">如果您未指定`returntype`，該屬性傳回`Object`。</span><span class="sxs-lookup"><span data-stu-id="3005b-194">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="3005b-195">**實作。**</span><span class="sxs-lookup"><span data-stu-id="3005b-195">**Implementation.**</span></span> <span data-ttu-id="3005b-196">如果這個屬性會使用`Implements`關鍵字、 包含的類別或結構必須`Implements`陳述式緊接著其`Class`或`Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3005b-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="3005b-197">`Implements`陳述式必須包含每個介面中指定`implementslist`。</span><span class="sxs-lookup"><span data-stu-id="3005b-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="3005b-198">不過，介面定義的名稱`Property`(在`definedname`) 沒有為這個屬性的名稱相同 (在`name`)。</span><span class="sxs-lookup"><span data-stu-id="3005b-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3005b-199">行為</span><span class="sxs-lookup"><span data-stu-id="3005b-199">Behavior</span></span>  
  
-   <span data-ttu-id="3005b-200">**傳回從屬性程序。**</span><span class="sxs-lookup"><span data-stu-id="3005b-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="3005b-201">當`Get`或`Set`程序傳回呼叫程式碼，執行會繼續進行叫用它的陳述式之後的陳述式。</span><span class="sxs-lookup"><span data-stu-id="3005b-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="3005b-202">`Exit Property`和`Return`陳述式會導致屬性程序立即結束。</span><span class="sxs-lookup"><span data-stu-id="3005b-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3005b-203">任何數目的`Exit Property`和`Return`陳述式可以出現在任何地方程序，且您可以混合`Exit Property`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3005b-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="3005b-204">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="3005b-204">**Return Value.**</span></span> <span data-ttu-id="3005b-205">若要傳回值，以從`Get`程序中，您可以將值指派給屬性名稱，或將它併入`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3005b-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="3005b-206">下列範例將傳回的值指派給屬性名稱`quoteForTheDay`，然後使用`Exit Property`陳述式來傳回。</span><span class="sxs-lookup"><span data-stu-id="3005b-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="3005b-207">如果您使用`Exit Property`而不指派值給`name`、`Get`程序會傳回屬性的資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="3005b-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="3005b-208">`Return`陳述式同時指派`Get`程序傳回值，然後結束程序。</span><span class="sxs-lookup"><span data-stu-id="3005b-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="3005b-209">下列範例顯示這點。</span><span class="sxs-lookup"><span data-stu-id="3005b-209">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="3005b-210">範例</span><span class="sxs-lookup"><span data-stu-id="3005b-210">Example</span></span>  
 <span data-ttu-id="3005b-211">下列範例會宣告類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3005b-211">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3005b-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3005b-212">See Also</span></span>  
 [<span data-ttu-id="3005b-213">自動實作的屬性</span><span class="sxs-lookup"><span data-stu-id="3005b-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="3005b-214">物件和類別</span><span class="sxs-lookup"><span data-stu-id="3005b-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="3005b-215">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="3005b-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="3005b-216">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="3005b-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="3005b-217">參數清單</span><span class="sxs-lookup"><span data-stu-id="3005b-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="3005b-218">Default</span><span class="sxs-lookup"><span data-stu-id="3005b-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
