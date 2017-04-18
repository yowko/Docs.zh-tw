---
title: "如何：在 Windows Form 應用程式中顯示預覽列印 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], 預覽列印"
  - "預覽列印, 顯示"
  - "列印 [Windows Form], 預覽列印"
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：在 Windows Form 應用程式中顯示預覽列印
您可以使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項讓使用者顯示文件 \(通常在列印之前\)。  
  
 若要執行這項作業，您需要指定 <xref:System.Drawing.Printing.PrintDocument> 類別的執行個體，也就是要列印的文件。  如需以 <xref:System.Drawing.Printing.PrintDocument> 元件使用預覽列印的詳細資訊，請參閱 [如何：使用預覽列印在 Windows Form 中進行列印](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)。  
  
> [!NOTE]
>  若要在執行階段使用 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項，使用者的電腦上必須安裝有印表機 \(無論是本機或透過網路\)，因為 <xref:System.Windows.Forms.PrintPreviewDialog> 元件在決定文件列印外觀時，有部分要透過安裝的印表機來決定。  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項使用 <xref:System.Drawing.Printing.PrinterSettings> 類別。  此外，<xref:System.Windows.Forms.PrintPreviewDialog> 控制項則使用 <xref:System.Drawing.Printing.PageSettings> 類別，就如同 <xref:System.Windows.Forms.PrintPreviewDialog> 元件。  在 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項的 <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> 屬性中指定的列印文件是指 <xref:System.Drawing.Printing.PrinterSettings> 和 <xref:System.Drawing.Printing.PageSettings> 類別的執行個體，而這些執行個體會用來在預覽視窗中呈現文件。  
  
### 若要使用 PrintPreviewDialog 控制項檢視網頁  
  
-   使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，指定要使用的 <xref:System.Drawing.Printing.PrintDocument>。  
  
     在下列程式碼範例中，<xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式會開啟 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項的執行個體。  列印文件會在 <xref:System.Windows.Forms.PrintDialog.Document%2A> 屬性中加以指定。  在下列的範例中沒有指定列印文件。  
  
     此範例需要您的表單具有 <xref:System.Windows.Forms.Button> 控制項、名為 `myDocument` 的 <xref:System.Drawing.Printing.PrintDocument> 控制項以及 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 請參閱  
 [PrintDocument 元件](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)   
 [PrintPreviewDialog 控制項](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [Windows Form 列印支援](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [Windows Form](../../../../docs/framework/winforms/index.md)