---
title: "如何：在 Windows Forms 應用程式中顯示預覽列印"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e705575b8c3acdcc3d92b985c59b60e7310dce7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>如何：在 Windows Forms 應用程式中顯示預覽列印
您可以使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項，讓使用者顯示文件，通常在列印之前。  
  
 若要這樣做，您需要指定的執行個體<xref:System.Drawing.Printing.PrintDocument>類別; 這是要列印文件。 如需有關使用預覽列印與<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[如何： 列印 Windows Form 使用預覽列印](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)。  
  
> [!NOTE]
>  若要使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項在執行階段，使用者必須已安裝印表機他們在電腦上，在本機或透過網路，因為這是部分如何<xref:System.Windows.Forms.PrintPreviewDialog>元件決定文件列印的樣子。  
  
 <xref:System.Windows.Forms.PrintPreviewDialog>控制使用<xref:System.Drawing.Printing.PrinterSettings>類別。 此外，<xref:System.Windows.Forms.PrintPreviewDialog>控制使用<xref:System.Drawing.Printing.PageSettings>類別，就如同<xref:System.Windows.Forms.PrintPreviewDialog>元件。 列印文件中指定<xref:System.Windows.Forms.PrintPreviewDialog>控制項的<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>屬性是指兩個執行個體<xref:System.Drawing.Printing.PrinterSettings>和<xref:System.Drawing.Printing.PageSettings>類別，以及這些用來呈現預覽視窗中的文件。  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>若要檢視使用 PrintPreviewDialog 控制項的頁面  
  
-   使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並指定要使用的 <xref:System.Drawing.Printing.PrintDocument> 。  
  
     在下列程式碼範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟執行個體<xref:System.Windows.Forms.PrintPreviewDialog>控制項。 列印文件中指定<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性。 在下列範例中，指定不列印的文件。  
  
     這個範例需要您的表單具有<xref:System.Windows.Forms.Button>控制項，<xref:System.Drawing.Printing.PrintDocument>名元件`myDocument`，和<xref:System.Windows.Forms.PrintPreviewDialog>控制項。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Windows Forms 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
