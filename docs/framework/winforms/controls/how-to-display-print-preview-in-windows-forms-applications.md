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
ms.workload: dotnet
ms.openlocfilehash: 2567a564b5769abd91d34696c1a94c21ad2913ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="a567f-102">如何：在 Windows Forms 應用程式中顯示預覽列印</span><span class="sxs-lookup"><span data-stu-id="a567f-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="a567f-103">您可以使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項，讓使用者顯示文件，通常在列印之前。</span><span class="sxs-lookup"><span data-stu-id="a567f-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="a567f-104">若要這樣做，您需要指定的執行個體<xref:System.Drawing.Printing.PrintDocument>類別; 這是要列印文件。</span><span class="sxs-lookup"><span data-stu-id="a567f-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="a567f-105">如需有關使用預覽列印與<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[如何： 列印 Windows Form 使用預覽列印](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)。</span><span class="sxs-lookup"><span data-stu-id="a567f-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a567f-106">若要使用<xref:System.Windows.Forms.PrintPreviewDialog>控制項在執行階段，使用者必須已安裝印表機他們在電腦上，在本機或透過網路，因為這是部分如何<xref:System.Windows.Forms.PrintPreviewDialog>元件決定文件列印的樣子。</span><span class="sxs-lookup"><span data-stu-id="a567f-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="a567f-107"><xref:System.Windows.Forms.PrintPreviewDialog>控制使用<xref:System.Drawing.Printing.PrinterSettings>類別。</span><span class="sxs-lookup"><span data-stu-id="a567f-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="a567f-108">此外，<xref:System.Windows.Forms.PrintPreviewDialog>控制使用<xref:System.Drawing.Printing.PageSettings>類別，就如同<xref:System.Windows.Forms.PrintPreviewDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="a567f-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="a567f-109">列印文件中指定<xref:System.Windows.Forms.PrintPreviewDialog>控制項的<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>屬性是指兩個執行個體<xref:System.Drawing.Printing.PrinterSettings>和<xref:System.Drawing.Printing.PageSettings>類別，以及這些用來呈現預覽視窗中的文件。</span><span class="sxs-lookup"><span data-stu-id="a567f-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="a567f-110">若要檢視使用 PrintPreviewDialog 控制項的頁面</span><span class="sxs-lookup"><span data-stu-id="a567f-110">To view pages using the PrintPreviewDialog control</span></span>  
  
-   <span data-ttu-id="a567f-111">使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並指定要使用的 <xref:System.Drawing.Printing.PrintDocument> 。</span><span class="sxs-lookup"><span data-stu-id="a567f-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="a567f-112">在下列程式碼範例中，<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式會開啟執行個體<xref:System.Windows.Forms.PrintPreviewDialog>控制項。</span><span class="sxs-lookup"><span data-stu-id="a567f-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="a567f-113">列印文件中指定<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a567f-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="a567f-114">在下列範例中，指定不列印的文件。</span><span class="sxs-lookup"><span data-stu-id="a567f-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="a567f-115">這個範例需要您的表單具有<xref:System.Windows.Forms.Button>控制項，<xref:System.Drawing.Printing.PrintDocument>名元件`myDocument`，和<xref:System.Windows.Forms.PrintPreviewDialog>控制項。</span><span class="sxs-lookup"><span data-stu-id="a567f-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="a567f-116">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a567f-116">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a567f-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a567f-117">See Also</span></span>  
 [<span data-ttu-id="a567f-118">PrintDocument 元件</span><span class="sxs-lookup"><span data-stu-id="a567f-118">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [<span data-ttu-id="a567f-119">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="a567f-119">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="a567f-120">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="a567f-120">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="a567f-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a567f-121">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
