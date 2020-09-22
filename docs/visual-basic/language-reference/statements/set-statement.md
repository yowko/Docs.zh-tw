---
title: Set 陳述式
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
ms.openlocfilehash: b3524769567a56a87184bf916a3e5ccb1fd4fa1c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871749"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="0118e-102">Set 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0118e-102">Set Statement (Visual Basic)</span></span>

<span data-ttu-id="0118e-103">宣告 `Set` 用來將值指派給屬性的屬性程式。</span><span class="sxs-lookup"><span data-stu-id="0118e-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0118e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0118e-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="0118e-105">組件</span><span class="sxs-lookup"><span data-stu-id="0118e-105">Parts</span></span>  

 `attributelist`  
 <span data-ttu-id="0118e-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0118e-106">Optional.</span></span> <span data-ttu-id="0118e-107">請參閱 [屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="0118e-107">See [Attribute List](attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="0118e-108">選擇性 `Get` 地在這個屬性中最多一個和 `Set` 語句上。</span><span class="sxs-lookup"><span data-stu-id="0118e-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="0118e-109">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0118e-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="0118e-110">保護</span><span class="sxs-lookup"><span data-stu-id="0118e-110">Protected</span></span>](../modifiers/protected.md)  
  
- [<span data-ttu-id="0118e-111">Friend</span><span class="sxs-lookup"><span data-stu-id="0118e-111">Friend</span></span>](../modifiers/friend.md)  
  
- [<span data-ttu-id="0118e-112">私人</span><span class="sxs-lookup"><span data-stu-id="0118e-112">Private</span></span>](../modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="0118e-113">請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="0118e-113">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="0118e-114">必要。</span><span class="sxs-lookup"><span data-stu-id="0118e-114">Required.</span></span> <span data-ttu-id="0118e-115">包含屬性之新值的參數。</span><span class="sxs-lookup"><span data-stu-id="0118e-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="0118e-116">如果 `Option Strict` 為，則為必要項 `On` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="0118e-117">參數的資料類型 `value` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="0118e-118">指定的資料類型必須與宣告此語句之屬性的資料類型相同 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="0118e-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0118e-119">Optional.</span></span> <span data-ttu-id="0118e-120">呼叫屬性程式時執行的一或多個語句 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="0118e-121">必要。</span><span class="sxs-lookup"><span data-stu-id="0118e-121">Required.</span></span> <span data-ttu-id="0118e-122">終止屬性程式的定義 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0118e-123">備註</span><span class="sxs-lookup"><span data-stu-id="0118e-123">Remarks</span></span>  

 <span data-ttu-id="0118e-124">除非已標記屬性，否則每個屬性都必須有 `Set` 屬性程式 `ReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="0118e-125">此 `Set` 程式是用來設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0118e-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="0118e-126">`Set`當指派語句提供要儲存在屬性中的值時，Visual Basic 會自動呼叫屬性的程式。</span><span class="sxs-lookup"><span data-stu-id="0118e-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="0118e-127">Visual Basic 會 `Set` 在屬性指派期間將參數傳遞給程式。</span><span class="sxs-lookup"><span data-stu-id="0118e-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="0118e-128">如果您未提供的參數 `Set` ，則 (IDE) 的整合式開發環境會使用名為的隱含參數 `value` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="0118e-129">參數會保存要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0118e-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="0118e-130">您通常會在私用區域變數中儲存此值，並在 `Get` 呼叫程式時傳回。</span><span class="sxs-lookup"><span data-stu-id="0118e-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="0118e-131">屬性宣告的主體只能包含屬性和屬性（property） `Get` `Set` [語句](property-statement.md) 和語句之間的程式 `End Property` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="0118e-132">它無法儲存那些程式以外的任何其他作業。</span><span class="sxs-lookup"><span data-stu-id="0118e-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="0118e-133">尤其是，它無法儲存屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="0118e-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="0118e-134">您必須將此值儲存在屬性之外，因為如果您將它儲存在其中一個屬性程式中，則其他屬性程式就無法存取它。</span><span class="sxs-lookup"><span data-stu-id="0118e-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="0118e-135">常見的方法是將值儲存在與屬性相同層級宣告的 [私](../modifiers/private.md) 用變數中。</span><span class="sxs-lookup"><span data-stu-id="0118e-135">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="0118e-136">您必須在 `Set` 套用它的屬性內定義程式。</span><span class="sxs-lookup"><span data-stu-id="0118e-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="0118e-137">`Set`除非您 `accessmodifier` 在語句中使用，否則程式會預設為其包含屬性的存取層級 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="0118e-138">規則</span><span class="sxs-lookup"><span data-stu-id="0118e-138">Rules</span></span>  
  
- <span data-ttu-id="0118e-139">**混合存取層級。**</span><span class="sxs-lookup"><span data-stu-id="0118e-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="0118e-140">如果您要定義讀寫屬性，則可以選擇性地為或程式指定不同的存取層級 `Get` `Set` ，但不能同時指定兩者。</span><span class="sxs-lookup"><span data-stu-id="0118e-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="0118e-141">如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="0118e-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="0118e-142">例如，如果已宣告屬性 `Friend` ，您可以宣告程式 `Set` `Private` ，但不可以 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="0118e-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="0118e-143">如果您要定義 `WriteOnly` 屬性，此程式 `Set` 代表整個屬性。</span><span class="sxs-lookup"><span data-stu-id="0118e-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="0118e-144">您無法針對設定不同的存取層級 `Set` ，因為這樣會為屬性設定兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="0118e-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="0118e-145">行為</span><span class="sxs-lookup"><span data-stu-id="0118e-145">Behavior</span></span>  
  
- <span data-ttu-id="0118e-146">**從屬性程式傳回。**</span><span class="sxs-lookup"><span data-stu-id="0118e-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="0118e-147">當程式 `Set` 返回呼叫程式碼時，執行會繼續遵循提供要儲存之值的語句。</span><span class="sxs-lookup"><span data-stu-id="0118e-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="0118e-148">`Set` 屬性程式可以使用 [Return 語句](return-statement.md) 或 [Exit 語句](exit-statement.md)傳回。</span><span class="sxs-lookup"><span data-stu-id="0118e-148">`Set` property procedures can return using either the [Return Statement](return-statement.md) or the [Exit Statement](exit-statement.md).</span></span>  
  
     <span data-ttu-id="0118e-149">`Exit Property`和 `Return` 語句會導致立即結束屬性程式。</span><span class="sxs-lookup"><span data-stu-id="0118e-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="0118e-150">任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合使用和 `Exit Property` `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="0118e-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0118e-151">範例</span><span class="sxs-lookup"><span data-stu-id="0118e-151">Example</span></span>  

 <span data-ttu-id="0118e-152">下列範例會使用 `Set` 語句來設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0118e-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="0118e-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0118e-153">See also</span></span>

- [<span data-ttu-id="0118e-154">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="0118e-154">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="0118e-155">Property Statement</span><span class="sxs-lookup"><span data-stu-id="0118e-155">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="0118e-156">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="0118e-156">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="0118e-157">屬性程序</span><span class="sxs-lookup"><span data-stu-id="0118e-157">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
