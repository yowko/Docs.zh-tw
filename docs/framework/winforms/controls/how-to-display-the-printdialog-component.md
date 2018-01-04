---
title: "如何：顯示 PrintDialog 元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d955febe528add4b774766a3b204f96eef5a119d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="2f3cf-102">如何：顯示 PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="2f3cf-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="2f3cf-103"><xref:System.Windows.Forms.PrintDialog>元件是標準 Windows 列印對話方塊，您的使用者都很熟悉。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="2f3cf-104">因為您的使用者會立即熟悉，很有幫助您使用<xref:System.Windows.Forms.PrintDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="2f3cf-105">顯示 PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="2f3cf-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="2f3cf-106">呼叫<xref:System.Windows.Forms.Form.ShowDialog%2A>從您的應用程式的程式碼中的方法。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="2f3cf-107">顯示此元件之後，使用者將會透過設定列印工作的屬性來與其互動。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="2f3cf-108">這些會儲存在<!--zz <xref:System.Drawing.Printing.PrinterSetting>-->`PrinterSetting`類別 (和<xref:System.Drawing.Printing.PageSettings>類別，如果使用者存取[PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)透過<xref:System.Windows.Forms.PrintDialog>元件) 與該列印工作相關聯。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="2f3cf-109">您接著可以呼叫它們所設定的屬性來決定列印工作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2f3cf-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3cf-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f3cf-110">See Also</span></span>  
 [<span data-ttu-id="2f3cf-111">操作說明：建立標準的 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="2f3cf-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="2f3cf-112">操作說明：在執行階段從 PrintDialog 擷取使用者輸入</span><span class="sxs-lookup"><span data-stu-id="2f3cf-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="2f3cf-113">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="2f3cf-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="2f3cf-114">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="2f3cf-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="2f3cf-115">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="2f3cf-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="2f3cf-116">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="2f3cf-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
