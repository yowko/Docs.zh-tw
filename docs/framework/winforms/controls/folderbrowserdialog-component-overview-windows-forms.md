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
ms.openlocfilehash: a735749698266ac20e2ea9ee5569fd210ee9977b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525004"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="b9cc8-102">FolderBrowserDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b9cc8-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b9cc8-103">Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件是用來瀏覽和選取資料夾的強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="b9cc8-104">也可以從建立新的資料夾<xref:System.Windows.Forms.FolderBrowserDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9cc8-105">若要選取檔案，而不是資料夾，使用[OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)元件。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-105">To select files, instead of folders, use the [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) component.</span></span>  
  
 <span data-ttu-id="b9cc8-106"><xref:System.Windows.Forms.FolderBrowserDialog>元件會顯示在執行的階段使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="b9cc8-107">設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性來判斷最上層資料夾，然後會出現在對話方塊的 在樹狀檢視中的任何子資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="b9cc8-108">一旦已顯示對話方塊，您可以使用<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性以取得所選取之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>  
  
 <span data-ttu-id="b9cc8-109">當加入至表單，<xref:System.Windows.Forms.FolderBrowserDialog>元件會出現在 Windows Form 設計工具底部的紙匣。</span><span class="sxs-lookup"><span data-stu-id="b9cc8-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9cc8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9cc8-110">See Also</span></span>  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [<span data-ttu-id="b9cc8-111">操作說明：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾</span><span class="sxs-lookup"><span data-stu-id="b9cc8-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)  
 [<span data-ttu-id="b9cc8-112">FolderBrowserDialog 元件</span><span class="sxs-lookup"><span data-stu-id="b9cc8-112">FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
