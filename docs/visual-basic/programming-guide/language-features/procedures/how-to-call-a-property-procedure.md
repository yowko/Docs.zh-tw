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
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="1413a-102">如何：呼叫屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1413a-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="1413a-103">You call a property procedure by storing a value in the property or retrieving its value.</span><span class="sxs-lookup"><span data-stu-id="1413a-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="1413a-104">You access a property the same way you access a variable.</span><span class="sxs-lookup"><span data-stu-id="1413a-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="1413a-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span><span class="sxs-lookup"><span data-stu-id="1413a-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="1413a-106">However, you do not explicitly call these procedures by name.</span><span class="sxs-lookup"><span data-stu-id="1413a-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="1413a-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span><span class="sxs-lookup"><span data-stu-id="1413a-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="1413a-108">Visual Basic makes the calls to the property's procedures.</span><span class="sxs-lookup"><span data-stu-id="1413a-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="1413a-109">To call a property's Get procedure</span><span class="sxs-lookup"><span data-stu-id="1413a-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="1413a-110">Use the property name in an expression the same way you would use a variable name.</span><span class="sxs-lookup"><span data-stu-id="1413a-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="1413a-111">You can use a property anywhere you can use a variable or a constant.</span><span class="sxs-lookup"><span data-stu-id="1413a-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="1413a-112">-或-</span><span class="sxs-lookup"><span data-stu-id="1413a-112">-or-</span></span>  
  
     <span data-ttu-id="1413a-113">Use the property name following the equal (`=`) sign in an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="1413a-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="1413a-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span><span class="sxs-lookup"><span data-stu-id="1413a-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="1413a-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span><span class="sxs-lookup"><span data-stu-id="1413a-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="1413a-116">If there are no arguments, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="1413a-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="1413a-117">Place the arguments in the argument list within the parentheses, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="1413a-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="1413a-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span><span class="sxs-lookup"><span data-stu-id="1413a-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="1413a-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span><span class="sxs-lookup"><span data-stu-id="1413a-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="1413a-120">To call a property's Set procedure</span><span class="sxs-lookup"><span data-stu-id="1413a-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="1413a-121">Use the property name on the left side of an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="1413a-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="1413a-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="1413a-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="1413a-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span><span class="sxs-lookup"><span data-stu-id="1413a-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="1413a-124">If there are no arguments, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="1413a-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="1413a-125">Place the arguments in the argument list within the parentheses, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="1413a-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="1413a-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span><span class="sxs-lookup"><span data-stu-id="1413a-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="1413a-127">The value generated on the right side of the assignment statement is stored in the property.</span><span class="sxs-lookup"><span data-stu-id="1413a-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1413a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="1413a-128">See also</span></span>

- [<span data-ttu-id="1413a-129">屬性程序</span><span class="sxs-lookup"><span data-stu-id="1413a-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1413a-130">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="1413a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1413a-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="1413a-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="1413a-132">Differences Between Properties and Variables in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1413a-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="1413a-133">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="1413a-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="1413a-134">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="1413a-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="1413a-135">How to: Declare and Call a Default Property in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1413a-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="1413a-136">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="1413a-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="1413a-137">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="1413a-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="1413a-138">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="1413a-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="1413a-139">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="1413a-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
