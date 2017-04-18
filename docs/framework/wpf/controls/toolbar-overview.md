---
title: "工具列概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "控制項, ToolBar"
  - "ToolBar 控制項"
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# 工具列概觀
<xref:System.Windows.Controls.ToolBar> 控制項是包含一組命令或控制項的容器，這些命令或控制項通常與其功能相關。  <xref:System.Windows.Controls.ToolBar> 通常包含會叫用 \(Invoke\) 命令的按鈕。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="ToolBarControl"></a>   
## 工具列控制項  
 <xref:System.Windows.Controls.ToolBar> 控制項的名稱，取自於按鈕或其他控制項排列成單列或單欄的條狀外觀。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> 控制項會提供一項溢位機制，可以將無法自然放入有大小限制之 <xref:System.Windows.Controls.ToolBar> 內的任何項目放入特定的溢位區域。  同時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> 控制項通常會與相關的 <xref:System.Windows.Controls.ToolBarTray> 控制項一起使用，以提供特殊的配置行為並支援使用者啟始的工具列大小設定及排列。  
  
<a name="Creating_ToolBars"></a>   
## 指定工具列在 ToolBarTray 中的位置  
 使用 <xref:System.Windows.Controls.ToolBar.Band%2A> 和 <xref:System.Windows.Controls.ToolBar.BandIndex%2A> 屬性以指定 <xref:System.Windows.Controls.ToolBar> 在 <xref:System.Windows.Controls.ToolBarTray> 中的位置。  <xref:System.Windows.Controls.ToolBar.Band%2A> 表示 <xref:System.Windows.Controls.ToolBar> 在其父 <xref:System.Windows.Controls.ToolBarTray> 內的放置位置。  <xref:System.Windows.Controls.ToolBar.BandIndex%2A> 表示 <xref:System.Windows.Controls.ToolBar> 在其群組列內的放置順序。  下列範例顯示如何使用這個屬性將 <xref:System.Windows.Controls.ToolBar> 控制項放置在 <xref:System.Windows.Controls.ToolBarTray> 內。  
  
 [!code-xml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## 具有溢位項目的工具列  
 通常 <xref:System.Windows.Controls.ToolBar> 控制項會包含超過工具列大小可以容納的項目。  當這種情況發生時，<xref:System.Windows.Controls.ToolBar> 會顯示溢位按鈕。  若要查看溢位項目，使用者可以按一下溢位按鈕，然後項目就會顯示在 <xref:System.Windows.Controls.ToolBar> 底下的快顯視窗 \(Pop\-Up Window\)。  下圖顯示具有溢位項目的 <xref:System.Windows.Controls.ToolBar>。  
  
 ![包含超出項目的工具列](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
具有溢位項目的工具列  
  
 您可以指定工具列上的項目放置到溢位面板的時機，方法是將 <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=fullName> 附加屬性設為 <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName>、<xref:System.Windows.Controls.OverflowMode?displayProperty=fullName> 或 <xref:System.Windows.Controls.OverflowMode?displayProperty=fullName>。  下列範例會指定工具列上的最後四個按鈕應該一律位在溢位面板上。  
  
 [!code-xml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> 會在其 <xref:System.Windows.Controls.ControlTemplate> 中使用 <xref:System.Windows.Controls.Primitives.ToolBarPanel> 和 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>。  <xref:System.Windows.Controls.Primitives.ToolBarPanel> 負責工具列上項目的配置。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> 負責不符合 <xref:System.Windows.Controls.ToolBar> 之項目的配置。  如需 <xref:System.Windows.Controls.ToolBar> 之 <xref:System.Windows.Controls.ControlTemplate> 的範例，請參閱  
  
 [ToolBar 樣式和範本](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).  
  
## 請參閱  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>   
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>   
 [工具列上的樣式控制項](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)   
 [WPF 控制項圖庫範例](http://go.microsoft.com/fwlink/?LinkID=160053)