---
title: "如何：使用設計工具定義工具列按鈕的圖示 | Microsoft Docs"
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
  - "按鈕 [Windows Form], 影像"
  - "範例 [Windows Form], 工具列"
  - "圖示 [Windows Form], 工具列按鈕"
  - "影像 [Windows Form], 工具列按鈕"
  - "ToolBar 控制項 [Windows Form], 將圖示加入至按鈕"
  - "工具列 [Windows Form], 將圖示加入至按鈕"
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用設計工具定義工具列按鈕的圖示
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 <xref:System.Windows.Forms.ToolBar> 按鈕可以在按鈕中顯示圖示，方便使用者識別。  這項功能是經由將影像加入至 <xref:System.Windows.Forms.ImageList> 元件，並將元件關聯至 <xref:System.Windows.Forms.ToolBar> 控制項來達成。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.ToolBar> 控制項和 <xref:System.Windows.Forms.ImageList> 元件的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段設定工具列按鈕的圖示  
  
1.  將影像加入至 <xref:System.Windows.Forms.ImageList> 元件。  如需詳細資訊，請參閱 [如何：使用設計工具加入或移除 ImageList 影像](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md)。  
  
2.  選取表單上的 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.ToolBar> 控制項的 <xref:System.Windows.Forms.ToolBar.ImageList%2A> 屬性值設為 <xref:System.Windows.Forms.ImageList> 元件。  
  
4.  按一下 <xref:System.Windows.Forms.ToolBar> 控制項的 <xref:System.Windows.Forms.ToolBar.Buttons%2A> 屬性來選取它，並按一下省略 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕開啟 \[**ToolBarButton 集合編輯器**\]。  
  
5.  使用 \[**加入**\] 按鈕，將按鈕加入至 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
6.  在 \[**ToolBarButton 集合編輯器**\] 右邊窗格出現的 \[**屬性**\] 視窗中，將每個工具列按鈕的 <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> 屬性設定為清單中的一個值，此清單是由您加入至 <xref:System.Windows.Forms.ImageList> 元件的影像所繪製而成。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolBar>   
 [如何：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)