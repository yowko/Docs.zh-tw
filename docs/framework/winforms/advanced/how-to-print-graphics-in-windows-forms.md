---
title: HOW TO：列印 Windows Forms 中的圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 55459482d0994c581164128b17c08a7ca90d0717
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339095"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="8a489-102">HOW TO：列印 Windows Forms 中的圖形</span><span class="sxs-lookup"><span data-stu-id="8a489-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="8a489-103">通常，您要列印您以 Windows 為基礎的應用程式中的圖形。</span><span class="sxs-lookup"><span data-stu-id="8a489-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="8a489-104"><xref:System.Drawing.Graphics>類別會提供物件繪製到螢幕或印表機等裝置的方法。</span><span class="sxs-lookup"><span data-stu-id="8a489-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="8a489-105">若要列印的圖形</span><span class="sxs-lookup"><span data-stu-id="8a489-105">To print graphics</span></span>  
  
1. <span data-ttu-id="8a489-106">新增<xref:System.Drawing.Printing.PrintDocument>元件至您的表單。</span><span class="sxs-lookup"><span data-stu-id="8a489-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="8a489-107">在 <xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式，使用<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>類別，以指示何種列印圖形上的印表機。</span><span class="sxs-lookup"><span data-stu-id="8a489-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="8a489-108">下列程式碼範例顯示用來建立藍色的橢圓形的週框矩形內的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8a489-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="8a489-109">矩形的下列位置和維度： 開始 100，150，使用為 250 的寬度和高度為 250。</span><span class="sxs-lookup"><span data-stu-id="8a489-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="8a489-110">(Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8a489-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a489-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a489-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="8a489-112">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="8a489-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
