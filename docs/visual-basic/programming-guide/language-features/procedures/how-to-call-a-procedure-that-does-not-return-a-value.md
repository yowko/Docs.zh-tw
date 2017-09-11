---
title: "如何︰ 呼叫不傳回值 (Visual Basic) 的程序 |Microsoft 文件"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
ms.openlocfilehash: 26120b763d2ecedb3aa43adb08e4c87c2b1e0be1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="7f2f9-102">如何：呼叫不傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f2f9-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="7f2f9-103">A`Sub`程序不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="7f2f9-104">明確呼叫它，以獨立的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="7f2f9-105">您無法直接使用其名稱在運算式中的呼叫它。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="7f2f9-106">若要呼叫子函數程序</span><span class="sxs-lookup"><span data-stu-id="7f2f9-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="7f2f9-107">指定的名稱`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="7f2f9-108">請依照下列程序名稱以括號括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="7f2f9-109">如果不有任何引數，您可以省略括號。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="7f2f9-110">不過，使用括號會讓您的程式碼容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="7f2f9-111">將引數放在括號，以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="7f2f9-112">確定您提供的相同順序的引數，`Sub`程序定義對應的參數。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="7f2f9-113">下列範例會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>函式來啟動應用程式視窗。</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="7f2f9-113">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="7f2f9-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>使用視窗標題做為其唯一引數。</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="7f2f9-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="7f2f9-115">它不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="7f2f9-116">如果未執行 「 記事本 」 處理程序，則會擲回<xref:System.ArgumentException>.</xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="7f2f9-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="7f2f9-117">`Shell`程序假設應用程式中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="7f2f9-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     <span data-ttu-id="7f2f9-118">[!code-vb[VbVbalrCatRef #&11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7f2f9-118">[!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2f9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f2f9-119">See Also</span></span>  
 <span data-ttu-id="7f2f9-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A></span><span class="sxs-lookup"><span data-stu-id="7f2f9-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></span></span>   
 <span data-ttu-id="7f2f9-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="7f2f9-121"><xref:System.ArgumentException></span></span>   
<span data-ttu-id="7f2f9-122"> [程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="7f2f9-122"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="7f2f9-123"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7f2f9-123"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="7f2f9-124"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="7f2f9-124"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="7f2f9-125"> [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7f2f9-125"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="7f2f9-126"> [如何︰ 建立程序](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7f2f9-126"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="7f2f9-127"> [如何︰ 呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="7f2f9-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="7f2f9-128"> [如何︰ 在 Visual Basic 中呼叫事件處理常式](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="7f2f9-128"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
