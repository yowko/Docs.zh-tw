---
title: FolderBrowserDialog 元件總覽
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745734"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="9b029-102">FolderBrowserDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9b029-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="9b029-103">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> 元件是用來流覽和選取資料夾的強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b029-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="9b029-104">您也可以從 <xref:System.Windows.Forms.FolderBrowserDialog> 元件中建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9b029-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="9b029-105">若要選取檔案，而不是資料夾，請使用[OpenFileDialog](openfiledialog-component-windows-forms.md)元件。</span><span class="sxs-lookup"><span data-stu-id="9b029-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="9b029-106"><xref:System.Windows.Forms.FolderBrowserDialog> 元件會在執行時間使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法來顯示。</span><span class="sxs-lookup"><span data-stu-id="9b029-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="9b029-107">設定 [<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>] 屬性，以決定將出現在對話方塊樹狀檢視中的最上層資料夾和任何子資料夾。</span><span class="sxs-lookup"><span data-stu-id="9b029-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="9b029-108">顯示對話方塊之後，您就可以使用 [<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>] 屬性來取得已選取之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="9b029-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="9b029-109">當它新增至表單時，<xref:System.Windows.Forms.FolderBrowserDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。</span><span class="sxs-lookup"><span data-stu-id="9b029-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b029-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b029-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="9b029-111">操作說明：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾</span><span class="sxs-lookup"><span data-stu-id="9b029-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="9b029-112">FolderBrowserDialog 元件</span><span class="sxs-lookup"><span data-stu-id="9b029-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
