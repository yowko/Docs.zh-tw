---
title: "PrintDialog 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20bbfd02c7fe8f5ca89d67e045b0edd4f2db996c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="895a6-102">PrintDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="895a6-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="895a6-103">Windows Form [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)元件是預先設定的對話方塊，用來選取印表機、 選擇要列印的頁面以及決定 Windows 架構應用程式中的其他列印相關設定。</span><span class="sxs-lookup"><span data-stu-id="895a6-103">The Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="895a6-104">使用它做為印表機和列印相關設定選擇的簡單解決方案，就不需設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="895a6-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="895a6-105">您可以讓使用者列印文件中的許多部分： 列印全部、 列印選取的頁面範圍或列印選取的範圍。</span><span class="sxs-lookup"><span data-stu-id="895a6-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="895a6-106">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="895a6-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="895a6-107"><xref:System.Windows.Forms.PrintDialog>元件繼承自<xref:System.Windows.Forms.CommonDialog>類別。</span><span class="sxs-lookup"><span data-stu-id="895a6-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="895a6-108">使用元件</span><span class="sxs-lookup"><span data-stu-id="895a6-108">Working with the Component</span></span>  
 <span data-ttu-id="895a6-109">使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="895a6-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="895a6-110">這個元件有與其中一個列印工作的屬性 (<xref:System.Drawing.Printing.PrintDocument>類別) 或個別的印表機設定 (<xref:System.Drawing.Printing.PrinterSettings>類別)。</span><span class="sxs-lookup"><span data-stu-id="895a6-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="895a6-111">任一種，接著，會共用由多部印表機。</span><span class="sxs-lookup"><span data-stu-id="895a6-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="895a6-112">當加入至表單，<xref:System.Windows.Forms.PrintDialog>元件會出現在 Windows Form 設計工具底部的紙匣。</span><span class="sxs-lookup"><span data-stu-id="895a6-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895a6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="895a6-113">See Also</span></span>  
 <xref:System.Windows.Forms.PrintDialog>  
 [<span data-ttu-id="895a6-114">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="895a6-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
