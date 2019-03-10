---
title: HOW TO：顯示預覽列印在 Windows Forms 應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 13510086edb13ff54f5551296c1b64c51873f649
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715356"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>HOW TO：顯示預覽列印在 Windows Forms 應用程式
您可以使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項，讓使用者以顯示文件，通常要列印之前。  
  
 若要這樣做，您需要指定的執行個體<xref:System.Drawing.Printing.PrintDocument>類別; 這是要列印的文件。 如需有關使用使用預覽列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[How to:使用預覽列印 Windows Forms 中列印](../advanced/how-to-print-in-windows-forms-using-print-preview.md)。  
  
> [!NOTE]
>  若要使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項在執行階段，使用者必須擁有在本機或透過網路，在他們的電腦上安裝印表機，這有一部分是如何<xref:System.Windows.Forms.PrintPreviewDialog>元件可讓您判斷文件列印的樣子。  
  
 <xref:System.Windows.Forms.PrintPreviewDialog>控制項會使用<xref:System.Drawing.Printing.PrinterSettings>類別。 此外，<xref:System.Windows.Forms.PrintPreviewDialog>控制項會使用<xref:System.Drawing.Printing.PageSettings>類別，就如同<xref:System.Windows.Forms.PrintPreviewDialog>元件。 列印文件中指定<xref:System.Windows.Forms.PrintPreviewDialog>控制項的<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>屬性會參考兩個執行個體<xref:System.Drawing.Printing.PrinterSettings>和<xref:System.Drawing.Printing.PageSettings>類別，以及這些用來呈現預覽視窗中的文件。  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>若要檢視使用 PrintPreviewDialog 控制項的頁面  
  
-   使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並指定要使用的 <xref:System.Drawing.Printing.PrintDocument> 。  
  
     在下列程式碼範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟的執行個體<xref:System.Windows.Forms.PrintPreviewDialog>控制項。 列印文件中指定<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性。 在下列範例中，指定不列印的文件。  
  
     這個範例需要您的表單具有<xref:System.Windows.Forms.Button>控制<xref:System.Drawing.Printing.PrintDocument>名元件`myDocument`，和<xref:System.Windows.Forms.PrintPreviewDialog>控制項。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱
- [PrintDocument 元件](printdocument-component-windows-forms.md)
- [PrintPreviewDialog 控制項](printpreviewdialog-control-windows-forms.md)
- [Windows Forms 列印支援](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
