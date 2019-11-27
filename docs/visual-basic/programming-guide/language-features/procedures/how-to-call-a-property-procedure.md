---
title: 如何：呼叫屬性程序
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340560"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="293e6-102">如何：呼叫屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="293e6-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="293e6-103">您可以呼叫屬性程式，方法是在屬性中儲存值，或抓取其值。</span><span class="sxs-lookup"><span data-stu-id="293e6-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="293e6-104">您可以使用與存取變數相同的方式來存取屬性。</span><span class="sxs-lookup"><span data-stu-id="293e6-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="293e6-105">屬性的 `Set` 程式會儲存值，而其 `Get` 程式會抓取值。</span><span class="sxs-lookup"><span data-stu-id="293e6-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="293e6-106">不過，您不會依名稱明確地呼叫這些程式。</span><span class="sxs-lookup"><span data-stu-id="293e6-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="293e6-107">您可以在指派語句或運算式中使用屬性，就如同儲存或取出變數的值一樣。</span><span class="sxs-lookup"><span data-stu-id="293e6-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="293e6-108">Visual Basic 會呼叫屬性的程式。</span><span class="sxs-lookup"><span data-stu-id="293e6-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="293e6-109">呼叫屬性的 Get 程式</span><span class="sxs-lookup"><span data-stu-id="293e6-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="293e6-110">在運算式中使用屬性名稱，方法與使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="293e6-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="293e6-111">您可以在任何可使用變數或常數的地方使用屬性。</span><span class="sxs-lookup"><span data-stu-id="293e6-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="293e6-112">-或-</span><span class="sxs-lookup"><span data-stu-id="293e6-112">-or-</span></span>  
  
     <span data-ttu-id="293e6-113">在指派語句中的等號（`=`）後面，使用屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="293e6-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="293e6-114">下列範例會讀取 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> 屬性的值，並隱含地呼叫其 `Get` 程式。</span><span class="sxs-lookup"><span data-stu-id="293e6-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="293e6-115">如果屬性接受引數，請在屬性名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="293e6-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="293e6-116">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="293e6-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="293e6-117">將引數放在括弧內的引數清單中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="293e6-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="293e6-118">請務必以屬性定義對應參數的相同順序來提供引數。</span><span class="sxs-lookup"><span data-stu-id="293e6-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="293e6-119">屬性的值會當做變數或常數來參與運算式，或是儲存在指派語句左側的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="293e6-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="293e6-120">呼叫屬性的 Set 程式</span><span class="sxs-lookup"><span data-stu-id="293e6-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="293e6-121">使用指派語句左側的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="293e6-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="293e6-122">下列範例會設定 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> 屬性的值，並隱含地呼叫 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="293e6-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="293e6-123">如果屬性接受引數，請在屬性名稱後面加上括弧，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="293e6-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="293e6-124">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="293e6-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="293e6-125">將引數放在括弧內的引數清單中，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="293e6-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="293e6-126">請務必以屬性定義對應參數的相同順序來提供引數。</span><span class="sxs-lookup"><span data-stu-id="293e6-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="293e6-127">在指派語句的右邊產生的值會儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="293e6-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="293e6-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="293e6-128">See also</span></span>

- [<span data-ttu-id="293e6-129">屬性程序</span><span class="sxs-lookup"><span data-stu-id="293e6-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="293e6-130">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="293e6-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="293e6-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="293e6-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="293e6-132">Visual Basic 中的屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="293e6-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="293e6-133">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="293e6-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="293e6-134">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="293e6-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="293e6-135">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="293e6-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="293e6-136">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="293e6-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="293e6-137">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="293e6-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="293e6-138">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="293e6-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="293e6-139">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="293e6-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
