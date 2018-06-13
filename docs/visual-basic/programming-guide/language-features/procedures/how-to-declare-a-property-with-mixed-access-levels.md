---
title: 如何：宣告混合存取層級的屬性 (Visual Basic)
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
ms.openlocfilehash: 8d25086fe6f8b5f5300006466ef49782cb065edf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651407"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="78ea2-102">如何：宣告混合存取層級的屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78ea2-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="78ea2-103">如果您想`Get`和`Set`屬性有不同的存取層級的程序，您可以使用中的更寬鬆的層級`Property`陳述式和更嚴格的層級，在`Get`或`Set`陳述式。</span><span class="sxs-lookup"><span data-stu-id="78ea2-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="78ea2-104">當您想要能夠取得屬性值的程式碼某些部分和其他部分的程式碼，將值變更時，您可以使用屬性上的混合的存取層級。</span><span class="sxs-lookup"><span data-stu-id="78ea2-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="78ea2-105">如需有關存取層級的詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="78ea2-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="78ea2-106">若要宣告混合的存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="78ea2-106">To declare a property with mixed access levels</span></span>  
  
1.  <span data-ttu-id="78ea2-107">宣告屬性以一般方式，並指定較不嚴格的存取層級 (例如`Public`) 中`Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="78ea2-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2.  <span data-ttu-id="78ea2-108">宣告其中`Get`或`Set`程序並指定更嚴格的存取層級 (例如`Friend`)。</span><span class="sxs-lookup"><span data-stu-id="78ea2-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3.  <span data-ttu-id="78ea2-109">未指定存取層級上的其他屬性程序。</span><span class="sxs-lookup"><span data-stu-id="78ea2-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="78ea2-110">它會假設中宣告的存取層級`Property`陳述式。</span><span class="sxs-lookup"><span data-stu-id="78ea2-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="78ea2-111">您可以限制存取其中一個屬性程序。</span><span class="sxs-lookup"><span data-stu-id="78ea2-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     <span data-ttu-id="78ea2-112">在上述範例中，`Get`程序中的相同`Protected`存取與屬性本身，而`Set`程序中的`Private`存取。</span><span class="sxs-lookup"><span data-stu-id="78ea2-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="78ea2-113">類別衍生自`employee`可以讀取`salary`值，但只`employee`類別可以將其設定。</span><span class="sxs-lookup"><span data-stu-id="78ea2-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ea2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78ea2-114">See Also</span></span>  
 [<span data-ttu-id="78ea2-115">程序</span><span class="sxs-lookup"><span data-stu-id="78ea2-115">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="78ea2-116">屬性程序</span><span class="sxs-lookup"><span data-stu-id="78ea2-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="78ea2-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="78ea2-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="78ea2-118">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="78ea2-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="78ea2-119">在 Visual Basic 中屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="78ea2-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="78ea2-120">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="78ea2-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="78ea2-121">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="78ea2-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="78ea2-122">如何： 宣告及呼叫在 Visual Basic 中的預設屬性</span><span class="sxs-lookup"><span data-stu-id="78ea2-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="78ea2-123">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="78ea2-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="78ea2-124">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="78ea2-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
