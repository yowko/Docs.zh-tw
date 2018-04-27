---
title: 如何：呼叫不傳回值的程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb9f13d5387f4a440a7fdd39c5e8f50cb8d56270
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="b61c3-102">如何：呼叫不傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b61c3-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="b61c3-103">A`Sub`程序不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="b61c3-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="b61c3-104">明確呼叫它，以獨立的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="b61c3-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="b61c3-105">您無法只使用其名稱，在運算式中的呼叫它。</span><span class="sxs-lookup"><span data-stu-id="b61c3-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="b61c3-106">若要呼叫 Sub 程序</span><span class="sxs-lookup"><span data-stu-id="b61c3-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="b61c3-107">指定的名稱`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="b61c3-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="b61c3-108">請依照下列程序名稱與括號來括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="b61c3-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="b61c3-109">如果有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="b61c3-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="b61c3-110">不過，使用括號可讓您的程式碼更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="b61c3-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="b61c3-111">將引數放在括號，並以逗號分隔的引數清單。</span><span class="sxs-lookup"><span data-stu-id="b61c3-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="b61c3-112">確定您提供的相同順序的引數，`Sub`程序所定義的對應參數。</span><span class="sxs-lookup"><span data-stu-id="b61c3-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="b61c3-113">下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>函式可啟動應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="b61c3-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="b61c3-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 使用視窗標題做為其唯一的引數。</span><span class="sxs-lookup"><span data-stu-id="b61c3-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="b61c3-115">呼叫程式碼不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="b61c3-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="b61c3-116">如果未執行 「 記事本 」 處理程序，此範例會擲回<xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="b61c3-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="b61c3-117">`Shell`程序會假設應用程式是在指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="b61c3-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b61c3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b61c3-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="b61c3-119">程序</span><span class="sxs-lookup"><span data-stu-id="b61c3-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b61c3-120">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="b61c3-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="b61c3-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="b61c3-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b61c3-122">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="b61c3-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="b61c3-123">如何：建立程序</span><span class="sxs-lookup"><span data-stu-id="b61c3-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="b61c3-124">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="b61c3-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="b61c3-125">如何： 在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="b61c3-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
