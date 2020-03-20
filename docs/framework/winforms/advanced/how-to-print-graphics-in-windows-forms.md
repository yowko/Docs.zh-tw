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
# <a name="how-to-print-graphics-in-windows-forms"></a>如何：列印 Windows Form 中的圖形
通常，您需要在基於 Windows 的應用程式中列印圖形。 類<xref:System.Drawing.Graphics>提供將物件繪製到設備（如螢幕或印表機）的方法。  
  
### <a name="to-print-graphics"></a>列印圖形  
  
1. 向表單<xref:System.Drawing.Printing.PrintDocument>添加元件。  
  
2. 在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>，使用<xref:System.Drawing.Printing.PrintPageEventArgs>類的屬性指示印表機列印的圖形類型。  
  
     下面的代碼示例顯示了用於在邊界矩形內創建藍色橢圓的事件處理常式。 矩形具有以下位置和尺寸：從 100 開始，150 開頭，寬度為 250，高度為 250。  
  
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
  
     （視覺 C# 和視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows Forms 列印支援](windows-forms-print-support.md)
