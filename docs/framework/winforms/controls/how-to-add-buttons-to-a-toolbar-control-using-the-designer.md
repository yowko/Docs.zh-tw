---
title: "如何：使用設計工具在工具列控制項中加入按鈕 | Microsoft Docs"
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
  - "範例 [Windows Form], 工具列"
  - "ToolBar 控制項 [Windows Form], 加入按鈕"
  - "ToolBar 控制項 [Windows Form], 加入下拉式功能表"
  - "ToolBar 控制項 [Windows Form], 加入分隔符號"
  - "工具列 [Windows Form], 加入按鈕"
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用設計工具在工具列控制項中加入按鈕
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 <xref:System.Windows.Forms.ToolBar> 控制項的一個整數部分，是您加入的按鈕。  這些按鈕可用以輕鬆存取功能表命令，或是也可置於應用程式使用者介面的其他區域，將功能表結構中沒有的命令公開給您的使用者。  
  
 下列程序需要 **Windows 應用程式**專案，且專案具有包含 <xref:System.Windows.Forms.ToolBar> 控制項的表單。  如需設定這類專案的詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa) 和 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段加入按鈕  
  
1.  選取 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
2.  在 \[**屬性**\] 視窗中按一下 <xref:System.Windows.Forms.ToolBar.Buttons%2A> 屬性以選取它，然後按一下**省略符號** \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕以開啟 \[**ToolBarButton 集合編輯器**\]。  
  
3.  使用 \[**加入**\] 和 \[**移除**\] 按鈕，在 <xref:System.Windows.Forms.ToolBar> 控制項中加入和移除按鈕。  
  
4.  在編輯器右方窗格的 \[**屬性**\] 視窗中，設定個別按鈕的屬性。  下表顯示了一些要列入考量的重要屬性。  
  
    |屬性|描述|  
    |--------|--------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|設定要在下拉式工具列按鈕中顯示的功能表。  工具列按鈕的 <xref:System.Windows.Forms.ToolBarButton.Style%2A> 屬性必須設定為 <xref:System.Windows.Forms.ToolBarButtonStyle>。  本屬性將 <xref:System.Windows.Forms.ContextMenu> 類別的執行個體 \(Instance\) 當做參考。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|設定切換樣式的工具列按鈕目前是否在按下的狀態。  工具列按鈕的 <xref:System.Windows.Forms.ToolBarButton.Style%2A> 屬性必須設定為 <xref:System.Windows.Forms.ToolBarButtonStyle>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|設定切換樣式的工具列按鈕目前是否在按下的狀態。  工具列按鈕的 <xref:System.Windows.Forms.ToolBarButton.Style%2A> 屬性必須設定為 <xref:System.Windows.Forms.ToolBarButtonStyle> 或 <xref:System.Windows.Forms.ToolBarButtonStyle>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|設定工具列按鈕的樣式。  必須是 <xref:System.Windows.Forms.ToolBarButtonStyle> 列舉型別 \(Enumeration\) 當中的任一值。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|按鈕顯示的文字字串。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|以做為按鈕的工具提示出現之文字。|  
  
5.  按一下 \[**確定**\] 以關閉對話方塊並建立指定的面板。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolBar>   
 [如何：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [如何：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)   
 [ToolBar 控制項概觀](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)   
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)