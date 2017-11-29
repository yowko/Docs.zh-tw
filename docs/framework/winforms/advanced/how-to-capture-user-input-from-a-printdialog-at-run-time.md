---
title: "如何：在執行階段從 PrintDialog 擷取使用者輸入"
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
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c942cb5f005177b74dd25a9725b4990553adbb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="f09fc-102">如何：在執行階段從 PrintDialog 擷取使用者輸入</span><span class="sxs-lookup"><span data-stu-id="f09fc-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="f09fc-103">雖然您可以設定與設計階段的列印相關的選項，您有時要在執行階段，因為使用者所做的選擇最有可能變更這些選項。</span><span class="sxs-lookup"><span data-stu-id="f09fc-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="f09fc-104">您可以擷取使用者輸入來列印文件使用<xref:System.Windows.Forms.PrintDialog>和<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="f09fc-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="f09fc-105">若要以程式設計方式變更列印選項</span><span class="sxs-lookup"><span data-stu-id="f09fc-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="f09fc-106">新增<xref:System.Windows.Forms.PrintDialog>和<xref:System.Drawing.Printing.PrintDocument>元件加入至表單。</span><span class="sxs-lookup"><span data-stu-id="f09fc-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="f09fc-107">設定<xref:System.Windows.Forms.PrintDialog.Document%2A>屬性<xref:System.Windows.Forms.PrintDialog>至<xref:System.Drawing.Printing.PrintDocument>加入至表單。</span><span class="sxs-lookup"><span data-stu-id="f09fc-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="f09fc-108">顯示<xref:System.Windows.Forms.PrintDialog>元件使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="f09fc-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="f09fc-109">使用者的列印選項，從對話方塊將會複製到<xref:System.Drawing.Printing.PrinterSettings>屬性<xref:System.Drawing.Printing.PrintDocument>元件。</span><span class="sxs-lookup"><span data-stu-id="f09fc-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f09fc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f09fc-110">See Also</span></span>  
 [<span data-ttu-id="f09fc-111">如何：在 Windows Forms 中列印多頁文字檔</span><span class="sxs-lookup"><span data-stu-id="f09fc-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="f09fc-112">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="f09fc-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
