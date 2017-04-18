---
title: "ToolBar 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], ToolBar"
  - "組件 [WPF], ToolBar"
  - "狀態 [WPF], ToolBar"
  - "樣式 [WPF], ToolBar"
  - "範本 [WPF], ToolBar"
  - "ToolBar [WPF], 樣式和範本"
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# ToolBar 樣式和範本
本主題說明 <xref:System.Windows.Controls.ToolBar> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## ToolBar 組件  
 下表列出 <xref:System.Windows.Controls.ToolBar> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_ToolBarPanel|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|物件，包含 <xref:System.Windows.Controls.ToolBar> 上的控制項。|  
|PART\_ToolBarOverflowPanel|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|物件，包含位於 <xref:System.Windows.Controls.ToolBar> 溢位區域中的控制項。|  
  
 當您建立 <xref:System.Windows.Controls.ToolBar> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.ToolBar> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
## ToolBar 狀態  
 下表列出 <xref:System.Windows.Controls.ToolBar> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## ToolBar ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ToolBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 前述範例使用了下列一或多項資源。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整範例，請參閱[使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)