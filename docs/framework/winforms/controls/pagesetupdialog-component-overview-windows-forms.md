---
title: PageSetupDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 30ac782cae830ac996132046cbbc57392067c0ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932531"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="4dfb3-102">PageSetupDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="4dfb3-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="4dfb3-103">Windows Form<xref:System.Windows.Forms.PageSetupDialog>元件是預先設定的對話方塊，用於以 Windows 為基礎的應用程式中設定列印的頁面詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="4dfb3-104">它用於應用程式內以 Windows 為基礎的簡單解決方案，為使用者設定頁面的喜好設定，不需設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="4dfb3-105">您可以讓使用者設定框線和邊界調整、 頁首和頁尾和直向或橫向方向。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="4dfb3-106">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="4dfb3-107">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="4dfb3-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="4dfb3-108">使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="4dfb3-109">這個元件有您可以設定為單一頁面的相關屬性 (<xref:System.Drawing.Printing.PrintDocument>類別) 或任何文件 (<xref:System.Drawing.Printing.PageSettings>類別)。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="4dfb3-110">此外，<xref:System.Windows.Forms.PageSetupDialog>元件可以用來判斷特定的印表機設定，會儲存在<xref:System.Drawing.Printing.PrinterSettings>類別。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="4dfb3-111">當加入至表單，<xref:System.Windows.Forms.PageSetupDialog>元件會出現在底部的 Windows Form 設計工具的紙匣。</span><span class="sxs-lookup"><span data-stu-id="4dfb3-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfb3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dfb3-112">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="4dfb3-113">PageSetupDialog 元件</span><span class="sxs-lookup"><span data-stu-id="4dfb3-113">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
