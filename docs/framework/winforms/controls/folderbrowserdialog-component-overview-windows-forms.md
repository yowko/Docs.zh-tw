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
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog 元件概觀 (Windows Form)

Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> 元件是用來流覽和選取資料夾的強制回應對話方塊。 您也可以從 <xref:System.Windows.Forms.FolderBrowserDialog> 元件中建立新的資料夾。

> [!NOTE]
> 若要選取檔案，而不是資料夾，請使用[OpenFileDialog](openfiledialog-component-windows-forms.md)元件。

<xref:System.Windows.Forms.FolderBrowserDialog> 元件會在執行時間使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法來顯示。 設定 [<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>] 屬性，以決定將出現在對話方塊樹狀檢視中的最上層資料夾和任何子資料夾。 顯示對話方塊之後，您就可以使用 [<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>] 屬性來取得已選取之資料夾的路徑。

當它新增至表單時，<xref:System.Windows.Forms.FolderBrowserDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [操作說明：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog 元件](folderbrowserdialog-component-windows-forms.md)
