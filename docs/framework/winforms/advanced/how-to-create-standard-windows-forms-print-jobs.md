---
title: 如何：建立標準的 Windows Form 列印工作
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
ms.openlocfilehash: b580268a6af3f56f240a1c511c3d473a4a5ddc15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>如何：建立標準的 Windows Form 列印工作
列印 Windows Form 中的基礎是<xref:System.Drawing.Printing.PrintDocument>元件 — 更具體來說，<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。 藉由撰寫程式碼來處理<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件，您可以指定要列印的內容，以及如何進行列印。  
  
### <a name="to-create-a-print-job"></a>若要建立列印工作  
  
1.  新增<xref:System.Drawing.Printing.PrintDocument>元件加入至表單。  
  
2.  撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  
  
     您必須撰寫您自己的列印邏輯的程式碼。 此外，您必須指定要列印的資料。  
  
     在下列程式碼範例中，建立範例圖形中以紅色矩形的圖形<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式，以做為要列印的資料。  
  
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
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
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
  
     您也可以撰寫程式碼<xref:System.Drawing.Printing.PrintDocument.BeginPrint>和<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件，可能包括整數，代表總頁數列印，隨著每一頁列印會遞減。  
  
    > [!NOTE]
    >  您可以加入<xref:System.Windows.Forms.PrintDialog>元件加入至表單，以全新且有效的使用者介面 (UI) 提供給您的使用者。 設定<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性<xref:System.Windows.Forms.PrintDialog>元件可讓您設定與列印相關屬性的文件您正在使用您的表單上。 如需有關<xref:System.Windows.Forms.PrintDialog>元件，請參閱[PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)。  
  
     如需特定的 Windows Form 列印工作，包括如何建立列印工作，以程式設計的方式，請參閱<xref:System.Drawing.Printing.PrintPageEventArgs>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
