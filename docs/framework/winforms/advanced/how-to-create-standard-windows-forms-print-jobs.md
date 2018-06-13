---
title: 如何：建立標準的 Windows Form 列印工作
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
ms.openlocfilehash: b580268a6af3f56f240a1c511c3d473a4a5ddc15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522329"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="49468-102">如何：建立標準的 Windows Form 列印工作</span><span class="sxs-lookup"><span data-stu-id="49468-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="49468-103">列印 Windows Form 中的基礎是<xref:System.Drawing.Printing.PrintDocument>元件 — 更具體來說，<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。</span><span class="sxs-lookup"><span data-stu-id="49468-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="49468-104">藉由撰寫程式碼來處理<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件，您可以指定要列印的內容，以及如何進行列印。</span><span class="sxs-lookup"><span data-stu-id="49468-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="49468-105">若要建立列印工作</span><span class="sxs-lookup"><span data-stu-id="49468-105">To create a print job</span></span>  
  
1.  <span data-ttu-id="49468-106">新增<xref:System.Drawing.Printing.PrintDocument>元件加入至表單。</span><span class="sxs-lookup"><span data-stu-id="49468-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="49468-107">撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。</span><span class="sxs-lookup"><span data-stu-id="49468-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="49468-108">您必須撰寫您自己的列印邏輯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="49468-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="49468-109">此外，您必須指定要列印的資料。</span><span class="sxs-lookup"><span data-stu-id="49468-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="49468-110">在下列程式碼範例中，建立範例圖形中以紅色矩形的圖形<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式，以做為要列印的資料。</span><span class="sxs-lookup"><span data-stu-id="49468-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="49468-111">(Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="49468-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="49468-112">您也可以撰寫程式碼<xref:System.Drawing.Printing.PrintDocument.BeginPrint>和<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件，可能包括整數，代表總頁數列印，隨著每一頁列印會遞減。</span><span class="sxs-lookup"><span data-stu-id="49468-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49468-113">您可以加入<xref:System.Windows.Forms.PrintDialog>元件加入至表單，以全新且有效的使用者介面 (UI) 提供給您的使用者。</span><span class="sxs-lookup"><span data-stu-id="49468-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="49468-114">設定<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性<xref:System.Windows.Forms.PrintDialog>元件可讓您設定與列印相關屬性的文件您正在使用您的表單上。</span><span class="sxs-lookup"><span data-stu-id="49468-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="49468-115">如需有關<xref:System.Windows.Forms.PrintDialog>元件，請參閱[PrintDialog 元件](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="49468-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="49468-116">如需特定的 Windows Form 列印工作，包括如何建立列印工作，以程式設計的方式，請參閱<xref:System.Drawing.Printing.PrintPageEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="49468-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49468-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49468-117">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="49468-118">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="49468-118">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
