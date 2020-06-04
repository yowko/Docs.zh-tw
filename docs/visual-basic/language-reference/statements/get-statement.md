---
title: Get 陳述式
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
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404598"
---
# <a name="get-statement"></a><span data-ttu-id="c2ff7-102">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="c2ff7-102">Get Statement</span></span>
<span data-ttu-id="c2ff7-103">宣告 `Get` 用來取出屬性值的屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ff7-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2ff7-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="c2ff7-105">組件</span><span class="sxs-lookup"><span data-stu-id="c2ff7-105">Parts</span></span>  
  
|<span data-ttu-id="c2ff7-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c2ff7-106">Term</span></span>|<span data-ttu-id="c2ff7-107">定義</span><span class="sxs-lookup"><span data-stu-id="c2ff7-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="c2ff7-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-108">Optional.</span></span> <span data-ttu-id="c2ff7-109">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="c2ff7-110">在 `Get` 此屬性中最多隻可有一個和語句的選擇性 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="c2ff7-111">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c2ff7-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="c2ff7-112">-   [免受](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="c2ff7-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="c2ff7-113">-   [給](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="c2ff7-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="c2ff7-114">-   [私人](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="c2ff7-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="c2ff7-115">請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="c2ff7-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-116">Optional.</span></span> <span data-ttu-id="c2ff7-117">呼叫屬性程式時所執行的一或多個語句 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="c2ff7-118">必要。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-118">Required.</span></span> <span data-ttu-id="c2ff7-119">終止屬性程式的定義 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2ff7-120">備註</span><span class="sxs-lookup"><span data-stu-id="c2ff7-120">Remarks</span></span>  
 <span data-ttu-id="c2ff7-121">`Get`除非已標記屬性，否則每個屬性都必須具有屬性程式 `WriteOnly` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="c2ff7-122">此 `Get` 程式是用來傳回屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="c2ff7-123">`Get`當運算式要求屬性的值時，Visual Basic 會自動呼叫屬性的程式。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="c2ff7-124">屬性宣告的主體只能包含屬性 `Get` `Set` [語句](property-statement.md)與語句之間的和程式 `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="c2ff7-125">它不能儲存那些程式以外的任何專案。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="c2ff7-126">特別是，它無法儲存屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="c2ff7-127">您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，另一個屬性程式就無法存取它。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="c2ff7-128">一般的方法是將值儲存在與屬性相同層級所宣告的[私](../modifiers/private.md)用變數中。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="c2ff7-129">您必須在 `Get` 所套用的屬性內定義程式。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="c2ff7-130">`Get`除非您 `accessmodifier` 在語句中使用，否則程式會預設為其包含屬性的存取層級 `Get` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c2ff7-131">規則</span><span class="sxs-lookup"><span data-stu-id="c2ff7-131">Rules</span></span>  
  
- <span data-ttu-id="c2ff7-132">**混合存取層級。**</span><span class="sxs-lookup"><span data-stu-id="c2ff7-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="c2ff7-133">如果您要定義讀寫屬性，則可以選擇性地為或程式指定不同的存取層級 `Get` `Set` ，但不能同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="c2ff7-134">如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="c2ff7-135">例如，如果已宣告屬性 `Friend` ，您可以宣告程式 `Get` `Private` ，而不是 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="c2ff7-136">如果您要定義 `ReadOnly` 屬性，程式會 `Get` 代表整個屬性。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="c2ff7-137">您不能為設定不同的存取層級 `Get` ，因為這會為屬性設定兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="c2ff7-138">**傳回類型。**</span><span class="sxs-lookup"><span data-stu-id="c2ff7-138">**Return Type.**</span></span> <span data-ttu-id="c2ff7-139">[Property 語句](property-statement.md)可以宣告它所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="c2ff7-140">此 `Get` 程式會自動傳回該資料類型。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="c2ff7-141">您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="c2ff7-142">如果 `Property` 語句未指定，則程式會傳回 `returntype` `Object` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c2ff7-143">行為</span><span class="sxs-lookup"><span data-stu-id="c2ff7-143">Behavior</span></span>  
  
- <span data-ttu-id="c2ff7-144">**從程式傳回。**</span><span class="sxs-lookup"><span data-stu-id="c2ff7-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="c2ff7-145">當程式 `Get` 返回呼叫程式碼時，會在要求屬性值的語句中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="c2ff7-146">`Get`屬性程式可以使用[Return 語句](return-statement.md)或將傳回值指派給屬性名稱來傳回值。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="c2ff7-147">如需詳細資訊，請參閱[Function 語句](function-statement.md)中的「傳回值」。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="c2ff7-148">`Exit Property`和 `Return` 語句會導致立即離開屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="c2ff7-149">任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用 `Exit Property` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="c2ff7-150">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="c2ff7-150">**Return Value.**</span></span> <span data-ttu-id="c2ff7-151">若要從程式傳回值 `Get` ，您可以將值指派給屬性名稱，或將它包含在[return 語句](return-statement.md)中。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="c2ff7-152">`Return`語句會同時指派程式傳回 `Get` 值並結束程式。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="c2ff7-153">如果您使用 `Exit Property` 但未指派屬性名稱的值，程式會傳回 `Get` 屬性之資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="c2ff7-154">如需詳細資訊，請參閱[Function 語句](function-statement.md)中的「傳回值」。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="c2ff7-155">下列範例說明唯讀屬性 `quoteForTheDay` 可以傳回私用變數中保留之值的兩種方式 `quoteValue` 。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="c2ff7-156">範例</span><span class="sxs-lookup"><span data-stu-id="c2ff7-156">Example</span></span>  
 <span data-ttu-id="c2ff7-157">下列範例會使用 `Get` 語句來傳回屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c2ff7-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="c2ff7-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2ff7-158">See also</span></span>

- [<span data-ttu-id="c2ff7-159">Set 語句</span><span class="sxs-lookup"><span data-stu-id="c2ff7-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="c2ff7-160">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c2ff7-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="c2ff7-161">Exit 陳述式</span><span class="sxs-lookup"><span data-stu-id="c2ff7-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="c2ff7-162">物件和類別</span><span class="sxs-lookup"><span data-stu-id="c2ff7-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="c2ff7-163">逐步解說：定義類別</span><span class="sxs-lookup"><span data-stu-id="c2ff7-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
