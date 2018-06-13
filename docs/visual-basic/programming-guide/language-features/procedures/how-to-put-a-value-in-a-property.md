---
title: 如何：將值置入屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650367"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="c80d7-102">如何：將值置入屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c80d7-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="c80d7-103">您儲存值，您可以在屬性中的屬性名稱放在指派陳述式的左半部。</span><span class="sxs-lookup"><span data-stu-id="c80d7-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="c80d7-104">屬性的`Set`程序可儲存值，但您沒有明確呼叫它的名稱。</span><span class="sxs-lookup"><span data-stu-id="c80d7-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="c80d7-105">就像您會使用變數，您可以使用屬性。</span><span class="sxs-lookup"><span data-stu-id="c80d7-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="c80d7-106">Visual Basic 會將屬性的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="c80d7-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="c80d7-107">若要在屬性中儲存的值</span><span class="sxs-lookup"><span data-stu-id="c80d7-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="c80d7-108">指派陳述式的左邊使用屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="c80d7-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="c80d7-109">下列範例會設定的值的 Visual Basic`TimeOfDay`屬性中午，隱含地呼叫其`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="c80d7-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  <span data-ttu-id="c80d7-110">如果屬性引數，請遵循以括號來括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="c80d7-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="c80d7-111">如果有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="c80d7-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="c80d7-112">將引數放在括號，並以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="c80d7-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="c80d7-113">請確定您提供的引數的屬性會定義的對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="c80d7-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="c80d7-114">產生的指派陳述式右邊的值會儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="c80d7-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80d7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c80d7-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [<span data-ttu-id="c80d7-116">屬性程序</span><span class="sxs-lookup"><span data-stu-id="c80d7-116">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="c80d7-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="c80d7-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c80d7-118">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="c80d7-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="c80d7-119">在 Visual Basic 中屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="c80d7-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="c80d7-120">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="c80d7-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="c80d7-121">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="c80d7-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="c80d7-122">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="c80d7-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="c80d7-123">如何： 宣告及呼叫在 Visual Basic 中的預設屬性</span><span class="sxs-lookup"><span data-stu-id="c80d7-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="c80d7-124">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="c80d7-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
