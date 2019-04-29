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
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783873"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="f8ce9-102">Set 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8ce9-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="f8ce9-103">宣告`Set`用來將值指派給屬性的屬性程序。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8ce9-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8ce9-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="f8ce9-105">組件</span><span class="sxs-lookup"><span data-stu-id="f8ce9-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="f8ce9-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-106">Optional.</span></span> <span data-ttu-id="f8ce9-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="f8ce9-108">上最多一個的選擇性`Get`和`Set`這個屬性中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="f8ce9-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f8ce9-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="f8ce9-110">Protected</span><span class="sxs-lookup"><span data-stu-id="f8ce9-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="f8ce9-111">Friend</span><span class="sxs-lookup"><span data-stu-id="f8ce9-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="f8ce9-112">Private</span><span class="sxs-lookup"><span data-stu-id="f8ce9-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="f8ce9-113">請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="f8ce9-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-114">Required.</span></span> <span data-ttu-id="f8ce9-115">包含屬性的新值的參數。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="f8ce9-116">需要`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="f8ce9-117">資料類型的`value`參數。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="f8ce9-118">指定的資料類型必須是屬性的資料型別相同，這`Set`宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="f8ce9-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-119">Optional.</span></span> <span data-ttu-id="f8ce9-120">一或多個陳述式時執行`Set`呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="f8ce9-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-121">Required.</span></span> <span data-ttu-id="f8ce9-122">結束的定義`Set`屬性程序。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8ce9-123">備註</span><span class="sxs-lookup"><span data-stu-id="f8ce9-123">Remarks</span></span>  
 <span data-ttu-id="f8ce9-124">每個屬性必須有`Set`屬性程序屬性標示為除非`ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="f8ce9-125">`Set`程序用來設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="f8ce9-126">Visual Basic 會自動呼叫屬性的`Set`程序時在指派陳述式提供所要儲存在屬性值。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="f8ce9-127">Visual Basic 會將傳遞的參數`Set`屬性指派期間的程序。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="f8ce9-128">如果您未提供的參數`Set`，整合式的開發環境 (IDE) 會使用名為的隱含參數`value`。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="f8ce9-129">參數包含要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="f8ce9-130">您通常會將此值儲存在私用的本機變數，並將它傳回每當`Get`呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="f8ce9-131">屬性宣告的主體可以包含屬性的`Get`並`Set`之間的程序[Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)而`End Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="f8ce9-132">它無法儲存這些程序以外的任何項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="f8ce9-133">特別是，它無法儲存屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="f8ce9-134">您必須先儲存外部屬性，這個值，因為如果您將其儲存在其中一個屬性程序，其他的屬性程序無法存取它。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="f8ce9-135">一般的方法是將值儲存在[私人](../../../visual-basic/language-reference/modifiers/private.md)屬性與相同層級宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="f8ce9-136">您必須定義`Set`它所套用的屬性內的程序。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="f8ce9-137">`Set`程序預設值為其包含屬性的存取層級，除非您使用`accessmodifier`在`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f8ce9-138">規則</span><span class="sxs-lookup"><span data-stu-id="f8ce9-138">Rules</span></span>  
  
- <span data-ttu-id="f8ce9-139">**混合的存取層級。**</span><span class="sxs-lookup"><span data-stu-id="f8ce9-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="f8ce9-140">如果您正在定義的讀寫屬性，您可以選擇性地針對指定不同的存取層級`Get`或`Set`程序，但非兩者。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="f8ce9-141">如果您這麼做時，程序的存取層級必須比屬性的存取層級更具限制性。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="f8ce9-142">例如，如果屬性宣告`Friend`，您可以宣告`Set`程序`Private`，而非`Public`。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="f8ce9-143">如果您要定義`WriteOnly`屬性，`Set`程序都代表整個屬性。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="f8ce9-144">您無法宣告不同的存取層級`Set`，因為，則會設定屬性的兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f8ce9-145">行為</span><span class="sxs-lookup"><span data-stu-id="f8ce9-145">Behavior</span></span>  
  
- <span data-ttu-id="f8ce9-146">**傳回從屬性程序。**</span><span class="sxs-lookup"><span data-stu-id="f8ce9-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="f8ce9-147">當`Set`程序傳回給呼叫程式碼，會繼續執行下列陳述式，提供要儲存的值。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="f8ce9-148">`Set` 屬性程序可以傳回使用[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)或[Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="f8ce9-149">`Exit Property`和`Return`陳述式造成屬性程序立即結束。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="f8ce9-150">任意數目的`Exit Property`並`Return`陳述式可以出現在任何位置的程序中，您可以混合`Exit Property`和`Return`陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8ce9-151">範例</span><span class="sxs-lookup"><span data-stu-id="f8ce9-151">Example</span></span>  
 <span data-ttu-id="f8ce9-152">下列範例會使用`Set`陳述式來設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f8ce9-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="f8ce9-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8ce9-153">See also</span></span>

- [<span data-ttu-id="f8ce9-154">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="f8ce9-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="f8ce9-155">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="f8ce9-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="f8ce9-156">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f8ce9-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f8ce9-157">屬性程序</span><span class="sxs-lookup"><span data-stu-id="f8ce9-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
