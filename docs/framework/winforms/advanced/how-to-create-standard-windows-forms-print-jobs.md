---
title: 創建標準列印工作
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182574"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="b24e1-102">如何：建立標準的 Windows Form 列印工作</span><span class="sxs-lookup"><span data-stu-id="b24e1-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="b24e1-103">在 Windows 表單中列印的基礎是<xref:System.Drawing.Printing.PrintDocument>元件，更具體地說，是<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。</span><span class="sxs-lookup"><span data-stu-id="b24e1-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="b24e1-104">通過編寫代碼來處理事件，<xref:System.Drawing.Printing.PrintDocument.PrintPage>您可以指定要列印的內容以及如何列印它。</span><span class="sxs-lookup"><span data-stu-id="b24e1-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="b24e1-105">創建列印工作</span><span class="sxs-lookup"><span data-stu-id="b24e1-105">To create a print job</span></span>  
  
1. <span data-ttu-id="b24e1-106">向表單<xref:System.Drawing.Printing.PrintDocument>添加元件。</span><span class="sxs-lookup"><span data-stu-id="b24e1-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="b24e1-107">撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件。</span><span class="sxs-lookup"><span data-stu-id="b24e1-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="b24e1-108">您必須編寫自己的列印邏輯代碼。</span><span class="sxs-lookup"><span data-stu-id="b24e1-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="b24e1-109">此外，您必須指定要列印的材料。</span><span class="sxs-lookup"><span data-stu-id="b24e1-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="b24e1-110">在下面的代碼示例中，將在<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件處理常式中創建紅色矩形形狀的示例圖形，以用作要列印的材料。</span><span class="sxs-lookup"><span data-stu-id="b24e1-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
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
  
     <span data-ttu-id="b24e1-111">（視覺 C# 和視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b24e1-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
     <span data-ttu-id="b24e1-112">您可能還希望為<xref:System.Drawing.Printing.PrintDocument.BeginPrint>和<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件編寫代碼，可能包括一個整數，表示每個頁面列印時要列印的頁總數。</span><span class="sxs-lookup"><span data-stu-id="b24e1-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b24e1-113">您可以將元件添加到表單<xref:System.Windows.Forms.PrintDialog>中，以便為使用者提供乾淨高效的使用者介面 （UI）。</span><span class="sxs-lookup"><span data-stu-id="b24e1-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="b24e1-114">通過設置<xref:System.Windows.Forms.PrintDialog.Document%2A>元件的屬性，<xref:System.Windows.Forms.PrintDialog>可以設置與在表單上處理的列印文檔相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="b24e1-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="b24e1-115">有關元件的詳細資訊，<xref:System.Windows.Forms.PrintDialog>請參閱[PrintDialog 元件](../controls/printdialog-component-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b24e1-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="b24e1-116">有關 Windows 表單列印工作的詳細資訊，包括如何以程式設計方式創建列印工作，請參閱<xref:System.Drawing.Printing.PrintPageEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="b24e1-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b24e1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b24e1-117">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="b24e1-118">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="b24e1-118">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
