---
title: SaveFileDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: be5f70e2e8b0d5143ef387819689ce95564a72d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537443"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="e4cc2-102">SaveFileDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e4cc2-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e4cc2-103">Windows Form <xref:System.Windows.Forms.SaveFileDialog> 元件是預先設定的對話方塊，</span><span class="sxs-lookup"><span data-stu-id="e4cc2-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="e4cc2-104">它等同於標準**儲存檔案**Windows 所使用的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="e4cc2-105">它繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="e4cc2-106">使用 SaveFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="e4cc2-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="e4cc2-107">使用它做為簡單的解決方案可讓使用者儲存檔案，而不是設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="e4cc2-108">藉由標準 Windows 對話方塊，您所建立的應用程式的基本功能是使用者可立即熟悉的。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="e4cc2-109">不過，要注意，當使用<xref:System.Windows.Forms.SaveFileDialog>元件，您必須撰寫您自己的檔案儲存邏輯。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="e4cc2-110">您可以使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="e4cc2-111">您可以開啟檔案讀取/寫入模式中使用<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="e4cc2-112">當加入至表單，<xref:System.Windows.Forms.SaveFileDialog>元件會出現在 Windows Form 設計工具底部的紙匣。</span><span class="sxs-lookup"><span data-stu-id="e4cc2-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cc2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4cc2-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="e4cc2-114">SaveFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="e4cc2-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
