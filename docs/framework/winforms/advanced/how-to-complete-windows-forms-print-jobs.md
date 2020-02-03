---
title: 完成列印工作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746499"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a><span data-ttu-id="74edc-102">如何：完成 Windows Form 列印工作</span><span class="sxs-lookup"><span data-stu-id="74edc-102">How to: Complete Windows Forms Print Jobs</span></span>
<span data-ttu-id="74edc-103">經常，包含列印的文字處理器和其他應用程式將會提供選項，讓使用者顯示列印工作已完成的訊息。</span><span class="sxs-lookup"><span data-stu-id="74edc-103">Frequently, word processors and other applications that involve printing will provide the option to display a message to users that a print job is complete.</span></span> <span data-ttu-id="74edc-104">您可以藉由處理 <xref:System.Drawing.Printing.PrintDocument> 元件的 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件，在您的 Windows Forms 中提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="74edc-104">You can provide this functionality in your Windows Forms by handling the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="74edc-105">下列程式需要您建立一個具有 <xref:System.Drawing.Printing.PrintDocument> 元件的 Windows 應用程式，這是從 Windows 應用程式啟用列印的標準方式。</span><span class="sxs-lookup"><span data-stu-id="74edc-105">The following procedure requires that you have created a Windows-based application with a <xref:System.Drawing.Printing.PrintDocument> component on it, which is the standard way of enabling printing from a Windows-based application.</span></span> <span data-ttu-id="74edc-106">如需使用 <xref:System.Drawing.Printing.PrintDocument> 元件從 Windows Forms 列印的詳細資訊，請參閱[如何：建立標準 Windows Forms 列印工作](how-to-create-standard-windows-forms-print-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="74edc-106">For more information about printing from Windows Forms using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Create Standard Windows Forms Print Jobs](how-to-create-standard-windows-forms-print-jobs.md).</span></span>  
  
### <a name="to-complete-a-print-job"></a><span data-ttu-id="74edc-107">完成列印工作</span><span class="sxs-lookup"><span data-stu-id="74edc-107">To complete a print job</span></span>  
  
1. <span data-ttu-id="74edc-108">設定 <xref:System.Drawing.Printing.PrintDocument> 元件的 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="74edc-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <span data-ttu-id="74edc-109">撰寫程式碼來處理 <xref:System.Drawing.Printing.PrintDocument.EndPrint> 事件。</span><span class="sxs-lookup"><span data-stu-id="74edc-109">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.EndPrint> event.</span></span>  
  
     <span data-ttu-id="74edc-110">在下列程式碼範例中，會顯示訊息方塊，指出檔已完成列印。</span><span class="sxs-lookup"><span data-stu-id="74edc-110">In the following code example, a message box is displayed, indicating that the document has finished printing.</span></span>  
  
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
  
     <span data-ttu-id="74edc-111">（視覺C#效果和C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="74edc-111">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74edc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74edc-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="74edc-113">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="74edc-113">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
