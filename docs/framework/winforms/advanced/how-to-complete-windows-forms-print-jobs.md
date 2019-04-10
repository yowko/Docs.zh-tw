---
title: HOW TO：完成 Windows Forms 列印工作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 256b9a3d8842aaa4b032e67ebac9ca6a9e1ef34a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293751"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="cc8f9-102">HOW TO：完成 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="cc8f9-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="cc8f9-103">通常，文書處理器和其他應用程式牽涉到列印會提供對列印工作已完成的使用者顯示一則訊息的選項。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="cc8f9-104">您可以在 Windows Forms 中提供這項功能，藉由處理<xref:System.Drawing.Printing.PrintDocument.EndPrint>事件的<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="cc8f9-105">下列程序需要您已建立的 Windows 應用程式與<xref:System.Drawing.Printing.PrintDocument>它，也就是標準的方式，啟用從以 Windows 為基礎的應用程式列印的元件。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="cc8f9-106">如需有關從使用 Windows Form 列印<xref:System.Drawing.Printing.PrintDocument>元件，請參閱[How to:建立標準的 Windows Forms 列印工作](how-to-create-standard-windows-forms-print-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="cc8f9-107">若要完成列印工作</span><span class="sxs-lookup"><span data-stu-id="cc8f9-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="cc8f9-108">設定<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>屬性<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="cc8f9-109">撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="cc8f9-110">在下列程式碼範例中，會顯示訊息方塊，表示文件已完成列印。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     <span data-ttu-id="cc8f9-111">(Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="cc8f9-111">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cc8f9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc8f9-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="cc8f9-113">Windows Form 列印支援</span><span class="sxs-lookup"><span data-stu-id="cc8f9-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
