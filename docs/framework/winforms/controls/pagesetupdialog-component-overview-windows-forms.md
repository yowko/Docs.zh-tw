---
title: PageSetupDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 4e7b4548f5a178ed7b819dbc2edc37bb95e3e0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534221"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="71e00-102">PageSetupDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="71e00-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="71e00-103">Windows Form<xref:System.Windows.Forms.PageSetupDialog>元件是預先設定的對話方塊，用來設定 Windows 架構應用程式中列印的頁面詳細資料。</span><span class="sxs-lookup"><span data-stu-id="71e00-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="71e00-104">它應用程式中使用 windows 做為簡單的解決方案使用者設定 頁面就不需設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="71e00-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="71e00-105">您可以讓使用者設定框線和邊界調整、 頁首和頁尾和縱向或橫向。</span><span class="sxs-lookup"><span data-stu-id="71e00-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="71e00-106">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="71e00-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="71e00-107">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="71e00-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="71e00-108">使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="71e00-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="71e00-109">這個元件有您可以設定的屬性與相關的是單一頁面 (<xref:System.Drawing.Printing.PrintDocument>類別) 或任何文件 (<xref:System.Drawing.Printing.PageSettings>類別)。</span><span class="sxs-lookup"><span data-stu-id="71e00-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="71e00-110">此外，<xref:System.Windows.Forms.PageSetupDialog>元件可以用來判斷特定的印表機設定，儲存在<xref:System.Drawing.Printing.PrinterSettings>類別。</span><span class="sxs-lookup"><span data-stu-id="71e00-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="71e00-111">當加入至表單，<xref:System.Windows.Forms.PageSetupDialog>元件會出現在 Windows Form 設計工具底部的紙匣。</span><span class="sxs-lookup"><span data-stu-id="71e00-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e00-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71e00-112">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="71e00-113">PageSetupDialog 元件</span><span class="sxs-lookup"><span data-stu-id="71e00-113">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
