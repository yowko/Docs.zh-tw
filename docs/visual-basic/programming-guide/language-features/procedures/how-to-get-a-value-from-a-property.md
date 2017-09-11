---
title: "如何︰ 取得屬性 (Visual Basic) 的值 |Microsoft 文件"
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
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
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
ms.openlocfilehash: 719a4fc9ff163fb4437ea40c8265a5e36232347e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="41aaf-102">如何：取得屬性值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41aaf-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="41aaf-103">您可以在運算式中包含的屬性名稱擷取屬性的值。</span><span class="sxs-lookup"><span data-stu-id="41aaf-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="41aaf-104">屬性的`Get`程序會擷取值，但您沒有明確呼叫它的名稱。</span><span class="sxs-lookup"><span data-stu-id="41aaf-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="41aaf-105">就像您會使用變數，您可以使用屬性。</span><span class="sxs-lookup"><span data-stu-id="41aaf-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="41aaf-106">會呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="41aaf-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="41aaf-107">若要擷取屬性值</span><span class="sxs-lookup"><span data-stu-id="41aaf-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="41aaf-108">使用屬性名稱的運算式中使用變數名稱的方式相同。</span><span class="sxs-lookup"><span data-stu-id="41aaf-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="41aaf-109">您可以使用屬性您可以在任何地方使用的變數或常數。</span><span class="sxs-lookup"><span data-stu-id="41aaf-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="41aaf-110">-或-</span><span class="sxs-lookup"><span data-stu-id="41aaf-110">-or-</span></span>  
  
     <span data-ttu-id="41aaf-111">使用下列等的屬性名稱 (`=`) 登入在指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="41aaf-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="41aaf-112">下列範例會讀取的值[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`Now`屬性，以隱含方式呼叫其`Get`程序。</span><span class="sxs-lookup"><span data-stu-id="41aaf-112">The following example reads the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="41aaf-113">[!code-vb[VbVbalrDateProperties #&4;](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="41aaf-113">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="41aaf-114">如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="41aaf-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="41aaf-115">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="41aaf-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="41aaf-116">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="41aaf-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="41aaf-117">請確定您提供的引數的屬性會定義對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="41aaf-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="41aaf-118">屬性的值加入運算式如同變數或常數一般使用，或會儲存在變數或屬性指派陳述式的左邊。</span><span class="sxs-lookup"><span data-stu-id="41aaf-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41aaf-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41aaf-119">See Also</span></span>  
 <span data-ttu-id="41aaf-120">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-120">[Procedures](./index.md) </span></span>  
<span data-ttu-id="41aaf-121"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="41aaf-122"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-122"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="41aaf-123"> [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-123"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="41aaf-124"> [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-124"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="41aaf-125"> [如何︰ 建立屬性](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-125"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="41aaf-126"> [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-126"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="41aaf-127"> [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-127"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="41aaf-128"> [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="41aaf-128"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="41aaf-129"> [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="41aaf-129"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md)</span></span>
