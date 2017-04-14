---
title: "ListBox 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], ListBox"
  - "ListBox [WPF], 樣式和範本"
  - "組件 [WPF], ListBox"
  - "狀態 [WPF], ListBox"
  - "樣式 [WPF], ListBox"
  - "範本 [WPF], ListBox"
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# ListBox 樣式和範本
本主題說明 <xref:System.Windows.Controls.ListBox> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## ListBox 組件  
 <xref:System.Windows.Controls.ListBox> 控制項沒有任何具名組件。  
  
 當您建立 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.ListBox> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
## ListBox 狀態  
 下表列出 <xref:System.Windows.Controls.ListBox> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Valid|ValidationStates|控制項有效。|  
|InvalidFocused|ValidationStates|控制項無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且沒有焦點。|  
  
## ListBoxItem 組件  
 <xref:System.Windows.Controls.ListBoxItem> 控制項沒有任何具名組件。  
  
## ListBoxItem 狀態  
 下表列出 <xref:System.Windows.Controls.ListBox> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於控制項上方。|  
|Disabled|CommonStates|這個項目目前暫止。|  
|Focused|FocusStates|這個項目有焦點。|  
|Unfocused|FocusStates|這個項目沒有焦點。|  
|Unselected|SelectionStates|這個項目目前已選取。|  
|Selected|SelectionStates|這個項目未選取。|  
|SelectedUnfocused|SelectionStates|這個項目已選取，但沒有焦點。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## ListBox ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ListBoxItem> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
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