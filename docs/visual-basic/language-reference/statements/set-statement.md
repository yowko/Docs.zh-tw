---
title: Set 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583228"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="7ab61-102">Set 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ab61-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="7ab61-103">宣告用來將值指派給屬性的 `Set` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab61-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ab61-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="7ab61-105">組件</span><span class="sxs-lookup"><span data-stu-id="7ab61-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="7ab61-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="7ab61-106">Optional.</span></span> <span data-ttu-id="7ab61-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab61-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="7ab61-108">在此屬性中的最多一個 `Get` 和 `Set` 語句上為選擇性。</span><span class="sxs-lookup"><span data-stu-id="7ab61-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="7ab61-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7ab61-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="7ab61-110">Protected</span><span class="sxs-lookup"><span data-stu-id="7ab61-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="7ab61-111">Friend</span><span class="sxs-lookup"><span data-stu-id="7ab61-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="7ab61-112">Private</span><span class="sxs-lookup"><span data-stu-id="7ab61-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="7ab61-113">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab61-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="7ab61-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="7ab61-114">Required.</span></span> <span data-ttu-id="7ab61-115">包含屬性之新值的參數。</span><span class="sxs-lookup"><span data-stu-id="7ab61-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="7ab61-116">如果 `Option Strict` `On`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="7ab61-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="7ab61-117">@No__t_0 參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7ab61-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="7ab61-118">指定的資料類型必須與宣告此 `Set` 語句之屬性的資料類型相同。</span><span class="sxs-lookup"><span data-stu-id="7ab61-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="7ab61-119">選擇項。</span><span class="sxs-lookup"><span data-stu-id="7ab61-119">Optional.</span></span> <span data-ttu-id="7ab61-120">呼叫 `Set` 屬性程式時，所執行的一或多個語句。</span><span class="sxs-lookup"><span data-stu-id="7ab61-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="7ab61-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="7ab61-121">Required.</span></span> <span data-ttu-id="7ab61-122">結束 `Set` 屬性程式的定義。</span><span class="sxs-lookup"><span data-stu-id="7ab61-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab61-123">備註</span><span class="sxs-lookup"><span data-stu-id="7ab61-123">Remarks</span></span>  
 <span data-ttu-id="7ab61-124">除非屬性標示為 `ReadOnly`，否則每個屬性都必須有 `Set` 的屬性程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="7ab61-125">@No__t_0 程式是用來設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7ab61-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="7ab61-126">當指派語句提供要儲存在屬性中的值時，Visual Basic 會自動呼叫屬性的 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="7ab61-127">Visual Basic 在屬性指派期間，將參數傳遞給 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="7ab61-128">如果您未提供 `Set` 的參數，整合式開發環境（IDE）會使用名為 `value` 的隱含參數。</span><span class="sxs-lookup"><span data-stu-id="7ab61-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="7ab61-129">參數會保留要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7ab61-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="7ab61-130">您通常會將此值儲存在私用區域變數中，並在每次呼叫 `Get` 程式時傳回它。</span><span class="sxs-lookup"><span data-stu-id="7ab61-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="7ab61-131">屬性宣告的主體只能包含屬性的 `Get`，以及[屬性語句](../../../visual-basic/language-reference/statements/property-statement.md)和 `End Property` 語句之間的 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="7ab61-132">它不能儲存那些程式以外的任何專案。</span><span class="sxs-lookup"><span data-stu-id="7ab61-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="7ab61-133">特別是，它無法儲存屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="7ab61-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="7ab61-134">您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，另一個屬性程式就無法存取它。</span><span class="sxs-lookup"><span data-stu-id="7ab61-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="7ab61-135">一般的方法是將值儲存在與屬性相同層級所宣告的[私](../../../visual-basic/language-reference/modifiers/private.md)用變數中。</span><span class="sxs-lookup"><span data-stu-id="7ab61-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="7ab61-136">您必須在套用的屬性內定義 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="7ab61-137">除非您在 `Set` 語句中使用 `accessmodifier`，否則 `Set` 程式預設為其包含屬性的存取層級。</span><span class="sxs-lookup"><span data-stu-id="7ab61-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7ab61-138">規則</span><span class="sxs-lookup"><span data-stu-id="7ab61-138">Rules</span></span>  
  
- <span data-ttu-id="7ab61-139">**混合存取層級。**</span><span class="sxs-lookup"><span data-stu-id="7ab61-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="7ab61-140">如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="7ab61-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="7ab61-141">如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="7ab61-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="7ab61-142">例如，如果屬性是 `Friend` 宣告的，您可以宣告 `Set` 程式 `Private` 但不會 `Public`。</span><span class="sxs-lookup"><span data-stu-id="7ab61-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="7ab61-143">如果您要定義 `WriteOnly` 屬性，`Set` 程式會代表整個屬性。</span><span class="sxs-lookup"><span data-stu-id="7ab61-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="7ab61-144">您無法為 `Set` 宣告不同的存取層級，因為這會為屬性設定兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="7ab61-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7ab61-145">行為</span><span class="sxs-lookup"><span data-stu-id="7ab61-145">Behavior</span></span>  
  
- <span data-ttu-id="7ab61-146">**從屬性程式傳回。**</span><span class="sxs-lookup"><span data-stu-id="7ab61-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="7ab61-147">當 `Set` 程式回到呼叫程式碼時，執行會在提供要儲存之值的語句後面繼續進行。</span><span class="sxs-lookup"><span data-stu-id="7ab61-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="7ab61-148">`Set` 屬性程式可以使用[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)或[Exit 語句](../../../visual-basic/language-reference/statements/exit-statement.md)傳回。</span><span class="sxs-lookup"><span data-stu-id="7ab61-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="7ab61-149">@No__t_0 和 `Return` 語句會導致立即離開屬性程式。</span><span class="sxs-lookup"><span data-stu-id="7ab61-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="7ab61-150">任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Property` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="7ab61-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ab61-151">範例</span><span class="sxs-lookup"><span data-stu-id="7ab61-151">Example</span></span>  
 <span data-ttu-id="7ab61-152">下列範例會使用 `Set` 語句來設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7ab61-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="7ab61-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ab61-153">See also</span></span>

- [<span data-ttu-id="7ab61-154">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ab61-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="7ab61-155">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ab61-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="7ab61-156">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="7ab61-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7ab61-157">屬性程序</span><span class="sxs-lookup"><span data-stu-id="7ab61-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
