---
title: FolderBrowserDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: cd89980ccad7e6c73094c1fb462d93cee8094959
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210403"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="e55e9-102">FolderBrowserDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e55e9-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e55e9-103">Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件是用來瀏覽和選取的資料夾的強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e55e9-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="e55e9-104">新的資料夾也可以建立從<xref:System.Windows.Forms.FolderBrowserDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="e55e9-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="e55e9-105">若要選取檔案，而不是資料夾，使用[OpenFileDialog](openfiledialog-component-windows-forms.md)元件。</span><span class="sxs-lookup"><span data-stu-id="e55e9-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="e55e9-106"><xref:System.Windows.Forms.FolderBrowserDialog>元件會顯示在執行的階段使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e55e9-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="e55e9-107">設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性來判斷最上層資料夾，然後將出現在對話方塊中的樹狀檢視內的任何子資料夾。</span><span class="sxs-lookup"><span data-stu-id="e55e9-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="e55e9-108">一旦已顯示 [] 對話方塊中，您可以使用<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性來取得所選取之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="e55e9-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="e55e9-109">當加入至表單，<xref:System.Windows.Forms.FolderBrowserDialog>元件會出現在底部的 Windows Form 設計工具，在 Visual Studio 中的紙匣。</span><span class="sxs-lookup"><span data-stu-id="e55e9-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="e55e9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e55e9-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="e55e9-111">如何：選擇使用 Windows Forms FolderBrowserDialog 元件的資料夾</span><span class="sxs-lookup"><span data-stu-id="e55e9-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="e55e9-112">FolderBrowserDialog 元件</span><span class="sxs-lookup"><span data-stu-id="e55e9-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
