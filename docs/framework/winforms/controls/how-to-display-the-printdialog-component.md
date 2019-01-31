---
title: 如何顯示 PrintDialog 元件
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285151"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="f6aae-102">如何顯示 PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="f6aae-102">How to display the PrintDialog component</span></span>

<span data-ttu-id="f6aae-103"><xref:System.Windows.Forms.PrintDialog>元件是標準 Windows 列印對話方塊，您的許多使用者不會感到陌生。</span><span class="sxs-lookup"><span data-stu-id="f6aae-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="f6aae-104">因為您的使用者可以立即熟悉它，它會有幫助您使用<xref:System.Windows.Forms.PrintDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="f6aae-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>

## <a name="to-display-the-printdialog-component"></a><span data-ttu-id="f6aae-105">顯示 PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="f6aae-105">To display the PrintDialog component</span></span>

- <span data-ttu-id="f6aae-106">呼叫<xref:System.Windows.Forms.Form.ShowDialog%2A>從您的應用程式的程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="f6aae-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>

     <span data-ttu-id="f6aae-107">顯示此元件之後，使用者將會透過設定列印工作的屬性來與其互動。</span><span class="sxs-lookup"><span data-stu-id="f6aae-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="f6aae-108">這些會儲存在<xref:System.Drawing.Printing.PrinterSettings>類別 (和<xref:System.Drawing.Printing.PageSettings>類別，如果使用者存取[PageSetupDialog 元件](pagesetupdialog-component-windows-forms.md)透過<xref:System.Windows.Forms.PrintDialog>元件) 與該列印工作相關聯。</span><span class="sxs-lookup"><span data-stu-id="f6aae-108">These are saved in the  <xref:System.Drawing.Printing.PrinterSettings> class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="f6aae-109">您接著可以呼叫它們所設定的屬性來決定列印工作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f6aae-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6aae-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6aae-110">See also</span></span>

- [<span data-ttu-id="f6aae-111">如何：建立標準的 Windows Forms 列印工作</span><span class="sxs-lookup"><span data-stu-id="f6aae-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="f6aae-112">如何：在執行階段擷取使用者輸入從 PrintDialog</span><span class="sxs-lookup"><span data-stu-id="f6aae-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [<span data-ttu-id="f6aae-113">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="f6aae-113">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="f6aae-114">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="f6aae-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
- [<span data-ttu-id="f6aae-115">Windows Forms 列印支援</span><span class="sxs-lookup"><span data-stu-id="f6aae-115">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="f6aae-116">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="f6aae-116">Windows Forms Controls</span></span>](index.md)