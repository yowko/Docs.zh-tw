---
title: Get 語句（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d76155b8ff29e4f5e9206ae8fc689fa4fcaf3b8c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581824"
---
# <a name="get-statement"></a><span data-ttu-id="c8c84-102">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="c8c84-102">Get Statement</span></span>
<span data-ttu-id="c8c84-103">宣告用來取出屬性值的 `Get` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c84-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8c84-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="c8c84-105">組件</span><span class="sxs-lookup"><span data-stu-id="c8c84-105">Parts</span></span>  
  
|<span data-ttu-id="c8c84-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c8c84-106">Term</span></span>|<span data-ttu-id="c8c84-107">定義</span><span class="sxs-lookup"><span data-stu-id="c8c84-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="c8c84-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c8c84-108">Optional.</span></span> <span data-ttu-id="c8c84-109">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c84-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="c8c84-110">在此屬性中的最多一個 `Get` 和 `Set` 語句上為選擇性。</span><span class="sxs-lookup"><span data-stu-id="c8c84-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="c8c84-111">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c8c84-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="c8c84-112">-   [保護](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="c8c84-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="c8c84-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="c8c84-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="c8c84-114">-   [私](../../../visual-basic/language-reference/modifiers/private.md)用</span><span class="sxs-lookup"><span data-stu-id="c8c84-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="c8c84-115">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c8c84-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="c8c84-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c8c84-116">Optional.</span></span> <span data-ttu-id="c8c84-117">呼叫 `Get` 屬性程式時，所執行的一或多個語句。</span><span class="sxs-lookup"><span data-stu-id="c8c84-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="c8c84-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="c8c84-118">Required.</span></span> <span data-ttu-id="c8c84-119">結束 `Get` 屬性程式的定義。</span><span class="sxs-lookup"><span data-stu-id="c8c84-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8c84-120">備註</span><span class="sxs-lookup"><span data-stu-id="c8c84-120">Remarks</span></span>  
 <span data-ttu-id="c8c84-121">除非屬性標示為 `WriteOnly`，否則每個屬性都必須有 `Get` 的屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="c8c84-122">@No__t_0 程式是用來傳回屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="c8c84-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="c8c84-123">當運算式要求屬性的值時，Visual Basic 會自動呼叫屬性的 `Get` 程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="c8c84-124">屬性宣告的主體只能包含屬性的 `Get`，以及[屬性語句](../../../visual-basic/language-reference/statements/property-statement.md)和 `End Property` 語句之間的 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="c8c84-125">它不能儲存那些程式以外的任何專案。</span><span class="sxs-lookup"><span data-stu-id="c8c84-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="c8c84-126">特別是，它無法儲存屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="c8c84-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="c8c84-127">您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，另一個屬性程式就無法存取它。</span><span class="sxs-lookup"><span data-stu-id="c8c84-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="c8c84-128">一般的方法是將值儲存在與屬性相同層級所宣告的[私](../../../visual-basic/language-reference/modifiers/private.md)用變數中。</span><span class="sxs-lookup"><span data-stu-id="c8c84-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="c8c84-129">您必須在套用的屬性內定義 `Get` 程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="c8c84-130">除非您在 `Get` 語句中使用 `accessmodifier`，否則 `Get` 程式預設為其包含屬性的存取層級。</span><span class="sxs-lookup"><span data-stu-id="c8c84-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c8c84-131">規則</span><span class="sxs-lookup"><span data-stu-id="c8c84-131">Rules</span></span>  
  
- <span data-ttu-id="c8c84-132">**混合存取層級。**</span><span class="sxs-lookup"><span data-stu-id="c8c84-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="c8c84-133">如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="c8c84-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="c8c84-134">如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="c8c84-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="c8c84-135">例如，如果屬性是 `Friend` 宣告的，您可以宣告 `Get` 程式 `Private` 但不會 `Public`。</span><span class="sxs-lookup"><span data-stu-id="c8c84-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="c8c84-136">如果您要定義 `ReadOnly` 屬性，`Get` 程式會代表整個屬性。</span><span class="sxs-lookup"><span data-stu-id="c8c84-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="c8c84-137">您無法為 `Get` 宣告不同的存取層級，因為這會為屬性設定兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="c8c84-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="c8c84-138">**傳回類型。**</span><span class="sxs-lookup"><span data-stu-id="c8c84-138">**Return Type.**</span></span> <span data-ttu-id="c8c84-139">[Property 語句](../../../visual-basic/language-reference/statements/property-statement.md)可以宣告它所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c8c84-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="c8c84-140">@No__t_0 程式會自動傳回該資料類型。</span><span class="sxs-lookup"><span data-stu-id="c8c84-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="c8c84-141">您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="c8c84-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="c8c84-142">如果 `Property` 語句未指定 `returntype`，程式會傳回 `Object`。</span><span class="sxs-lookup"><span data-stu-id="c8c84-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c8c84-143">行為</span><span class="sxs-lookup"><span data-stu-id="c8c84-143">Behavior</span></span>  
  
- <span data-ttu-id="c8c84-144">**從程式傳回。**</span><span class="sxs-lookup"><span data-stu-id="c8c84-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="c8c84-145">當 `Get` 程式回到呼叫程式碼時，會在要求屬性值的語句中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="c8c84-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="c8c84-146">`Get` 屬性程式可以使用[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)或將傳回值指派給屬性名稱來傳回值。</span><span class="sxs-lookup"><span data-stu-id="c8c84-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="c8c84-147">如需詳細資訊，請參閱[Function 語句](../../../visual-basic/language-reference/statements/function-statement.md)中的「傳回值」。</span><span class="sxs-lookup"><span data-stu-id="c8c84-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="c8c84-148">@No__t_0 和 `Return` 語句會導致立即離開屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="c8c84-149">任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Property` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="c8c84-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="c8c84-150">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="c8c84-150">**Return Value.**</span></span> <span data-ttu-id="c8c84-151">若要從 `Get` 程式傳回值，您可以將值指派給屬性名稱，或將它包含在[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)中。</span><span class="sxs-lookup"><span data-stu-id="c8c84-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="c8c84-152">@No__t_0 語句會同時指派 `Get` 程式傳回值並結束程式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="c8c84-153">如果您使用 `Exit Property` 而不指派屬性名稱的值，則 `Get` 程式會傳回屬性之資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="c8c84-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="c8c84-154">如需詳細資訊，請參閱[Function 語句](../../../visual-basic/language-reference/statements/function-statement.md)中的「傳回值」。</span><span class="sxs-lookup"><span data-stu-id="c8c84-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="c8c84-155">下列範例說明唯讀屬性 `quoteForTheDay` 可以傳回 `quoteValue` 的私用變數中保留之值的兩種方式。</span><span class="sxs-lookup"><span data-stu-id="c8c84-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="c8c84-156">範例</span><span class="sxs-lookup"><span data-stu-id="c8c84-156">Example</span></span>  
 <span data-ttu-id="c8c84-157">下列範例會使用 `Get` 語句來傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c8c84-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="c8c84-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8c84-158">See also</span></span>

- [<span data-ttu-id="c8c84-159">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="c8c84-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="c8c84-160">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="c8c84-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="c8c84-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="c8c84-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="c8c84-162">物件和類別</span><span class="sxs-lookup"><span data-stu-id="c8c84-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="c8c84-163">逐步解說：定義類別</span><span class="sxs-lookup"><span data-stu-id="c8c84-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
