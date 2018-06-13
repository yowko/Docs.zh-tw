---
title: 如何：使用 PageSetupDialog 元件決定頁面屬性
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
ms.openlocfilehash: 4b1acef216e4f8eca078d47a8cde87fb8f95ee0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532723"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="5718a-102">如何：使用 PageSetupDialog 元件決定頁面屬性</span><span class="sxs-lookup"><span data-stu-id="5718a-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="5718a-103">[PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) 元件會向文件使用者呈現配置、紙張大小和其他頁面配置選項。</span><span class="sxs-lookup"><span data-stu-id="5718a-103">The [PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="5718a-104">您需要指定 <xref:System.Drawing.Printing.PrintDocument> 類別執行個體，這是要列印文件。</span><span class="sxs-lookup"><span data-stu-id="5718a-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="5718a-105">此外，使用者必須在其電腦上安裝印表機 (本機或透過網路)，因為這有一部分是 <xref:System.Windows.Forms.PageSetupDialog> 元件如何決定呈現給使用者的頁面格式選項。</span><span class="sxs-lookup"><span data-stu-id="5718a-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="5718a-106">使用 <xref:System.Windows.Forms.PageSetupDialog> 元件的重要層面是如何與 <xref:System.Drawing.Printing.PageSettings> 類別互動。</span><span class="sxs-lookup"><span data-stu-id="5718a-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="5718a-107"><xref:System.Drawing.Printing.PageSettings> 類別是用來指定可修改頁面列印方式的設定，例如紙張列印方向，頁面大小和邊界。</span><span class="sxs-lookup"><span data-stu-id="5718a-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="5718a-108">所有這些設定都是呈現為 <xref:System.Drawing.Printing.PageSettings> 類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="5718a-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="5718a-109"><xref:System.Windows.Forms.PageSetupDialog> 類別會針對與文件相關聯 (並呈現為 <xref:System.Drawing.Printing.PageSettings> 屬性) 的指定 <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> 類別執行個體來修改這些屬性值。</span><span class="sxs-lookup"><span data-stu-id="5718a-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="5718a-110">使用 PageSetupDialog 元件決定頁面屬性</span><span class="sxs-lookup"><span data-stu-id="5718a-110">To set page properties using the PageSetupDialog component</span></span>  
  
1.  <span data-ttu-id="5718a-111">使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示對話方塊，並指定要使用的 <xref:System.Drawing.Printing.PrintDocument> 。</span><span class="sxs-lookup"><span data-stu-id="5718a-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="5718a-112">在下列範例中， <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式會開啟 <xref:System.Windows.Forms.PageSetupDialog> 元件執行個體。</span><span class="sxs-lookup"><span data-stu-id="5718a-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="5718a-113">現有的文件指定於 <xref:System.Windows.Forms.PageSetupDialog.Document%2A> 屬性中，而且其 <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5718a-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="5718a-114">這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項，<xref:System.Drawing.Printing.PrintDocument>名元件`myDocument`，和<xref:System.Windows.Forms.PageSetupDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="5718a-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="5718a-115">(Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5718a-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5718a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5718a-116">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="5718a-117">操作說明：建立標準的 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="5718a-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="5718a-118">PageSetupDialog 元件</span><span class="sxs-lookup"><span data-stu-id="5718a-118">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
