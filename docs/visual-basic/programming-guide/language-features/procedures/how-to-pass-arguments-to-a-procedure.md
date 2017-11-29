---
title: "如何：將引數傳遞至程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3debb4fa6e7b15f9c321ef207d0cc04181a98da2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="bbed8-102">如何：將引數傳遞至程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbed8-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="bbed8-103">當您呼叫程序時，您會遵循括號括住的引數清單的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="bbed8-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="bbed8-104">您會提供引數對應至每個必要參數的程序所定義，而您可以選擇性地提供的引數`Optional`參數。</span><span class="sxs-lookup"><span data-stu-id="bbed8-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="bbed8-105">如果您未提供`Optional`呼叫中的參數，您必須包含逗號來標示它的引數清單中的位置，如果您提供的任何後續的引數。</span><span class="sxs-lookup"><span data-stu-id="bbed8-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="bbed8-106">如果您想要傳遞的資料型別引數不同於其對應的參數，例如`Byte`至`String`，您可以設定類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 至`Off`。</span><span class="sxs-lookup"><span data-stu-id="bbed8-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="bbed8-107">如果`Option Strict`是`On`，您必須使用擴展轉換或明確轉換關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bbed8-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="bbed8-108">如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="bbed8-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="bbed8-109">如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="bbed8-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="bbed8-110">若要將一個或多個引數傳遞至程序</span><span class="sxs-lookup"><span data-stu-id="bbed8-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="bbed8-111">在呼叫的陳述式，請依照下列程序名稱，加上括弧。</span><span class="sxs-lookup"><span data-stu-id="bbed8-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="bbed8-112">放在括弧內的引數清單。</span><span class="sxs-lookup"><span data-stu-id="bbed8-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="bbed8-113">包含一個引數的每個必要參數的程序所定義，並以逗號分隔的引數。</span><span class="sxs-lookup"><span data-stu-id="bbed8-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="bbed8-114">請確定每個引數是有效的運算式評估為資料類型轉換為型別程序定義的對應參數。</span><span class="sxs-lookup"><span data-stu-id="bbed8-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="bbed8-115">如果參數定義成[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)，您可以將它包含引數清單中，或加以省略。</span><span class="sxs-lookup"><span data-stu-id="bbed8-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="bbed8-116">如果您省略它，程序會使用該參數所定義的預設值。</span><span class="sxs-lookup"><span data-stu-id="bbed8-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="bbed8-117">如果您省略的引數`Optional`參數且沒有其他參數之後參數清單中，您可以標記多餘的逗號引數清單中省略的引數的位置。</span><span class="sxs-lookup"><span data-stu-id="bbed8-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="bbed8-118">下列範例會呼叫[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>函式。</span><span class="sxs-lookup"><span data-stu-id="bbed8-118">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     <span data-ttu-id="bbed8-119">上述範例中提供必要的第一個引數，這是要顯示的訊息字串。</span><span class="sxs-lookup"><span data-stu-id="bbed8-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="bbed8-120">它會省略選擇性的第二個參數，指定要顯示在訊息方塊上的按鈕的引數。</span><span class="sxs-lookup"><span data-stu-id="bbed8-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="bbed8-121">呼叫未提供值，因為`MsgBox`會使用預設值， `MsgBoxStyle.OKOnly`，這只會顯示**確定** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bbed8-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="bbed8-122">第二個引數清單中的逗號標示省略第二個引數的位置和最後一個的字串傳遞給選擇性第三個參數`MsgBox`，這是要顯示的標題列中的文字。</span><span class="sxs-lookup"><span data-stu-id="bbed8-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbed8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbed8-123">See Also</span></span>  
 [<span data-ttu-id="bbed8-124">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="bbed8-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="bbed8-125">函式程序</span><span class="sxs-lookup"><span data-stu-id="bbed8-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="bbed8-126">屬性程序</span><span class="sxs-lookup"><span data-stu-id="bbed8-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="bbed8-127">運算子程序</span><span class="sxs-lookup"><span data-stu-id="bbed8-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="bbed8-128">如何：定義程序的參數</span><span class="sxs-lookup"><span data-stu-id="bbed8-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="bbed8-129">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="bbed8-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="bbed8-130">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="bbed8-130">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="bbed8-131">程序多載化</span><span class="sxs-lookup"><span data-stu-id="bbed8-131">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="bbed8-132">物件和類別</span><span class="sxs-lookup"><span data-stu-id="bbed8-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="bbed8-133">物件導向程式設計</span><span class="sxs-lookup"><span data-stu-id="bbed8-133">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
