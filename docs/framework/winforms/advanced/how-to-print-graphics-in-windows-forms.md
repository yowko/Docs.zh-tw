---
title: 如何：列印圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 15f3a507839430ce058302e7f5abd317ef84626f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182528"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="a3996-102">如何：列印 Windows Form 中的圖形</span><span class="sxs-lookup"><span data-stu-id="a3996-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="a3996-103">通常，您需要在基於 Windows 的應用程式中列印圖形。</span><span class="sxs-lookup"><span data-stu-id="a3996-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="a3996-104">類<xref:System.Drawing.Graphics>提供將物件繪製到設備（如螢幕或印表機）的方法。</span><span class="sxs-lookup"><span data-stu-id="a3996-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="a3996-105">列印圖形</span><span class="sxs-lookup"><span data-stu-id="a3996-105">To print graphics</span></span>  
  
1. <span data-ttu-id="a3996-106">向表單<xref:System.Drawing.Printing.PrintDocument>添加元件。</span><span class="sxs-lookup"><span data-stu-id="a3996-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="a3996-107">在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>，使用<xref:System.Drawing.Printing.PrintPageEventArgs>類的屬性指示印表機列印的圖形類型。</span><span class="sxs-lookup"><span data-stu-id="a3996-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="a3996-108">下面的代碼示例顯示了用於在邊界矩形內創建藍色橢圓的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a3996-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="a3996-109">矩形具有以下位置和尺寸：從 100 開始，150 開頭，寬度為 250，高度為 250。</span><span class="sxs-lookup"><span data-stu-id="a3996-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="a3996-110">（視覺 C# 和視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a3996-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3996-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3996-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="a3996-112">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="a3996-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
