---
title: "如何：在 Windows Form 建立 Windows 檔案總管樣式的介面 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "表單, Windows 檔案總管類型"
  - "SplitContainer 控制項 [Windows Form], 檔案總管樣式介面"
  - "Windows 檔案總管, 使用 Windows Form 建立"
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：在 Windows Form 建立 Windows 檔案總管樣式的介面
因為使用者對 Windows 檔案總管已有相當程度的了解，因此使用者常以其為應用程式的使用者介面。  
  
 本質上，Windows 檔案總管在個別的面板是 <xref:System.Windows.Forms.TreeView> 控制項 <xref:System.Windows.Forms.ListView> 控制項。  面板是以可調整的分隔器 \(Splitter\) 所組成。  對於顯示和瀏覽資訊而言，這個控制項的安排非常的有效率。  
  
 下列步驟顯示如何以類似 Windows 檔案總管的形式來排列控制項。  但是並未顯示如何在 Windows 檔案總管應用程式的檔案瀏覽功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立 Windows 檔案總管樣式的 Windows Form  
  
1.  建立新的 \[Windows 應用程式\] 專案。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  從 \[**工具箱**\]：  
  
    1.  將 <xref:System.Windows.Forms.SplitContainer> 控制項拖曳到您的表單上。  
  
    2.  將 <xref:System.Windows.Forms.TreeView> 控制項拖曳到 **SplitterPanel1** \(<xref:System.Windows.Forms.SplitContainer> 控制項的面板標記為 \[**Panel1**\]\)。  
  
    3.  將 <xref:System.Windows.Forms.ListView> 控制項拖曳到 **SplitterPanel2** \(<xref:System.Windows.Forms.SplitContainer> 控制項的面板標記為 \[**Panel2**\]\)。  
  
3.  按下 CTRL 鍵不放並依序按一下這三個控制項。  當您選取 <xref:System.Windows.Forms.SplitContainer> 控制項時，請按分隔列，不要按面板。  
  
    > [!NOTE]
    >  請不要在 \[**編輯**\] 功能表上使用 \[**全選**\] 命令。  如果這麼做，在下個步驟所需的屬性就不會出現在 \[**屬性**\] 視窗。  
  
4.  在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>。  
  
5.  按下 F5 執行應用程式。  
  
     表單會顯示由兩個部分所組成的使用者介面，與 Windows 檔案總管的使用者介面類似。  
  
    > [!NOTE]
    >  當您拖曳分隔器時，面板會自動調整。  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 [逐步解說：利用 Windows Form 建立多窗格使用者介面](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)   
 [如何：定義分隔視窗的調整大小和位置行為](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)   
 [如何：水平分隔視窗](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)   
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)