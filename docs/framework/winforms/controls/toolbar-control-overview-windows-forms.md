---
title: "ToolBar 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "ToolBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolBar 控制項 [Windows Form], 關於 ToolBar 控制項"
  - "工具列 [Windows Form], 關於工具列"
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# ToolBar 控制項概觀 (Windows Form)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form <xref:System.Windows.Forms.ToolBar> 控制項在表單中是當做顯示下拉式功能表 \(Drop\-Down Menu\) 其中一列的控制列 \(Control Bar\) 和啟動命令的點陣圖按鈕使用。  因此，按一下工具列按鈕相當於選擇功能表命令。  您可將這些按鈕設定成和按鈕、下拉式功能表或分隔符號一樣顯示和運作。  一般來說，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。  
  
## 使用工具列控制項  
 <xref:System.Windows.Forms.ToolBar> 控制項通常沿著它的父視窗上方停駐，不過它也可以在視窗的任何一邊停駐。  當使用者將滑鼠指標指向工具列按鈕時，工具列即可顯示工具提示。  工具提示是個簡要描述按鈕或功能表用途的小型快顯視窗。  若要顯示工具提示，您必須將 <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> 屬性設定為 `true`。  
  
> [!NOTE]
>  某些應用程式所具備的控制項非常類似具有「漂浮」在應用程式視窗上方和重新調整位置能力的工具列。  Windows Form ToolBar 控制項無法執行這些動作。  
  
 當 <xref:System.Windows.Forms.ToolBar.Appearance%2A> 屬性設定為 [Normal](frlrfSystemWindowsFormsToolBarAppearanceClassTopic) 時，工具列按鈕便會凸起成 3D 狀。  您可以將工具列的 <xref:System.Windows.Forms.ToolBar.Appearance%2A> 屬性設定為 <xref:System.Windows.Forms.ToolBarAppearance>，將工具列及其按鈕的外觀設定為平面。  當滑鼠指標移過平面按鈕時，按鈕的外觀會變更為 3D。  您可使用分隔符號來將工具列按鈕分為幾個邏輯群組。  分隔符號就是將 <xref:System.Windows.Forms.ToolBarButton.Style%2A> 屬性設定為 [Separator](frlrfSystemWindowsFormsToolBarButtonStyleClassTopic) 的工具列按鈕。  它在工具列中會顯示為空格。  當將工具列的外觀設定為平面時，按鈕分隔符號在按鈕之間會顯示為直線而不是空格。  
  
 <xref:System.Windows.Forms.ToolBar> 控制項可讓您建立工具列，方法是將 <xref:System.Windows.Forms.Button> 物件加入 <xref:System.Windows.Forms.ToolBar.Buttons%2A> 集合。  您可以使用 \[集合編輯器\]，將按鈕加入 <xref:System.Windows.Forms.ToolBar> 控制項；每個 <xref:System.Windows.Forms.Button> 物件都應有指派的文字或影像，不過您可同時指派兩者。  影像是由關聯的 [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) 元件提供。  在執行階段，您可以使用 <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> 和 <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> 方法在 <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> 中加入或移除按鈕。  若要進行 <xref:System.Windows.Forms.ToolBar> 之按鈕的程式設計，請將程式碼加入 <xref:System.Windows.Forms.ToolBar> 的 <xref:System.Windows.Forms.ToolBar.ButtonClick> 事件，以 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> 類別 \(Class\) 的 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> 屬性來判斷所按下的按鈕。  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolBar>   
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [如何：將按鈕加入至 ToolBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)   
 [如何：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [如何：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)