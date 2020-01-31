---
title: SaveFileDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743107"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="4959c-102">SaveFileDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="4959c-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="4959c-103">Windows Form <xref:System.Windows.Forms.SaveFileDialog> 元件是預先設定的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4959c-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="4959c-104">這與 Windows 所使用的標準 [**儲存**盤案] 對話方塊相同。</span><span class="sxs-lookup"><span data-stu-id="4959c-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="4959c-105">這個元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。</span><span class="sxs-lookup"><span data-stu-id="4959c-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="4959c-106">使用 SaveFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="4959c-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="4959c-107">使用它作為簡單的解決方案，讓使用者可以儲存檔案，而不是設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4959c-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="4959c-108">藉由依賴標準 Windows 對話方塊，使用者可以立即熟悉您所建立的應用程式基本功能。</span><span class="sxs-lookup"><span data-stu-id="4959c-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="4959c-109">不過要注意的是，使用 <xref:System.Windows.Forms.SaveFileDialog> 元件時，您必須撰寫自己的檔案儲存邏輯。</span><span class="sxs-lookup"><span data-stu-id="4959c-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="4959c-110">您可以使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4959c-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="4959c-111">您可以使用 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法，在讀取/寫入模式中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="4959c-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="4959c-112">當它新增至表單時，<xref:System.Windows.Forms.SaveFileDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。</span><span class="sxs-lookup"><span data-stu-id="4959c-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="4959c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="4959c-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="4959c-114">SaveFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="4959c-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
