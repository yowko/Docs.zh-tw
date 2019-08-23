---
title: HOW TO：建立標準的 Windows Forms 列印工作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938235"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>作法：建立標準的 Windows Forms 列印工作
Windows Forms 中列印的基礎是<xref:System.Drawing.Printing.PrintDocument>元件, 更具體來說<xref:System.Drawing.Printing.PrintDocument.PrintPage>就是事件。 藉由撰寫程式碼來<xref:System.Drawing.Printing.PrintDocument.PrintPage>處理事件, 您可以指定要列印的內容以及列印方式。  
  
### <a name="to-create-a-print-job"></a>建立列印工作  
  
1. <xref:System.Drawing.Printing.PrintDocument>將元件新增至您的表單。  
  
2. 撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  
  
     您將必須撰寫自己的列印邏輯程式碼。 此外, 您也必須指定要列印的材質。  
  
     在下列程式碼範例中, 會在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中建立紅色矩形圖形的範例圖形, 以作為要列印的材質。  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (視覺C#效果和C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     您可能也會想要撰寫<xref:System.Drawing.Printing.PrintDocument.BeginPrint>和<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件的程式碼, 其中可能包含一個整數, 代表要列印的總頁數, 會隨著每頁列印而遞減。  
  
    > [!NOTE]
    > 您可以將<xref:System.Windows.Forms.PrintDialog>元件新增至表單, 為您的使用者提供乾淨且有效率的使用者介面 (UI)。 設定<xref:System.Windows.Forms.PrintDialog>元件<xref:System.Windows.Forms.PrintDialog.Document%2A>的屬性, 可讓您設定與您在表單上使用之列印檔案相關的屬性。 如需<xref:System.Windows.Forms.PrintDialog>元件的詳細資訊, 請參閱[PrintDialog 元件](../controls/printdialog-component-windows-forms.md)。  
  
     如需 Windows Forms 列印工作細節的詳細資訊, 包括如何以程式設計方式建立列印工作, 請<xref:System.Drawing.Printing.PrintPageEventArgs>參閱。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms 列印支援](windows-forms-print-support.md)
