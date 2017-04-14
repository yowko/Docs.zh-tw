---
title: "TreeView 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], TreeView"
  - "組件 [WPF], TreeView"
  - "狀態 [WPF], TreeView"
  - "樣式 [WPF], TreeView"
  - "範本 [WPF], TreeView"
  - "TreeView [WPF], 樣式和範本"
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# TreeView 樣式和範本
本主題說明 <xref:System.Windows.Controls.TreeView> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## TreeView 組件  
 <xref:System.Windows.Controls.TreeView> 控制項沒有任何具名組件。  
  
 當您建立 <xref:System.Windows.Controls.TreeView> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.TreeView> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
## TreeView 狀態  
 下表列出 <xref:System.Windows.Controls.TreeView> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## TreeViewItem 組件  
 下表列出 <xref:System.Windows.Controls.TreeViewItem> 控制項的具名組件。  
  
|組件|型別|描述|  
|--------|--------|--------|  
|PART\_Header|<xref:System.Windows.FrameworkElement>|視覺化項目，包含 <xref:System.Windows.Controls.TreeView> 控制項的標頭內容。|  
  
## TreeViewItem 狀態  
 下表列出 <xref:System.Windows.Controls.TreeViewItem> 控制項的可見狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|--------------------|-------------------------|--------|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.TreeViewItem> 上方。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.TreeViewItem> 已停用。|  
|Focused|FocusStates|<xref:System.Windows.Controls.TreeViewItem> 有焦點。|  
|Unfocused|FocusStates|<xref:System.Windows.Controls.TreeViewItem> 沒有焦點。|  
|Expanded|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> 控制項已展開。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> 控制項已收合。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> 有項目。|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> 沒有項目。|  
|Selected|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> 已選取。|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> 已選取但非作用中。|  
|Unselected|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> 未選取。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## TreeView ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.TreeView> 控制項的 <xref:System.Windows.Controls.ControlTemplate> 及其關聯的型別。  
  
 [!code-xml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
 前述範例使用了下列一或多項資源。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整範例，請參閱          [使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041) .  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)