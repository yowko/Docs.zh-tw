---
title: HOW TO：呼叫程序不會傳回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 6e3ce2a184ca5411a6a016929a16bf3d67e669ca
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335468"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="595df-102">HOW TO：呼叫程序不會傳回值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="595df-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="595df-103">A`Sub`程序不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="595df-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="595df-104">明確呼叫它，以獨立的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="595df-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="595df-105">您無法直接使用其名稱，在運算式內呼叫它。</span><span class="sxs-lookup"><span data-stu-id="595df-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="595df-106">若要呼叫子函數程序</span><span class="sxs-lookup"><span data-stu-id="595df-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="595df-107">指定的名稱`Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="595df-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="595df-108">程序名稱後面加上括號括住的引數清單。</span><span class="sxs-lookup"><span data-stu-id="595df-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="595df-109">如果不有任何引數，您可以選擇性地省略括號。</span><span class="sxs-lookup"><span data-stu-id="595df-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="595df-110">不過，使用括號可讓您的程式碼更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="595df-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="595df-111">以括弧括住，並以逗號分隔的引數清單括住的引數。</span><span class="sxs-lookup"><span data-stu-id="595df-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="595df-112">確定您提供的相同順序的引數，`Sub`程序會定義對應的參數。</span><span class="sxs-lookup"><span data-stu-id="595df-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="595df-113">下列範例會呼叫 Visual Basic<xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>函式來啟動應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="595df-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> <span data-ttu-id="595df-114">使用視窗標題做為其唯一引數。</span><span class="sxs-lookup"><span data-stu-id="595df-114">takes the window title as its sole argument.</span></span> <span data-ttu-id="595df-115">它不會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="595df-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="595df-116">如果未執行 「 記事本 」 處理程序，此範例會擲回<xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="595df-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="595df-117">`Shell`程序會假設應用程式都在指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="595df-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="595df-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="595df-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="595df-119">程序</span><span class="sxs-lookup"><span data-stu-id="595df-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="595df-120">子程序</span><span class="sxs-lookup"><span data-stu-id="595df-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="595df-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="595df-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="595df-122">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="595df-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="595df-123">HOW TO：建立程序</span><span class="sxs-lookup"><span data-stu-id="595df-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="595df-124">HOW TO：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="595df-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="595df-125">HOW TO：在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="595df-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
