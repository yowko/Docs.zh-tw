---
title: OpenFileDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728432"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="bb269-102">OpenFileDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="bb269-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="bb269-103">Windows Form <xref:System.Windows.Forms.OpenFileDialog> 元件是預先設定的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bb269-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="bb269-104">這是 Windows 作業系統所公開的相同 [**開啟**檔案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bb269-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="bb269-105">這個元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。</span><span class="sxs-lookup"><span data-stu-id="bb269-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="bb269-106">使用此元件</span><span class="sxs-lookup"><span data-stu-id="bb269-106">Use this component</span></span>

<span data-ttu-id="bb269-107">在以 Windows 為基礎的應用程式中使用此元件，做為檔案選取的簡單解決方案，而不是設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bb269-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="bb269-108">藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bb269-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="bb269-109">不過要注意的是，使用 <xref:System.Windows.Forms.OpenFileDialog> 元件時，您必須撰寫自己的檔案開啟邏輯。</span><span class="sxs-lookup"><span data-stu-id="bb269-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="bb269-110">使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bb269-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="bb269-111">您可以讓使用者透過 [<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>] 屬性，以多重選取要開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb269-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="bb269-112">此外，您可以使用 [<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>] 屬性來判斷對話方塊中是否出現唯讀核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bb269-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="bb269-113">[<xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>] 屬性會指出是否已選取 [唯讀] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bb269-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="bb269-114">最後，<xref:System.Windows.Forms.FileDialog.Filter%2A> 屬性會設定目前的檔案名篩選字串，以決定出現在對話方塊中 [檔案類型] 方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="bb269-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="bb269-115">當它新增至表單時，<xref:System.Windows.Forms.OpenFileDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。</span><span class="sxs-lookup"><span data-stu-id="bb269-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb269-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb269-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="bb269-117">OpenFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="bb269-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
