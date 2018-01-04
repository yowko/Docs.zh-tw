---
title: "如何：列印 Windows Form 中的圖形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 634689b0b39510cbcc9dc49b1f4717e7e07f88d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="606fc-102">如何：列印 Windows Form 中的圖形</span><span class="sxs-lookup"><span data-stu-id="606fc-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="606fc-103">通常您會想要列印在 Windows 架構應用程式中的圖形。</span><span class="sxs-lookup"><span data-stu-id="606fc-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="606fc-104"><xref:System.Drawing.Graphics>類別提供方法來繪製至裝置，例如螢幕或印表機的物件。</span><span class="sxs-lookup"><span data-stu-id="606fc-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="606fc-105">若要列印的圖形</span><span class="sxs-lookup"><span data-stu-id="606fc-105">To print graphics</span></span>  
  
1.  <span data-ttu-id="606fc-106">新增<xref:System.Drawing.Printing.PrintDocument>元件加入至表單。</span><span class="sxs-lookup"><span data-stu-id="606fc-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="606fc-107">在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式，使用<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>指示何種列印圖形上的印表機的類別。</span><span class="sxs-lookup"><span data-stu-id="606fc-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="606fc-108">下列程式碼範例顯示用來建立的藍色橢圓形的週框矩形內的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="606fc-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="606fc-109">矩形的位置及尺寸： 開始 100，150 250 寬度與高度為 250。</span><span class="sxs-lookup"><span data-stu-id="606fc-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     <span data-ttu-id="606fc-110">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="606fc-110">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="606fc-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="606fc-111">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="606fc-112">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="606fc-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
