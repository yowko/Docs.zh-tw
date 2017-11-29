---
title: "如何：列印表單的工作區 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42dd3c809ff0a1594350e252d4c4aa2f0ec004
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="50833-102">如何：列印表單的工作區 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50833-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="50833-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您快速列印表單的影像，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。</span><span class="sxs-lookup"><span data-stu-id="50833-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="50833-104">下列程序示範如何只列印表單的工作區，而不列印標題列、框線和捲軸。</span><span class="sxs-lookup"><span data-stu-id="50833-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="50833-105">Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。</span><span class="sxs-lookup"><span data-stu-id="50833-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="50833-106">列印表單的工作區</span><span class="sxs-lookup"><span data-stu-id="50833-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="50833-107">在 [工具箱] 中，按一下 [Visual Basic PowerPacks]  索引標籤，然後將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="50833-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="50833-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件會加入元件匣中。</span><span class="sxs-lookup"><span data-stu-id="50833-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="50833-109">在 [屬性]  視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。</span><span class="sxs-lookup"><span data-stu-id="50833-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="50833-110">在適當的事件處理常式 (例如 [列印] `Click`**的**`Button`事件處理常式) 中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="50833-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="50833-111">在某些作業系統上，可能無法正確列印由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形。</span><span class="sxs-lookup"><span data-stu-id="50833-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="50833-112">在這種情況下，請使用相容的列印方法： `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="50833-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50833-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50833-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="50833-114">PrintForm 元件</span><span class="sxs-lookup"><span data-stu-id="50833-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="50833-115">操作說明：列印表單的工作區和非工作區</span><span class="sxs-lookup"><span data-stu-id="50833-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="50833-116">操作說明：列印可捲動的表單</span><span class="sxs-lookup"><span data-stu-id="50833-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
