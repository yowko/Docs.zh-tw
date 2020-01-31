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
ms.openlocfilehash: 2435b3bc14747a00d2a0fc03a9ebd21ae43c5369
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740651"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>如何：列印 Windows Form 中的圖形
通常，您會想要在以 Windows 為基礎的應用程式中列印圖形。 <xref:System.Drawing.Graphics> 類別提供將物件繪製至裝置的方法，例如螢幕或印表機。  
  
### <a name="to-print-graphics"></a>列印圖形  
  
1. 將 <xref:System.Drawing.Printing.PrintDocument> 元件新增至您的表單。  
  
2. 在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件處理常式中，使用 <xref:System.Drawing.Printing.PrintPageEventArgs> 類別的 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 屬性，指示印表機要列印的圖形類型。  
  
     下列程式碼範例顯示用來在周框矩形內建立藍色橢圓形的事件處理常式。 矩形具有下列位置和維度：從100、150開始，寬度為250，高度為250。  
  
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
  
     （視覺C#效果和C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。  
  
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
  
## <a name="see-also"></a>請參閱

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows Forms 列印支援](windows-forms-print-support.md)
