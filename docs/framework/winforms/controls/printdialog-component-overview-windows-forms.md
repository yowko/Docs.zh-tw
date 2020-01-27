---
title: PrintDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728675"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="5783c-102">PrintDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="5783c-102">PrintDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="5783c-103">Windows Forms [PrintDialog](printdialog-component-windows-forms.md)元件是預先設定的對話方塊，用來選取印表機、選擇要列印的頁面，以及判斷 Windows 應用程式中的其他列印相關設定。</span><span class="sxs-lookup"><span data-stu-id="5783c-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="5783c-104">使用它做為印表機和列印相關設定選擇的簡單解決方案，就不需設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5783c-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="5783c-105">您可以讓使用者列印檔案的許多部分： [列印全部]、[列印選取的頁面範圍] 或 [列印選取專案]。</span><span class="sxs-lookup"><span data-stu-id="5783c-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="5783c-106">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5783c-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="5783c-107"><xref:System.Windows.Forms.PrintDialog> 元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。</span><span class="sxs-lookup"><span data-stu-id="5783c-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-component"></a><span data-ttu-id="5783c-108">使用元件</span><span class="sxs-lookup"><span data-stu-id="5783c-108">Working with the Component</span></span>

<span data-ttu-id="5783c-109">使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5783c-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="5783c-110">此元件具有與單一列印工作（<xref:System.Drawing.Printing.PrintDocument> 類別）或個別印表機（<xref:System.Drawing.Printing.PrinterSettings> 類別）設定相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="5783c-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="5783c-111">其中任何一項都可以由多台印表機共用。</span><span class="sxs-lookup"><span data-stu-id="5783c-111">Either of these, in turn, may be shared by multiple printers.</span></span>

<span data-ttu-id="5783c-112">當它新增至表單時，<xref:System.Windows.Forms.PrintDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。</span><span class="sxs-lookup"><span data-stu-id="5783c-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="5783c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5783c-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="5783c-114">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="5783c-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
