---
title: "FolderBrowserDialog 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7fab1dbe01c5b21e510841b1541150f6152ab0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog 元件概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件是用來瀏覽和選取資料夾的強制回應對話方塊。 也可以從建立新的資料夾<xref:System.Windows.Forms.FolderBrowserDialog>元件。  
  
> [!NOTE]
>  若要選取檔案，而不是資料夾，使用[OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)元件。  
  
 <xref:System.Windows.Forms.FolderBrowserDialog>元件會顯示在執行的階段使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。 設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性來判斷最上層資料夾，然後會出現在對話方塊的 在樹狀檢視中的任何子資料夾。 一旦已顯示對話方塊，您可以使用<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性以取得所選取之資料夾的路徑。  
  
 當加入至表單，<xref:System.Windows.Forms.FolderBrowserDialog>元件會出現在 Windows Form 設計工具底部的紙匣。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [操作說明：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)  
 [FolderBrowserDialog 元件](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
