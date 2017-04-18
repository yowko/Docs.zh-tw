---
title: "FolderBrowserDialog 元件概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FolderBrowserDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "目錄 [Windows Form], 在應用程式中啟用瀏覽"
  - "FolderBrowserDialog 元件 [Windows Form], 關於 FolderBrowserDialog"
  - "資料夾 [Windows Form], 在應用程式中啟用瀏覽"
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# FolderBrowserDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.FolderBrowserDialog> 元件為強制回應對話方塊，供瀏覽和選取資料夾之用。  新資料夾也可以從 <xref:System.Windows.Forms.FolderBrowserDialog> 元件中建立。  
  
> [!NOTE]
>  若要選取檔案，而不是資料夾，請使用 [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) 元件。  
  
 <xref:System.Windows.Forms.FolderBrowserDialog> 元件是在執行階段使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法顯示的。  設定 <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> 屬性，以決定在對話方塊樹狀檢視內出現的最上層資料夾及任何子資料夾。  一旦對話方塊出現，即可使用 <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 屬性來取得所選取的資料夾路徑。  
  
 當 <xref:System.Windows.Forms.FolderBrowserDialog> 元件加入表單時，它會出現在 \[Windows Form 設計工具\] 下方的匣中。  
  
## 請參閱  
 <xref:System.Windows.Forms.FolderBrowserDialog>   
 [如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)   
 [FolderBrowserDialog 元件](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)