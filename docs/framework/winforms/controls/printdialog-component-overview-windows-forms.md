---
title: PrintDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 982c52dbe9243e69bbb0452513e78798f4d1fd0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903405"
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="7db13-102">PrintDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7db13-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="7db13-103">Windows Forms [PrintDialog](printdialog-component-windows-forms.md)元件是預先設定的對話方塊，用來選取印表機、 選擇要列印的頁面以及決定其他列印相關設定以 Windows 為基礎的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7db13-103">The Windows Forms [PrintDialog](printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="7db13-104">使用它做為印表機和列印相關設定選擇的簡單解決方案，就不需設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7db13-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="7db13-105">您可以讓使用者列印文件中的許多部分： 列印全部、 列印選取的頁面範圍或列印選取的範圍。</span><span class="sxs-lookup"><span data-stu-id="7db13-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="7db13-106">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7db13-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="7db13-107"><xref:System.Windows.Forms.PrintDialog>元件繼承自<xref:System.Windows.Forms.CommonDialog>類別。</span><span class="sxs-lookup"><span data-stu-id="7db13-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="7db13-108">使用元件</span><span class="sxs-lookup"><span data-stu-id="7db13-108">Working with the Component</span></span>  
 <span data-ttu-id="7db13-109">使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7db13-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="7db13-110">這個元件有指單一列印工作的屬性 (<xref:System.Drawing.Printing.PrintDocument>類別) 或個別的印表機設定 (<xref:System.Drawing.Printing.PrinterSettings>類別)。</span><span class="sxs-lookup"><span data-stu-id="7db13-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="7db13-111">任一種，反而會共用由多部印表機。</span><span class="sxs-lookup"><span data-stu-id="7db13-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="7db13-112">當加入至表單，<xref:System.Windows.Forms.PrintDialog>元件會出現在底部的 Windows Form 設計工具的紙匣。</span><span class="sxs-lookup"><span data-stu-id="7db13-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db13-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7db13-113">See also</span></span>

- <xref:System.Windows.Forms.PrintDialog>
- [<span data-ttu-id="7db13-114">PrintDialog 元件</span><span class="sxs-lookup"><span data-stu-id="7db13-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
