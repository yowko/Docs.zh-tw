---
title: "ToolBar 控制項 (Windows Form) | Microsoft Docs"
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
  - "ToolBar 控制項 [Windows Form]"
  - "工具列 [Windows Form]"
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# ToolBar 控制項 (Windows Form)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 `ToolBar` 控制項並加入其他功能，不過您也可以選擇保留 `ToolBar` 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form `ToolBar` 控制項在表單中，是當做顯示下拉式功能表其中一列的控制列和啟動命令的點陣圖按鈕使用。  因此，按一下工具列按鈕相當於選擇功能表命令。  您可將這些按鈕設定成和按鈕、下拉式功能表或分隔符號一樣顯示和運作。  一般而言，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。  
  
> [!NOTE]
>  `ToolBar` 控制項的 <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> 屬性會將 <xref:System.Windows.Forms.ContextMenu> 類別的執行個體當做參考。  請仔細考慮在應用程式中實作工具列上這類按鈕時所傳遞的參考，因為這個屬性會接受任何繼承自 <xref:System.Windows.Forms.Menu> 類別的物件。  
  
## 在本節中  
 [ToolBar 控制項概觀](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 介紹 `ToolBar` 控制項的一般概念，讓您能夠設計自訂工具列以供使用者利用。  
  
 [如何：將按鈕加入至 ToolBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 描述如何將按鈕加入 `ToolBar` 控制項。  
  
 [如何：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 描述如何在 `ToolBar` 控制項的按鈕內顯示圖示。  
  
 [如何：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 指示如何撰寫程式碼，來解譯使用者在 `ToolBar` 控制項中按的是哪一個按鈕。  
  
 另請參閱[如何：使用設計工具定義工具列按鈕的圖示](http://msdn.microsoft.com/library/ms233659%20\(v=vs.110\))和[如何：使用設計工具將按鈕加入 ToolBar 控制項](http://msdn.microsoft.com/library/ms233650%20\(v=vs.110\))。  
  
## 參考  
 <xref:System.Windows.Forms.ToolBar> 類別  
 提供這個類別及其成員的相關參考資訊。  
  
## 相關章節  
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 提供 Windows Form 控制項的完整清單及其用法資訊的連結。  
  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 描述可以在 Windows Form 應用程式中裝載功能表、控制項和使用者控制項的工具列。