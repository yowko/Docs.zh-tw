---
title: HOW TO：建立標準的 Windows Forms 列印工作
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
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938235"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="6ed2b-102">作法：建立標準的 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="6ed2b-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="6ed2b-103">Windows Forms 中列印的基礎是<xref:System.Drawing.Printing.PrintDocument>元件, 更具體來說<xref:System.Drawing.Printing.PrintDocument.PrintPage>就是事件。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="6ed2b-104">藉由撰寫程式碼來<xref:System.Drawing.Printing.PrintDocument.PrintPage>處理事件, 您可以指定要列印的內容以及列印方式。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="6ed2b-105">建立列印工作</span><span class="sxs-lookup"><span data-stu-id="6ed2b-105">To create a print job</span></span>  
  
1. <span data-ttu-id="6ed2b-106"><xref:System.Drawing.Printing.PrintDocument>將元件新增至您的表單。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="6ed2b-107">撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="6ed2b-108">您將必須撰寫自己的列印邏輯程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="6ed2b-109">此外, 您也必須指定要列印的材質。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="6ed2b-110">在下列程式碼範例中, 會在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中建立紅色矩形圖形的範例圖形, 以作為要列印的材質。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="6ed2b-111">(視覺C#效果和C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="6ed2b-112">您可能也會想要撰寫<xref:System.Drawing.Printing.PrintDocument.BeginPrint>和<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件的程式碼, 其中可能包含一個整數, 代表要列印的總頁數, 會隨著每頁列印而遞減。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6ed2b-113">您可以將<xref:System.Windows.Forms.PrintDialog>元件新增至表單, 為您的使用者提供乾淨且有效率的使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="6ed2b-114">設定<xref:System.Windows.Forms.PrintDialog>元件<xref:System.Windows.Forms.PrintDialog.Document%2A>的屬性, 可讓您設定與您在表單上使用之列印檔案相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="6ed2b-115">如需<xref:System.Windows.Forms.PrintDialog>元件的詳細資訊, 請參閱[PrintDialog 元件](../controls/printdialog-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="6ed2b-116">如需 Windows Forms 列印工作細節的詳細資訊, 包括如何以程式設計方式建立列印工作, 請<xref:System.Drawing.Printing.PrintPageEventArgs>參閱。</span><span class="sxs-lookup"><span data-stu-id="6ed2b-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed2b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ed2b-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="6ed2b-118">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="6ed2b-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
