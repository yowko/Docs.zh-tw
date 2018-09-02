---
title: 如何：列印表單的工作區和非工作區 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408435"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="e7692-102">如何：列印表單的工作區和非工作區 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7692-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="e7692-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您完全依照螢幕所示，快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。</span><span class="sxs-lookup"><span data-stu-id="e7692-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="e7692-104">下列程序示範如何列印表單，包括工作區和非工作區。</span><span class="sxs-lookup"><span data-stu-id="e7692-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="e7692-105">非工作區包含標題列、框線和捲軸。</span><span class="sxs-lookup"><span data-stu-id="e7692-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="e7692-106">在 Visual Studio 中，已不再包含 PowerPack 控制項，但您可以下載從[下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)。</span><span class="sxs-lookup"><span data-stu-id="e7692-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="e7692-107">列印表單的工作區和非工作區</span><span class="sxs-lookup"><span data-stu-id="e7692-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="e7692-108">在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="e7692-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="e7692-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。</span><span class="sxs-lookup"><span data-stu-id="e7692-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="e7692-110">在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。</span><span class="sxs-lookup"><span data-stu-id="e7692-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="e7692-111">在適當的事件處理常式 (例如 [列印] `Click` 的 `Button`事件處理常式) 中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7692-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e7692-112">在某些作業系統上，可能無法正確列印由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形。</span><span class="sxs-lookup"><span data-stu-id="e7692-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="e7692-113">在這種情況下，請使用相容的列印方法： `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`)。</span><span class="sxs-lookup"><span data-stu-id="e7692-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7692-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7692-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="e7692-115">PrintForm 元件</span><span class="sxs-lookup"><span data-stu-id="e7692-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="e7692-116">操作說明：列印可捲動的表單</span><span class="sxs-lookup"><span data-stu-id="e7692-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
