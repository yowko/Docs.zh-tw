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
ms.openlocfilehash: aae18167b29c71ad692cc6ba447457cd079374b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074127"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog 元件概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件是用來瀏覽和選取的資料夾的強制回應對話方塊。 新的資料夾也可以建立從<xref:System.Windows.Forms.FolderBrowserDialog>元件。  
  
> [!NOTE]
>  若要選取檔案，而不是資料夾，使用[OpenFileDialog](openfiledialog-component-windows-forms.md)元件。  
  
 <xref:System.Windows.Forms.FolderBrowserDialog>元件會顯示在執行的階段使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。 設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性來判斷最上層資料夾，然後將出現在對話方塊中的樹狀檢視內的任何子資料夾。 一旦已顯示 [] 對話方塊中，您可以使用<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性來取得所選取之資料夾的路徑。  
  
 當加入至表單，<xref:System.Windows.Forms.FolderBrowserDialog>元件會出現在底部的 Windows Form 設計工具的紙匣。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [如何：選擇使用 Windows Forms FolderBrowserDialog 元件的資料夾](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog 元件](folderbrowserdialog-component-windows-forms.md)
