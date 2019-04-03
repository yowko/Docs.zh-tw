---
title: Get 陳述式 (Visual Basic)
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
ms.openlocfilehash: 245d2cc36abde76a8f8bd73bae5d7ede183d4d03
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840506"
---
# <a name="get-statement"></a><span data-ttu-id="76358-102">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="76358-102">Get Statement</span></span>
<span data-ttu-id="76358-103">宣告`Get`屬性程序用來擷取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="76358-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76358-104">語法</span><span class="sxs-lookup"><span data-stu-id="76358-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="76358-105">組件</span><span class="sxs-lookup"><span data-stu-id="76358-105">Parts</span></span>  
  
|<span data-ttu-id="76358-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="76358-106">Term</span></span>|<span data-ttu-id="76358-107">定義</span><span class="sxs-lookup"><span data-stu-id="76358-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="76358-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="76358-108">Optional.</span></span> <span data-ttu-id="76358-109">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="76358-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="76358-110">上最多一個的選擇性`Get`和`Set`這個屬性中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="76358-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="76358-111">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="76358-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="76358-112">-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="76358-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="76358-113">-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="76358-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="76358-114">-   [私用](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="76358-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="76358-115">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="76358-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="76358-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="76358-116">Optional.</span></span> <span data-ttu-id="76358-117">一或多個陳述式時執行`Get`呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="76358-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="76358-118">必要項。</span><span class="sxs-lookup"><span data-stu-id="76358-118">Required.</span></span> <span data-ttu-id="76358-119">結束的定義`Get`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="76358-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76358-120">備註</span><span class="sxs-lookup"><span data-stu-id="76358-120">Remarks</span></span>  
 <span data-ttu-id="76358-121">每個屬性必須有`Get`屬性程序屬性標示為除非`WriteOnly`。</span><span class="sxs-lookup"><span data-stu-id="76358-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="76358-122">`Get`程序用來傳回屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="76358-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="76358-123">Visual Basic 會自動呼叫屬性的`Get`運算式要求屬性的值時的程序。</span><span class="sxs-lookup"><span data-stu-id="76358-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="76358-124">屬性宣告的主體可以包含屬性的`Get`並`Set`之間的程序[Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)而`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="76358-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="76358-125">它無法儲存這些程序以外的任何項目。</span><span class="sxs-lookup"><span data-stu-id="76358-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="76358-126">特別是，它無法儲存屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="76358-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="76358-127">您必須先儲存外部屬性，這個值，因為如果您將其儲存在其中一個屬性程序，其他的屬性程序無法存取它。</span><span class="sxs-lookup"><span data-stu-id="76358-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="76358-128">一般的方法是將值儲存在[私人](../../../visual-basic/language-reference/modifiers/private.md)屬性與相同層級宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="76358-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="76358-129">您必須定義`Get`它所套用的屬性內的程序。</span><span class="sxs-lookup"><span data-stu-id="76358-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="76358-130">`Get`程序預設值為其包含屬性的存取層級，除非您使用`accessmodifier`在`Get`陳述式。</span><span class="sxs-lookup"><span data-stu-id="76358-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="76358-131">規則</span><span class="sxs-lookup"><span data-stu-id="76358-131">Rules</span></span>  
  
-   <span data-ttu-id="76358-132">**混合的存取層級。**</span><span class="sxs-lookup"><span data-stu-id="76358-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="76358-133">如果您正在定義的讀寫屬性，您可以選擇性地針對指定不同的存取層級`Get`或`Set`程序，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="76358-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="76358-134">如果您這麼做時，程序的存取層級必須比屬性的存取層級更具限制性。</span><span class="sxs-lookup"><span data-stu-id="76358-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="76358-135">例如，如果屬性宣告`Friend`，您可以宣告`Get`程序`Private`，而非`Public`。</span><span class="sxs-lookup"><span data-stu-id="76358-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="76358-136">如果您要定義`ReadOnly`屬性，`Get`程序都代表整個屬性。</span><span class="sxs-lookup"><span data-stu-id="76358-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="76358-137">您無法宣告不同的存取層級`Get`，因為，則會設定屬性的兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="76358-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="76358-138">**傳回型別。**</span><span class="sxs-lookup"><span data-stu-id="76358-138">**Return Type.**</span></span> <span data-ttu-id="76358-139">[Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)可以宣告其傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="76358-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="76358-140">`Get`程序會自動傳回資料類型。</span><span class="sxs-lookup"><span data-stu-id="76358-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="76358-141">您可以指定任何資料類型或列舉、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="76358-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="76358-142">如果`Property`陳述式未指定`returntype`，此程序傳回`Object`。</span><span class="sxs-lookup"><span data-stu-id="76358-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="76358-143">行為</span><span class="sxs-lookup"><span data-stu-id="76358-143">Behavior</span></span>  
  
-   <span data-ttu-id="76358-144">**傳回從程序。**</span><span class="sxs-lookup"><span data-stu-id="76358-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="76358-145">當`Get`程序傳回給呼叫程式碼，會繼續執行要求的屬性值的陳述式中。</span><span class="sxs-lookup"><span data-stu-id="76358-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="76358-146">`Get` 屬性程序可以傳回值，使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)或傳回值，指派給屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="76358-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="76358-147">如需詳細資訊，請參閱 「 傳回的值 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="76358-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="76358-148">`Exit Property`和`Return`陳述式造成屬性程序立即結束。</span><span class="sxs-lookup"><span data-stu-id="76358-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="76358-149">任意數目的`Exit Property`並`Return`陳述式可以出現在任何位置的程序中，您可以混合`Exit Property`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="76358-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="76358-150">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="76358-150">**Return Value.**</span></span> <span data-ttu-id="76358-151">要傳回的值`Get`程序中，您可以將值指派給屬性名稱，或將它併入[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="76358-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="76358-152">`Return`陳述式同時指派`Get`程序傳回值，並結束程序。</span><span class="sxs-lookup"><span data-stu-id="76358-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="76358-153">如果您使用`Exit Property`而不指派值給屬性名稱，`Get`程序會傳回屬性的資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="76358-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="76358-154">如需詳細資訊，請參閱 「 傳回的值 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="76358-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="76358-155">下列範例說明兩種方式的唯讀屬性`quoteForTheDay`可以傳回私用變數的值`quoteValue`。</span><span class="sxs-lookup"><span data-stu-id="76358-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="76358-156">範例</span><span class="sxs-lookup"><span data-stu-id="76358-156">Example</span></span>  
 <span data-ttu-id="76358-157">下列範例會使用`Get`陳述式來傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="76358-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="76358-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76358-158">See also</span></span>

- [<span data-ttu-id="76358-159">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="76358-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="76358-160">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="76358-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="76358-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="76358-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="76358-162">物件和類別</span><span class="sxs-lookup"><span data-stu-id="76358-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="76358-163">逐步解說：定義類別</span><span class="sxs-lookup"><span data-stu-id="76358-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
