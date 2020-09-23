---
title: 如何：宣告混合存取層級的屬性
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: 78363f7b2fb5b251f7409e53b2802baf83b05810
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072700"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="d40f4-102">如何：宣告混合存取層級的屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d40f4-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>

<span data-ttu-id="d40f4-103">如果您想要 `Get` `Set` 屬性上的和程式具有不同的存取層級，您可以在語句中使用較寬鬆的層級， `Property` 並在或語句中使用更嚴格的層級 `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="d40f4-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="d40f4-104">當您想要讓程式碼的某些部分能夠取得屬性的值，以及程式碼的某些其他部分能夠變更值時，您可以在屬性上使用混合存取層級。</span><span class="sxs-lookup"><span data-stu-id="d40f4-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="d40f4-105">如需存取層級的詳細資訊，請參閱 [Visual Basic 中的存取層級](../declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d40f4-105">For more information on access levels, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="d40f4-106">宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="d40f4-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="d40f4-107">以一般方式宣告屬性，並指定較不嚴格的存取層級 (例如 `Public` 語句中的) `Property` 。</span><span class="sxs-lookup"><span data-stu-id="d40f4-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="d40f4-108">宣告 `Get` 或 `Set` 指定更嚴格的存取層級 (例如) 的程式 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="d40f4-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="d40f4-109">請勿在其他屬性程式上指定存取層級。</span><span class="sxs-lookup"><span data-stu-id="d40f4-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="d40f4-110">它會假設在語句中宣告的存取層級 `Property` 。</span><span class="sxs-lookup"><span data-stu-id="d40f4-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="d40f4-111">您可以限制只能存取其中一個屬性程式。</span><span class="sxs-lookup"><span data-stu-id="d40f4-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="d40f4-112">在上述範例中，程式 `Get` 具有與 `Protected` 屬性本身相同的存取權，但程式 `Set` 具有 `Private` 存取權。</span><span class="sxs-lookup"><span data-stu-id="d40f4-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="d40f4-113">衍生自的類別 `employee` 可以讀取 `salary` 值，但只有 `employee` 類別可以設定它。</span><span class="sxs-lookup"><span data-stu-id="d40f4-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40f4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d40f4-114">See also</span></span>

- [<span data-ttu-id="d40f4-115">程序</span><span class="sxs-lookup"><span data-stu-id="d40f4-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d40f4-116">屬性程序</span><span class="sxs-lookup"><span data-stu-id="d40f4-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d40f4-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="d40f4-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d40f4-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="d40f4-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="d40f4-119">Visual Basic 中屬性和變數的差異</span><span class="sxs-lookup"><span data-stu-id="d40f4-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="d40f4-120">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="d40f4-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="d40f4-121">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="d40f4-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="d40f4-122">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="d40f4-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="d40f4-123">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="d40f4-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="d40f4-124">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="d40f4-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
