---
title: "如何︰ 宣告及呼叫預設屬性，在 Visual Basic |Microsoft 文件"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: 7cfd476def67ccf46e524da7943680f9e34b6a26
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="64e14-102">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="64e14-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="64e14-103">A*預設屬性*是類別或結構的屬性，可以存取您的程式碼，而不指定它。</span><span class="sxs-lookup"><span data-stu-id="64e14-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="64e14-104">當呼叫程式碼的類別或結構，但不是屬性名稱和內容都可存取屬性，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]解析成該類別或結構的預設屬性的存取權，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="64e14-104">When calling code names a class or structure but not a property, and the context allows access to a property, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="64e14-105">類別或結構最多可以有一個預設屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="64e14-106">不過，您可以多載的預設屬性，並讓它的多個版本。</span><span class="sxs-lookup"><span data-stu-id="64e14-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="64e14-107">如需詳細資訊，請參閱[預設](../../../../visual-basic/language-reference/modifiers/default.md)。</span><span class="sxs-lookup"><span data-stu-id="64e14-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="64e14-108">若要宣告預設屬性</span><span class="sxs-lookup"><span data-stu-id="64e14-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="64e14-109">以一般方式宣告屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-109">Declare the property in the normal way.</span></span> <span data-ttu-id="64e14-110">未指定`Shared`或`Private`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="64e14-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="64e14-111">包含`Default`屬性宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="64e14-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="64e14-112">指定至少一個參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="64e14-113">您無法定義預設屬性不需要使用至少一個引數。</span><span class="sxs-lookup"><span data-stu-id="64e14-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     <span data-ttu-id="64e14-114">[!code-vb[VbVbcnProcedures #&17;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-114">[!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span></span>  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="64e14-115">若要呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="64e14-115">To call a default property</span></span>  
  
1.  <span data-ttu-id="64e14-116">宣告為包含的類別或結構類型的變數。</span><span class="sxs-lookup"><span data-stu-id="64e14-116">Declare a variable of the containing class or structure type.</span></span>  
  
     <span data-ttu-id="64e14-117">[!code-vb[VbVbcnProcedures #&16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-117">[!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span></span>  
  
2.  <span data-ttu-id="64e14-118">使用變數名稱只在運算式中，您通常會包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="64e14-118">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     <span data-ttu-id="64e14-119">[!code-vb[VbVbcnProcedures #&21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-119">[!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span></span>  
  
3.  <span data-ttu-id="64e14-120">在變數名稱後面的括號括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="64e14-120">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="64e14-121">預設屬性必須接受至少一個引數。</span><span class="sxs-lookup"><span data-stu-id="64e14-121">A default property must take at least one argument.</span></span>  
  
     <span data-ttu-id="64e14-122">[!code-vb[VbVbcnProcedures #&20;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-122">[!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span></span>  
  
4.  <span data-ttu-id="64e14-123">若要擷取預設屬性值，使用變數名稱，在運算式中，或等號之後的引數清單 (`=`) 登入在指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="64e14-123">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="64e14-124">[!code-vb[VbVbcnProcedures #&15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-124">[!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span></span>  
  
5.  <span data-ttu-id="64e14-125">若要設定預設屬性值，使用的引數清單，在指派陳述式左邊的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="64e14-125">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="64e14-126">[!code-vb[VbVbcnProcedures #&14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-126">[!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span></span>  
  
6.  <span data-ttu-id="64e14-127">您永遠可以指定預設屬性名稱與變數名稱，就像您一樣存取任何其他屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-127">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     <span data-ttu-id="64e14-128">[!code-vb[VbVbcnProcedures #&19;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-128">[!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="64e14-129">範例</span><span class="sxs-lookup"><span data-stu-id="64e14-129">Example</span></span>  
 <span data-ttu-id="64e14-130">下列範例會宣告預設屬性類別上。</span><span class="sxs-lookup"><span data-stu-id="64e14-130">The following example declares a default property on a class.</span></span>  
  
 <span data-ttu-id="64e14-131">[!code-vb[VbVbcnProcedures #&12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-131">[!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="64e14-132">範例</span><span class="sxs-lookup"><span data-stu-id="64e14-132">Example</span></span>  
 <span data-ttu-id="64e14-133">下列範例示範如何呼叫預設屬性`myProperty`類別上`class1`。</span><span class="sxs-lookup"><span data-stu-id="64e14-133">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="64e14-134">三個指派陳述式存放區中的值`myProperty`，而<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼叫讀取值。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="64e14-134">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 <span data-ttu-id="64e14-135">[!code-vb[VbVbcnProcedures #&13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e14-135">[!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span></span>  
  
 <span data-ttu-id="64e14-136">預設屬性的最常見的用法是<xref:Microsoft.VisualBasic.Collection.Item%2A>上各種不同的集合類別的屬性。</xref:Microsoft.VisualBasic.Collection.Item%2A></span><span class="sxs-lookup"><span data-stu-id="64e14-136">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="64e14-137">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="64e14-137">Robust Programming</span></span>  
 <span data-ttu-id="64e14-138">預設屬性可能會導致小減少原始程式碼字元，但會讓您的程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="64e14-138">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="64e14-139">如果類別或結構名稱的參考時呼叫的程式碼不熟悉您的類別或結構，它無法確定該參考存取類別或結構本身或預設屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-139">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="64e14-140">這可能會導致編譯器錯誤或微妙的執行階段邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="64e14-140">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="64e14-141">您可以稍微降低預設屬性錯誤的機會都使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定編譯器型別檢查`On`。</span><span class="sxs-lookup"><span data-stu-id="64e14-141">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="64e14-142">如果您打算使用預先定義的類別或結構中程式碼，您必須決定是否具有預設屬性，而且如果是，其名稱為何。</span><span class="sxs-lookup"><span data-stu-id="64e14-142">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="64e14-143">由於這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-143">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="64e14-144">程式碼的可讀性，您應該也考慮一律明確參考所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="64e14-144">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e14-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64e14-145">See Also</span></span>  
 <span data-ttu-id="64e14-146">[Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-146">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="64e14-147"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-147"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="64e14-148"> [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-148"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="64e14-149"> [預設值](../../../../visual-basic/language-reference/modifiers/default.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-149"> [Default](../../../../visual-basic/language-reference/modifiers/default.md) </span></span>  
<span data-ttu-id="64e14-150"> [Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-150"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="64e14-151"> [如何︰ 建立屬性](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-151"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="64e14-152"> [如何︰ 宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-152"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="64e14-153"> [如何︰ 呼叫屬性程序](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-153"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="64e14-154"> [如何︰ 將值置入屬性](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="64e14-154"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="64e14-155"> [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="64e14-155"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
