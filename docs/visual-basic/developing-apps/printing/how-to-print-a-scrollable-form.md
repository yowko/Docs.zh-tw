---
title: 如何：列印可捲動的表單 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: 4a509b7c48f2bff705bc95e58fb88252cb8ca4b9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779415"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="32fb2-102">如何：列印可捲動的表單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32fb2-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="32fb2-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。</span><span class="sxs-lookup"><span data-stu-id="32fb2-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="32fb2-104">根據預設，只會列印表單的目前可見部分；如果使用者已在執行階段調整表單的大小，影像可能無法如預期般列印。</span><span class="sxs-lookup"><span data-stu-id="32fb2-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="32fb2-105">下列程序示範如何列印可捲動表單的完整工作區，而不論表單是否已調整大小。</span><span class="sxs-lookup"><span data-stu-id="32fb2-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="32fb2-106">在 Visual Studio 中，已不再包含 PowerPack 控制項，但您可以下載從[下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)。</span><span class="sxs-lookup"><span data-stu-id="32fb2-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="32fb2-107">列印可捲動表單的完整工作區</span><span class="sxs-lookup"><span data-stu-id="32fb2-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="32fb2-108">在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="32fb2-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="32fb2-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。</span><span class="sxs-lookup"><span data-stu-id="32fb2-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="32fb2-110">在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。</span><span class="sxs-lookup"><span data-stu-id="32fb2-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="32fb2-111">在適當的事件處理常式 (例如 [列印] `Click`**的**`Button`事件處理常式) 中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="32fb2-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="32fb2-112">在某些作業系統上，可能無法正確列印由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形。</span><span class="sxs-lookup"><span data-stu-id="32fb2-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="32fb2-113">在這種情況下，您將無法使用 `Scrollable` 參數進行列印。</span><span class="sxs-lookup"><span data-stu-id="32fb2-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fb2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32fb2-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="32fb2-115">PrintForm 元件</span><span class="sxs-lookup"><span data-stu-id="32fb2-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="32fb2-116">操作說明：列印表單的工作區</span><span class="sxs-lookup"><span data-stu-id="32fb2-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="32fb2-117">操作說明：列印表單的工作區和非工作區</span><span class="sxs-lookup"><span data-stu-id="32fb2-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
