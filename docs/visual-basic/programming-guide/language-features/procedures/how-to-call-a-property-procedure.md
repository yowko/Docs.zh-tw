---
title: "如何：呼叫屬性程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="5c66a-102">如何：呼叫屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c66a-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="5c66a-103">您可以將值儲存在屬性或擷取其值呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="5c66a-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="5c66a-104">存取屬性相同的方式存取的變數。</span><span class="sxs-lookup"><span data-stu-id="5c66a-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="5c66a-105">屬性的`Set`程序可儲存值，並將其`Get`程序擷取的值。</span><span class="sxs-lookup"><span data-stu-id="5c66a-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="5c66a-106">不過，您沒有明確呼叫這些程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c66a-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="5c66a-107">就如同您儲存或擷取變數的值，您可以使用指派陳述式或運算式中的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c66a-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="5c66a-108">會呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="5c66a-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="5c66a-109">若要呼叫的屬性 Get 的程序</span><span class="sxs-lookup"><span data-stu-id="5c66a-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="5c66a-110">使用屬性名稱的運算式中使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="5c66a-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="5c66a-111">您可以使用屬性您可以在任何地方使用的變數或常數。</span><span class="sxs-lookup"><span data-stu-id="5c66a-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="5c66a-112">-或-</span><span class="sxs-lookup"><span data-stu-id="5c66a-112">-or-</span></span>  
  
     <span data-ttu-id="5c66a-113">使用下列相等的屬性名稱 (`=`) 登入指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="5c66a-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="5c66a-114">下列範例會讀取的值<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>屬性，以隱含方式呼叫其`Get`程序。</span><span class="sxs-lookup"><span data-stu-id="5c66a-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="5c66a-115">如果屬性引數，請遵循以括號來括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="5c66a-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="5c66a-116">如果有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="5c66a-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="5c66a-117">將引數放在括號，並以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="5c66a-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="5c66a-118">請確定您提供的引數的屬性會定義的對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="5c66a-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="5c66a-119">屬性的值加入運算式如同變數或常數會或儲存在變數或指派陳述式左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c66a-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="5c66a-120">呼叫屬性的設定程序</span><span class="sxs-lookup"><span data-stu-id="5c66a-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="5c66a-121">指派陳述式的左邊使用屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="5c66a-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="5c66a-122">下列範例會設定的值<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>屬性，以隱含方式呼叫`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="5c66a-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="5c66a-123">如果屬性引數，請遵循以括號來括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="5c66a-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="5c66a-124">如果有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="5c66a-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="5c66a-125">將引數放在括號，並以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="5c66a-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="5c66a-126">請確定您提供的引數的屬性會定義的對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="5c66a-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="5c66a-127">產生的指派陳述式右邊的值會儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="5c66a-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c66a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c66a-128">See Also</span></span>  
 [<span data-ttu-id="5c66a-129">屬性程序</span><span class="sxs-lookup"><span data-stu-id="5c66a-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="5c66a-130">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="5c66a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5c66a-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="5c66a-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="5c66a-132">在 Visual Basic 中屬性和變數之間的差異</span><span class="sxs-lookup"><span data-stu-id="5c66a-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="5c66a-133">如何：建立屬性</span><span class="sxs-lookup"><span data-stu-id="5c66a-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="5c66a-134">如何：宣告混合存取層級的屬性</span><span class="sxs-lookup"><span data-stu-id="5c66a-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="5c66a-135">如何： 宣告及呼叫在 Visual Basic 中的預設屬性</span><span class="sxs-lookup"><span data-stu-id="5c66a-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="5c66a-136">如何：將值置入屬性</span><span class="sxs-lookup"><span data-stu-id="5c66a-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="5c66a-137">如何：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="5c66a-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="5c66a-138">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="5c66a-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="5c66a-139">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="5c66a-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
