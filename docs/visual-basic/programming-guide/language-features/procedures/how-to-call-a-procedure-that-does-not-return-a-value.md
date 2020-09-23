---
title: 如何：呼叫不傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 2686a4d9dc10cde209f558771feeb5ba4f4ccb21
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075001"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="d0884-102">如何：呼叫不傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0884-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>

<span data-ttu-id="d0884-103">程式不 `Sub` 會傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="d0884-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="d0884-104">您可以使用獨立的呼叫語句來明確呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d0884-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="d0884-105">您無法直接在運算式中使用其名稱來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d0884-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="d0884-106">若要呼叫 Sub 程式</span><span class="sxs-lookup"><span data-stu-id="d0884-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="d0884-107">指定程式的名稱 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d0884-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="d0884-108">請以括弧括住程式名稱，以括住引數清單。</span><span class="sxs-lookup"><span data-stu-id="d0884-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d0884-109">如果沒有引數，您可以選擇性地省略括弧。</span><span class="sxs-lookup"><span data-stu-id="d0884-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="d0884-110">不過，使用括弧可讓您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="d0884-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="d0884-111">將引數清單中的引數放在括弧內，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="d0884-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d0884-112">請務必以程式定義對應參數的相同順序提供引數 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="d0884-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="d0884-113">下列範例會呼叫 Visual Basic 函 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 式來啟用應用程式視窗。</span><span class="sxs-lookup"><span data-stu-id="d0884-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="d0884-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 將視窗標題作為其唯一引數。</span><span class="sxs-lookup"><span data-stu-id="d0884-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="d0884-115">它不會傳回值給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0884-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="d0884-116">如果「記事本」處理常式未執行，此範例會擲回 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="d0884-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="d0884-117">此 `Shell` 程式假設應用程式位於指定的路徑中。</span><span class="sxs-lookup"><span data-stu-id="d0884-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="d0884-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0884-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="d0884-119">程序</span><span class="sxs-lookup"><span data-stu-id="d0884-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d0884-120">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="d0884-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d0884-121">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="d0884-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d0884-122">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="d0884-122">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d0884-123">如何：建立程序</span><span class="sxs-lookup"><span data-stu-id="d0884-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="d0884-124">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="d0884-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="d0884-125">如何：在 Visual Basic 中呼叫事件處理常式</span><span class="sxs-lookup"><span data-stu-id="d0884-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
