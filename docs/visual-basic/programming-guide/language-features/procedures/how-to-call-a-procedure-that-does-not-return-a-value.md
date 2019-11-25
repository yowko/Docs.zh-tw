---
title: 如何：呼叫不傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3a5de98c6edf795a11bd9f0465aa6919f09eebfa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340951"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="32b8f-102">如何：呼叫不傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32b8f-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="32b8f-103">A `Sub` procedure does not return a value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="32b8f-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="32b8f-104">You call it explicitly with a stand-alone calling statement.</span><span class="sxs-lookup"><span data-stu-id="32b8f-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="32b8f-105">You cannot call it by simply using its name within an expression.</span><span class="sxs-lookup"><span data-stu-id="32b8f-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="32b8f-106">To call a Sub procedure</span><span class="sxs-lookup"><span data-stu-id="32b8f-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="32b8f-107">Specify the name of the `Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="32b8f-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="32b8f-108">Follow the procedure name with parentheses to enclose the argument list.</span><span class="sxs-lookup"><span data-stu-id="32b8f-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="32b8f-109">If there are no arguments, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="32b8f-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="32b8f-110">However, using the parentheses makes your code easier to read.</span><span class="sxs-lookup"><span data-stu-id="32b8f-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="32b8f-111">Place the arguments in the argument list within the parentheses, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="32b8f-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="32b8f-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span><span class="sxs-lookup"><span data-stu-id="32b8f-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="32b8f-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span><span class="sxs-lookup"><span data-stu-id="32b8f-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="32b8f-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span><span class="sxs-lookup"><span data-stu-id="32b8f-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="32b8f-115">It does not return a value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="32b8f-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="32b8f-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="32b8f-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="32b8f-117">The `Shell` procedure assumes the applications are in the paths specified.</span><span class="sxs-lookup"><span data-stu-id="32b8f-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="32b8f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="32b8f-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="32b8f-119">程序</span><span class="sxs-lookup"><span data-stu-id="32b8f-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="32b8f-120">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="32b8f-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="32b8f-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="32b8f-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="32b8f-122">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="32b8f-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="32b8f-123">如何：建立程序</span><span class="sxs-lookup"><span data-stu-id="32b8f-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="32b8f-124">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="32b8f-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="32b8f-125">How to: Call an Event Handler in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32b8f-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
