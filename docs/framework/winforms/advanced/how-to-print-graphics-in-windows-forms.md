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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339095"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>HOW TO：列印 Windows Forms 中的圖形
通常，您要列印您以 Windows 為基礎的應用程式中的圖形。 <xref:System.Drawing.Graphics>類別會提供物件繪製到螢幕或印表機等裝置的方法。  
  
### <a name="to-print-graphics"></a>若要列印的圖形  
  
1. 新增<xref:System.Drawing.Printing.PrintDocument>元件至您的表單。  
  
2. 在 <xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式，使用<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>屬性<xref:System.Drawing.Printing.PrintPageEventArgs>類別，以指示何種列印圖形上的印表機。  
  
     下列程式碼範例顯示用來建立藍色的橢圓形的週框矩形內的事件處理常式。 矩形的下列位置和維度： 開始 100，150，使用為 250 的寬度和高度為 250。  
  
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
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
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
- [Windows Form 列印支援](windows-forms-print-support.md)
