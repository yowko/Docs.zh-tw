---
title: 如何：將值置入屬性
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 7d85066d4678ee2a53b8339bee2db20374482579
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071400"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="85ebc-102">如何：將值置入屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85ebc-102">How to: Put a Value in a Property (Visual Basic)</span></span>

<span data-ttu-id="85ebc-103">您可以將屬性名稱放在指派語句的左邊，以將值儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="85ebc-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="85ebc-104">屬性的程式會 `Set` 儲存一個值，但您不會依名稱明確地呼叫它。</span><span class="sxs-lookup"><span data-stu-id="85ebc-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="85ebc-105">您可以使用屬性，就像使用變數一樣。</span><span class="sxs-lookup"><span data-stu-id="85ebc-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="85ebc-106">Visual Basic 會對屬性的程式進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="85ebc-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="85ebc-107">若要在屬性中儲存值</span><span class="sxs-lookup"><span data-stu-id="85ebc-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="85ebc-108">使用指派語句左邊的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="85ebc-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="85ebc-109">下列範例會將 Visual Basic 屬性的值設定 `TimeOfDay` 為中午，並隱含地呼叫其程式 `Set` 。</span><span class="sxs-lookup"><span data-stu-id="85ebc-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="85ebc-110">如果屬性採用引數，請在屬性名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="85ebc-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="85ebc-111">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="85ebc-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="85ebc-112">將引數清單中的引數放在括弧內，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="85ebc-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="85ebc-113">請務必以屬性定義對應參數的相同順序提供引數。</span><span class="sxs-lookup"><span data-stu-id="85ebc-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="85ebc-114">在指派語句的右邊產生的值會儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="85ebc-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ebc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85ebc-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="85ebc-116">屬性程序</span><span class="sxs-lookup"><span data-stu-id="85ebc-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="85ebc-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="85ebc-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="85ebc-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="85ebc-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="85ebc-119">Visual Basic 中屬性和變數的差異</span><span class="sxs-lookup"><span data-stu-id="85ebc-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="85ebc-120">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="85ebc-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="85ebc-121">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="85ebc-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="85ebc-122">如何：呼叫屬性程序</span><span class="sxs-lookup"><span data-stu-id="85ebc-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="85ebc-123">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="85ebc-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="85ebc-124">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="85ebc-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
