---
title: 創建標準列印工作
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182574"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>如何：建立標準的 Windows Form 列印工作
在 Windows 表單中列印的基礎是<xref:System.Drawing.Printing.PrintDocument>元件，更具體地說，是<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。 通過編寫代碼來處理事件，<xref:System.Drawing.Printing.PrintDocument.PrintPage>您可以指定要列印的內容以及如何列印它。  
  
### <a name="to-create-a-print-job"></a>創建列印工作  
  
1. 向表單<xref:System.Drawing.Printing.PrintDocument>添加元件。  
  
2. 撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。  
  
     您必須編寫自己的列印邏輯代碼。 此外，您必須指定要列印的材料。  
  
     在下面的代碼示例中，將在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中創建紅色矩形形狀的示例圖形，以用作要列印的材料。  
  
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
  
     （視覺 C# 和視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。  
  
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
  
     您可能還希望為<xref:System.Drawing.Printing.PrintDocument.BeginPrint>和<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件編寫代碼，可能包括一個整數，表示每個頁面列印時要列印的頁總數。  
  
    > [!NOTE]
    > 您可以將元件添加到表單<xref:System.Windows.Forms.PrintDialog>中，以便為使用者提供乾淨高效的使用者介面 （UI）。 通過設置<xref:System.Windows.Forms.PrintDialog.Document%2A>元件的屬性，<xref:System.Windows.Forms.PrintDialog>可以設置與在表單上處理的列印文檔相關的屬性。 有關元件的詳細資訊，<xref:System.Windows.Forms.PrintDialog>請參閱[PrintDialog 元件](../controls/printdialog-component-windows-forms.md)。  
  
     有關 Windows 表單列印工作的詳細資訊，包括如何以程式設計方式創建列印工作，請參閱<xref:System.Drawing.Printing.PrintPageEventArgs>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms 列印支援](windows-forms-print-support.md)
