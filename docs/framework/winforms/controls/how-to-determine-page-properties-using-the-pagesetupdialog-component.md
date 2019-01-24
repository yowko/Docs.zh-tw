---
title: HOW TO：使用 PageSetupDialog 元件決定頁面屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: c72ed5e6db6149f2161e0586c783e041eb0b731b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713534"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>HOW TO：使用 PageSetupDialog 元件決定頁面屬性
[PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) 元件會向文件使用者呈現配置、紙張大小和其他頁面配置選項。  
  
 您需要指定 <xref:System.Drawing.Printing.PrintDocument> 類別執行個體，這是要列印文件。 此外，使用者必須在其電腦上安裝印表機 (本機或透過網路)，因為這有一部分是 <xref:System.Windows.Forms.PageSetupDialog> 元件如何決定呈現給使用者的頁面格式選項。  
  
 使用 <xref:System.Windows.Forms.PageSetupDialog> 元件的重要層面是如何與 <xref:System.Drawing.Printing.PageSettings> 類別互動。 <xref:System.Drawing.Printing.PageSettings> 類別是用來指定可修改頁面列印方式的設定，例如紙張列印方向，頁面大小和邊界。 所有這些設定都是呈現為 <xref:System.Drawing.Printing.PageSettings> 類別的屬性。 <xref:System.Windows.Forms.PageSetupDialog> 類別會針對與文件相關聯 (並呈現為 <xref:System.Drawing.Printing.PageSettings> 屬性) 的指定 <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> 類別執行個體來修改這些屬性值。  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>使用 PageSetupDialog 元件決定頁面屬性  
  
1.  使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並指定要使用的 <xref:System.Drawing.Printing.PrintDocument> 。  
  
     在下列範例中， <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式會開啟 <xref:System.Windows.Forms.PageSetupDialog> 元件執行個體。 現有的文件指定於 <xref:System.Windows.Forms.PageSetupDialog.Document%2A> 屬性中，而且其 <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> 屬性設定為 `false`。  
  
     此範例假設您的表單具有<xref:System.Windows.Forms.Button>控制<xref:System.Drawing.Printing.PrintDocument>名元件`myDocument`，和<xref:System.Windows.Forms.PageSetupDialog>元件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.PageSetupDialog>
- [如何：建立標準的 Windows Forms 列印工作](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
