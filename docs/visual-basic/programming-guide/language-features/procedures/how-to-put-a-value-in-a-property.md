---
title: "如何︰ 將值置入屬性 (Visual Basic) |Microsoft 文件"
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
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
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
ms.openlocfilehash: c838141a27c30b11765d30ae8b0c19bccc929f4b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="3bcd4-102">如何：將值置入屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bcd4-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="3bcd4-103">您放在指派陳述式左邊的屬性名稱的值儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="3bcd4-104">屬性的`Set`程序儲存值，但您沒有明確呼叫它的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="3bcd4-105">就像您會使用變數，您可以使用屬性。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="3bcd4-106">會呼叫屬性程序。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="3bcd4-107">若要儲存的屬性值</span><span class="sxs-lookup"><span data-stu-id="3bcd4-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="3bcd4-108">指派陳述式的左邊使用屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="3bcd4-109">下列範例會設定的值[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]`TimeOfDay`屬性到中午，隱含地呼叫其`Set`程序。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-109">The following example sets the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     <span data-ttu-id="3bcd4-110">[!code-vb[VbVbcnProcedures #&11;](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3bcd4-110">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="3bcd4-111">如果屬性有引數，請遵循有括號括住的引數清單的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-111">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="3bcd4-112">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-112">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="3bcd4-113">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-113">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="3bcd4-114">請確定您提供的引數的屬性會定義對應參數的順序相同。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-114">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="3bcd4-115">指派陳述式右邊所產生的值儲存在屬性中。</span><span class="sxs-lookup"><span data-stu-id="3bcd4-115">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcd4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bcd4-116">See Also</span></span>  
 <span data-ttu-id="3bcd4-117"><xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span><span class="sxs-lookup"><span data-stu-id="3bcd4-117"><xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span></span>   
<span data-ttu-id="3bcd4-118"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-118"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="3bcd4-119"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-119"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="3bcd4-120"> [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-120"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="3bcd4-121"> [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-121"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="3bcd4-122"> [如何︰ 建立屬性](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-122"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="3bcd4-123"> [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-123"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="3bcd4-124"> [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-124"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="3bcd4-125"> [如何︰ 宣告及呼叫預設屬性，在 Visual Basic 中](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="3bcd4-125"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="3bcd4-126"> [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="3bcd4-126"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
