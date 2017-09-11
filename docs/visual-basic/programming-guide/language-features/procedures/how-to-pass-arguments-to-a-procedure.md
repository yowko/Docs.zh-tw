---
title: "如何︰ 將引數傳遞至程序 (Visual Basic) |Microsoft 文件"
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
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
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
ms.openlocfilehash: 1e0a8d5e798f25f22f53f56a7c01bd69e3e14463
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="9730f-102">如何：將引數傳遞至程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9730f-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="9730f-103">當您呼叫程序時，您可以依照括號括住的引數清單的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="9730f-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="9730f-104">您會提供引數對應至每個必要參數的程序定義，而您可以選擇性地提供引數`Optional`參數。</span><span class="sxs-lookup"><span data-stu-id="9730f-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="9730f-105">如果您未提供`Optional`中呼叫的參數，您必須包含一個逗號，以標記引數清單中的位置，如果您提供的任何後續的引數。</span><span class="sxs-lookup"><span data-stu-id="9730f-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="9730f-106">如果您想要傳遞引數的資料型別不同於其對應的參數，例如`Byte`至`String`，您可以設定的型別檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 至`Off`。</span><span class="sxs-lookup"><span data-stu-id="9730f-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="9730f-107">如果`Option Strict`是`On`，您必須使用擴展轉換或明確轉換的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9730f-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="9730f-108">如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="9730f-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="9730f-109">如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="9730f-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="9730f-110">若要將一個或多個引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="9730f-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="9730f-111">在呼叫的陳述式，請依照下列程序名稱，加上括弧。</span><span class="sxs-lookup"><span data-stu-id="9730f-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="9730f-112">放在括號內的引數清單。</span><span class="sxs-lookup"><span data-stu-id="9730f-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="9730f-113">包含引數，每個必要參數定義程序，並以逗號分隔的引數。</span><span class="sxs-lookup"><span data-stu-id="9730f-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="9730f-114">請確定每個引數是有效的運算式評估為資料類型轉換成程序的型別定義為對應參數。</span><span class="sxs-lookup"><span data-stu-id="9730f-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="9730f-115">如果參數定義成[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)，您可以將它包含引數清單中，或省略它。</span><span class="sxs-lookup"><span data-stu-id="9730f-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="9730f-116">如果您省略它，此程序會使用定義為該參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="9730f-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="9730f-117">如果您省略引數`Optional`參數且沒有另一個參數之後的參數清單中，您可以省略引數的位置標記引數清單中額外的逗號。</span><span class="sxs-lookup"><span data-stu-id="9730f-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="9730f-118">下列範例會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="9730f-118">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     <span data-ttu-id="9730f-119">[!code-vb[VbVbcnProcedures #&34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9730f-119">[!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="9730f-120">上述範例，提供必要的第一個引數，也就是要顯示的訊息字串。</span><span class="sxs-lookup"><span data-stu-id="9730f-120">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="9730f-121">它省略引數為選擇性的第二個參數，指定要顯示在訊息方塊上的按鈕。</span><span class="sxs-lookup"><span data-stu-id="9730f-121">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="9730f-122">呼叫不會提供一個值，因為`MsgBox`會使用預設值， `MsgBoxStyle.OKOnly`，這只會顯示**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9730f-122">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="9730f-123">引數清單中的第二個逗號標示省略第二個引數的位置和最後一個字串傳遞給選擇性第三個參數`MsgBox`，這是顯示在標題列中的文字。</span><span class="sxs-lookup"><span data-stu-id="9730f-123">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9730f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9730f-124">See Also</span></span>  
 <span data-ttu-id="9730f-125">[Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-125">[Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="9730f-126"> [Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-126"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="9730f-127"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-127"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="9730f-128"> [運算子程序](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-128"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="9730f-129"> [如何︰ 定義程序參數](./how-to-define-a-parameter-for-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-129"> [How to: Define a Parameter for a Procedure](./how-to-define-a-parameter-for-a-procedure.md) </span></span>  
<span data-ttu-id="9730f-130"> [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-130"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="9730f-131"> [遞迴程序](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-131"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="9730f-132"> [多載化程序](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-132"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="9730f-133"> [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="9730f-133"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="9730f-134"> [物件導向程式設計](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="9730f-134"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>
