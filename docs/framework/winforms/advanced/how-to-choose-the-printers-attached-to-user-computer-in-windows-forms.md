---
title: 如何：選擇連接到使用者電腦的印表機
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182604"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>如何：在 Windows Form 中選擇附加至使用者電腦的印表機
通常，使用者會想要選擇列印到非預設的印表機。 使用 <xref:System.Windows.Forms.PrintDialog> 元件，即可讓使用者從目前安裝的印表機中選擇印表機。 透過 <xref:System.Windows.Forms.PrintDialog> 元件，擷取 <xref:System.Windows.Forms.DialogResult> 元件的 <xref:System.Windows.Forms.PrintDialog> 並將其用來選取印表機。  
  
 在下列程序中，選取要列印至預設印表機的文字檔案。 然後具現化 <xref:System.Windows.Forms.PrintDialog> 類別。  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>選擇印表機，然後列印檔案  
  
1. 選擇要使用該元件的<xref:System.Windows.Forms.PrintDialog>印表機。  
  
     在下列程式碼範例中，有兩個要處理的事件。 <xref:System.Windows.Forms.Button>在第一個<xref:System.Windows.Forms.Control.Click>控制項事件中，<xref:System.Windows.Forms.PrintDialog>將具現化類，並在<xref:System.Windows.Forms.DialogResult>屬性中捕獲使用者選擇的印表機。  
  
     在第二個事件中，<xref:System.Drawing.Printing.PrintDocument.PrintPage><xref:System.Drawing.Printing.PrintDocument>元件的事件，將示例文檔列印到指定的印表機。  
  
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
  
     （視覺 C# 和視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。  
  
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

- [Windows Forms 列印支援](windows-forms-print-support.md)
