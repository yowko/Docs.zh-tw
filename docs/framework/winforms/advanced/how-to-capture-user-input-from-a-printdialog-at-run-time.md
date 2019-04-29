---
title: HOW TO：在執行階段從 PrintDialog 擷取使用者輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: 2aaf988f362baf9cd80eb16e4a08f7f65a5077bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937796"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="e7342-102">HOW TO：在執行階段從 PrintDialog 擷取使用者輸入</span><span class="sxs-lookup"><span data-stu-id="e7342-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="e7342-103">雖然您可以設定在設計階段的列印相關的選項，您有時要變更這些選項在執行階段，最有可能因為使用者所做的選擇。</span><span class="sxs-lookup"><span data-stu-id="e7342-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="e7342-104">您可以擷取列印文件使用的使用者輸入<xref:System.Windows.Forms.PrintDialog>而<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="e7342-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="e7342-105">若要以程式設計方式變更列印選項</span><span class="sxs-lookup"><span data-stu-id="e7342-105">To change print options programmatically</span></span>  
  
1. <span data-ttu-id="e7342-106">新增<xref:System.Windows.Forms.PrintDialog>和<xref:System.Drawing.Printing.PrintDocument>元件至您的表單。</span><span class="sxs-lookup"><span data-stu-id="e7342-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="e7342-107">設定<xref:System.Windows.Forms.PrintDialog.Document%2A>的屬性<xref:System.Windows.Forms.PrintDialog>到<xref:System.Drawing.Printing.PrintDocument>加入至表單。</span><span class="sxs-lookup"><span data-stu-id="e7342-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3. <span data-ttu-id="e7342-108">顯示<xref:System.Windows.Forms.PrintDialog>元件使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e7342-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4. <span data-ttu-id="e7342-109">使用者的列印選項，從對話方塊將會複製到<xref:System.Drawing.Printing.PrinterSettings>屬性<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="e7342-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7342-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7342-110">See also</span></span>

- [<span data-ttu-id="e7342-111">如何：列印 Windows Form 中的多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="e7342-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="e7342-112">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="e7342-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
