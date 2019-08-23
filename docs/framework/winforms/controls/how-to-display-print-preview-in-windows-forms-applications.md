---
title: HOW TO：在 Windows Forms 應用程式中顯示預覽列印
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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929012"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="23bee-102">HOW TO：在 Windows Forms 應用程式中顯示預覽列印</span><span class="sxs-lookup"><span data-stu-id="23bee-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="23bee-103">您可以使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項, 讓使用者在列印前經常顯示檔。</span><span class="sxs-lookup"><span data-stu-id="23bee-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="23bee-104">若要這樣做, 您必須指定<xref:System.Drawing.Printing.PrintDocument>類別的實例, 這是要列印的檔。</span><span class="sxs-lookup"><span data-stu-id="23bee-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="23bee-105">如需搭配使用「預覽列印」和<xref:System.Drawing.Printing.PrintDocument>元件的詳細[資訊, 請參閱如何:使用預覽列印](../advanced/how-to-print-in-windows-forms-using-print-preview.md)在 Windows Forms 中列印。</span><span class="sxs-lookup"><span data-stu-id="23bee-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23bee-106">若要在<xref:System.Windows.Forms.PrintPreviewDialog>執行時間使用此控制項, 使用者必須在電腦上安裝印表機 (不論是在本機或透過網路), 因為<xref:System.Windows.Forms.PrintPreviewDialog>元件會在列印時決定檔的外觀。</span><span class="sxs-lookup"><span data-stu-id="23bee-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="23bee-107"><xref:System.Windows.Forms.PrintPreviewDialog> 控制項<xref:System.Drawing.Printing.PrinterSettings>使用類別。</span><span class="sxs-lookup"><span data-stu-id="23bee-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="23bee-108">此外, <xref:System.Windows.Forms.PrintPreviewDialog>控制項也會<xref:System.Drawing.Printing.PageSettings>使用<xref:System.Windows.Forms.PrintPreviewDialog>類別, 就像元件一樣。</span><span class="sxs-lookup"><span data-stu-id="23bee-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="23bee-109">在<xref:System.Windows.Forms.PrintPreviewDialog>控制項的<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>屬性中指定的列印檔案會參考<xref:System.Drawing.Printing.PrinterSettings>和<xref:System.Drawing.Printing.PageSettings>類別的實例, 而這些是用來在預覽視窗中呈現檔。</span><span class="sxs-lookup"><span data-stu-id="23bee-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="23bee-110">若要使用 PrintPreviewDialog 控制項來查看頁面</span><span class="sxs-lookup"><span data-stu-id="23bee-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="23bee-111">使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並指定要使用的 <xref:System.Drawing.Printing.PrintDocument> 。</span><span class="sxs-lookup"><span data-stu-id="23bee-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="23bee-112">在下列程式碼範例中, <xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式<xref:System.Windows.Forms.PrintPreviewDialog>會開啟控制項的實例。</span><span class="sxs-lookup"><span data-stu-id="23bee-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="23bee-113">列印檔案是在<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性中指定的。</span><span class="sxs-lookup"><span data-stu-id="23bee-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="23bee-114">在下列範例中, 不會指定列印檔案。</span><span class="sxs-lookup"><span data-stu-id="23bee-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="23bee-115">此範例會要求您的表單<xref:System.Windows.Forms.Button>具有控制項、 <xref:System.Drawing.Printing.PrintDocument>名為`myDocument`的<xref:System.Windows.Forms.PrintPreviewDialog>元件, 以及控制項。</span><span class="sxs-lookup"><span data-stu-id="23bee-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="23bee-116">(視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="23bee-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="23bee-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23bee-117">See also</span></span>

- [<span data-ttu-id="23bee-118">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="23bee-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="23bee-119">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="23bee-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="23bee-120">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="23bee-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="23bee-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23bee-121">Windows Forms</span></span>](../index.md)
