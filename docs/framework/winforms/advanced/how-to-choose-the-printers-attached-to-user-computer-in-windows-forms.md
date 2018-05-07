---
title: 如何： 選擇附加至使用者的印表機&#39;s Windows Form 中的電腦
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 5f54a74dc8118d2ebcb2df7e91f229c1807b0297
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-choose-the-printers-attached-to-a-user39s-computer-in-windows-forms"></a>如何： 選擇附加至使用者的印表機&#39;s Windows Form 中的電腦
通常，使用者會想要選擇列印到非預設的印表機。 使用 <xref:System.Windows.Forms.PrintDialog> 元件，即可讓使用者從目前安裝的印表機中選擇印表機。 透過 <xref:System.Windows.Forms.PrintDialog> 元件，擷取 <xref:System.Windows.Forms.DialogResult> 元件的 <xref:System.Windows.Forms.PrintDialog> 並將其用來選取印表機。  
  
 在下列程序中，選取要列印至預設印表機的文字檔案。 然後具現化 <xref:System.Windows.Forms.PrintDialog> 類別。  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>選擇印表機，然後列印檔案  
  
1.  選取要使用印表機<xref:System.Windows.Forms.PrintDialog>元件。  
  
     在下列程式碼範例中，有兩個要處理的事件。 首先，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件，<xref:System.Windows.Forms.PrintDialog>類別具現化，和擷取使用者所選印表機是<xref:System.Windows.Forms.DialogResult>屬性。  
  
     在第二個事件中，<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件<xref:System.Drawing.Printing.PrintDocument>元件，以指定的印表機列印範例文件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
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
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
