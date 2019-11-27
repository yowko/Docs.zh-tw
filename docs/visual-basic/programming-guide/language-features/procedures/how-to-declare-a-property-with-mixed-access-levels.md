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
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349689"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="03fc0-102">如何：宣告混合存取層級的屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03fc0-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="03fc0-103">如果您想要讓屬性上的 `Get` 和 `Set` 程式擁有不同的存取層級，您可以在 `Property` 語句中使用更寬鬆的等級，並在 `Get` 或 `Set` 語句中使用更嚴格的層級。</span><span class="sxs-lookup"><span data-stu-id="03fc0-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="03fc0-104">當您希望程式碼的某些部分能夠取得屬性的值，而且程式碼的某些其他部分能夠變更值時，您可以在屬性上使用混合存取層級。</span><span class="sxs-lookup"><span data-stu-id="03fc0-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="03fc0-105">如需存取層級的詳細資訊，請參閱[Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="03fc0-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="03fc0-106">若要宣告具有混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="03fc0-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="03fc0-107">以一般方式宣告屬性，並在 `Property` 語句中指定較不嚴格的存取層級（例如 `Public`）。</span><span class="sxs-lookup"><span data-stu-id="03fc0-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="03fc0-108">請宣告 `Get` 或 `Set` 程式，以指定更嚴格的存取層級（例如 `Friend`）。</span><span class="sxs-lookup"><span data-stu-id="03fc0-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="03fc0-109">請不要在另一個屬性程式上指定存取層級。</span><span class="sxs-lookup"><span data-stu-id="03fc0-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="03fc0-110">它會假設在 `Property` 語句中宣告的存取層級。</span><span class="sxs-lookup"><span data-stu-id="03fc0-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="03fc0-111">您可以限制只有其中一個屬性程式的存取權。</span><span class="sxs-lookup"><span data-stu-id="03fc0-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="03fc0-112">在上述範例中，`Get` 程式與屬性本身具有相同的 `Protected` 存取權，而 `Set` 程式則具有 `Private` 存取權。</span><span class="sxs-lookup"><span data-stu-id="03fc0-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="03fc0-113">衍生自 `employee` 的類別可以讀取 `salary` 值，但只有 `employee` 類別可以設定它。</span><span class="sxs-lookup"><span data-stu-id="03fc0-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03fc0-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="03fc0-114">See also</span></span>

- [<span data-ttu-id="03fc0-115">程序</span><span class="sxs-lookup"><span data-stu-id="03fc0-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="03fc0-116">屬性程序</span><span class="sxs-lookup"><span data-stu-id="03fc0-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="03fc0-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="03fc0-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="03fc0-118">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="03fc0-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="03fc0-119">Visual Basic 中的屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="03fc0-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="03fc0-120">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="03fc0-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="03fc0-121">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="03fc0-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="03fc0-122">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="03fc0-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="03fc0-123">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="03fc0-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="03fc0-124">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="03fc0-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
