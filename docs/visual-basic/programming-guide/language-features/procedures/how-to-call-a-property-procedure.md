---
title: "如何︰ 呼叫屬性程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d0d37fc2b7ae1d563a7e9d0a8e75343dd690089b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="73c55-102">如何：呼叫屬性程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73c55-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="73c55-103">您可以將值儲存在屬性中，或擷取其值呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="73c55-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="73c55-104">存取屬性相同的方式存取的變數。</span><span class="sxs-lookup"><span data-stu-id="73c55-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="73c55-105">屬性的`Set`程序儲存值，並將其`Get`程序擷取的值。</span><span class="sxs-lookup"><span data-stu-id="73c55-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="73c55-106">不過，您沒有明確呼叫這些程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="73c55-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="73c55-107">就像您儲存或擷取變數的值，您可以使用在指派陳述式或運算式中的屬性。</span><span class="sxs-lookup"><span data-stu-id="73c55-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="73c55-108">會呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="73c55-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="73c55-109">呼叫屬性的 Get 的程序</span><span class="sxs-lookup"><span data-stu-id="73c55-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="73c55-110">使用屬性名稱的運算式中使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="73c55-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="73c55-111">您可以使用屬性您可以在任何地方使用的變數或常數。</span><span class="sxs-lookup"><span data-stu-id="73c55-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="73c55-112">-或-</span><span class="sxs-lookup"><span data-stu-id="73c55-112">-or-</span></span>  
  
     <span data-ttu-id="73c55-113">使用下列等的屬性名稱 (`=`) 登入在指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="73c55-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="73c55-114">下列範例會讀取的值<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>屬性，以隱含方式呼叫其`Get`程序。</xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="73c55-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="73c55-115">[!code-vb[VbVbalrDateProperties #&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="73c55-115">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span></span>  
  
2.  <span data-ttu-id="73c55-116">如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="73c55-116">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="73c55-117">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="73c55-117">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="73c55-118">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="73c55-118">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="73c55-119">請確定您提供的引數的屬性會定義對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="73c55-119">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="73c55-120">屬性的值加入運算式如同變數或常數一般使用，或會儲存在變數或屬性指派陳述式的左邊。</span><span class="sxs-lookup"><span data-stu-id="73c55-120">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="73c55-121">若要呼叫屬性的設定程序</span><span class="sxs-lookup"><span data-stu-id="73c55-121">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="73c55-122">指派陳述式的左邊使用屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="73c55-122">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="73c55-123">下列範例會設定的值<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>屬性，以隱含方式呼叫`Set`程序。</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span><span class="sxs-lookup"><span data-stu-id="73c55-123">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     <span data-ttu-id="73c55-124">[!code-vb[VbVbcnProcedures #&11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="73c55-124">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span></span>  
  
2.  <span data-ttu-id="73c55-125">如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="73c55-125">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="73c55-126">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="73c55-126">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="73c55-127">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="73c55-127">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="73c55-128">請確定您提供的引數的屬性會定義對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="73c55-128">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="73c55-129">指派陳述式右邊所產生的值儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="73c55-129">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c55-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73c55-130">See Also</span></span>  
 <span data-ttu-id="73c55-131">[Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-131">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="73c55-132"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="73c55-133"> [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-133"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="73c55-134"> [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-134"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="73c55-135"> [如何︰ 建立屬性](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-135"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="73c55-136"> [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-136"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="73c55-137"> [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-137"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="73c55-138"> [如何︰ 將值置入屬性](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-138"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="73c55-139"> [如何︰ 取得屬性值](./how-to-get-a-value-from-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-139"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md) </span></span>  
<span data-ttu-id="73c55-140"> [Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="73c55-140"> [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="73c55-141"> [Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="73c55-141"> [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
