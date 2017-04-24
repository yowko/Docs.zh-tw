---
title: "ContextMenu 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ContextMenu 控制項 [WPF], 關於 ContextMenu 控制項"
  - "控制項, ContextMenu"
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# ContextMenu 概觀
<xref:System.Windows.Controls.ContextMenu> 類別代表利用內容相關 <xref:System.Windows.Controls.Menu> 公開功能的項目。  使用者通常都會透過按一下滑鼠右鍵的方式，在[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中公開 <xref:System.Windows.Controls.ContextMenu>。  本主題將介紹 <xref:System.Windows.Controls.ContextMenu> 項目，並提供如何在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼中使用該項目的範例。  
  
   
  
<a name="contextmenu_control"></a>   
## ContextMenu 控制項  
 <xref:System.Windows.Controls.ContextMenu> 會附加至特定控制項。  <xref:System.Windows.Controls.ContextMenu> 項目可讓您對使用者顯示一份項目清單，其中的項目指定了與特定控制項 \(例如 <xref:System.Windows.Controls.Button>\) 相關聯的命令或選項。  使用者以滑鼠右鍵按一下該控制項即可顯示功能表。  一般來說，按一下 <xref:System.Windows.Controls.MenuItem> 會開啟子功能表，或使應用程式執行命令。  
  
<a name="creating_contextmenus"></a>   
## 建立 ContextMenu  
 下列範例顯示如何建立具有子功能表的 <xref:System.Windows.Controls.ContextMenu>。  <xref:System.Windows.Controls.ContextMenu> 控制項會附加到按鈕控制項。  
  
 [!code-xml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## 將樣式套用至 ContextMenu  
 藉由使用控制項 <xref:System.Windows.Style>，您可以動態變更 <xref:System.Windows.Controls.ContextMenu> 的外觀和行為，而不需要撰寫自訂控制項。  除了設定視覺屬性之外，您也可以將樣式套用到控制項的各部分。  例如，您可以使用屬性變更控制項各部分的行為，也可以增加 <xref:System.Windows.Controls.ContextMenu> 的部分或變更其配置。  下列範例顯示將樣式加入到 <xref:System.Windows.Controls.ContextMenu> 控制項的幾種方式。  
  
 第一個範例會定義一個名為 `SimpleSysResources` 的樣式，顯示如何在樣式中使用目前的系統設定。  這個範例將 <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> 指派為 <xref:System.Windows.Controls.ContextMenu> 的 <xref:System.Windows.Controls.Control.Background%2A> 色彩，並將 <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> 指派為其 <xref:System.Windows.Controls.Control.Foreground%2A> 色彩。  
  
```  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 下列範例使用 <xref:System.Windows.Trigger> 項目變更 <xref:System.Windows.Controls.Menu> 的外觀，以回應 <xref:System.Windows.Controls.ContextMenu> 上引發的事件。  當使用者將滑鼠移到功能表上方時，<xref:System.Windows.Controls.ContextMenu> 項目的外觀就會改變。  
  
```  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## 請參閱  
 <xref:System.Windows.Controls.ContextMenu>   
 <xref:System.Windows.Style>   
 <xref:System.Windows.Controls.Menu>   
 <xref:System.Windows.Controls.MenuItem>   
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)   
 [ContextMenu 樣式和範本](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)   
 [WPF 控制項圖庫範例](http://go.microsoft.com/fwlink/?LinkID=160053)