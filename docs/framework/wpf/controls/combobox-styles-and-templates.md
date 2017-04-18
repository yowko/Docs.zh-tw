---
title: "ComboBox 樣式和範本 | Microsoft Docs"
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
  - "ComboBox [WPF], 樣式和範本"
  - "ControlTemplate [WPF], ComboBox"
  - "組件 [WPF], ComboBox"
  - "狀態 [WPF], ComboBox"
  - "樣式 [WPF], ComboBox"
  - "範本 [WPF], ComboBox"
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# ComboBox 樣式和範本
本主題說明 <xref:System.Windows.Controls.ComboBox> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## ComboBox 組件  
 下表列出 <xref:System.Windows.Controls.ComboBox> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_EditableTextBox|<xref:System.Windows.Controls.TextBox>|包含 <xref:System.Windows.Controls.ComboBox> 的文字。|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|包含下拉式方塊中項目的下拉式清單。|  
  
 當您建立 <xref:System.Windows.Controls.ComboBox> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.ComboBox> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
## ComboBox 狀態  
 下表列出 <xref:System.Windows.Controls.ComboBox> 控制項的狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|控制項已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.ComboBox> 控制項上方。|  
|Focused|FocusStates|控制項擁有焦點。|  
|Unfocused|FocusStates|控制項沒有焦點。|  
|FocusedDropDown|FocusStates|<xref:System.Windows.Controls.ComboBox> 的下拉式清單擁有焦點。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
|Editable|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 屬性為 `true`。|  
|Uneditable|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 屬性為 `false`。|  
  
## ComboBoxItem 組件  
 <xref:System.Windows.Controls.ComboBoxItem> 控制項沒有任何具名組件。  
  
## ComboBoxItem 狀態  
 下表列出 <xref:System.Windows.Controls.ComboBoxItem> 控制項的狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|控制項已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.ComboBox> 控制項上方。|  
|Focused|FocusStates|控制項擁有焦點。|  
|Unfocused|FocusStates|控制項沒有焦點。|  
|Selected|SelectionStates|這個項目目前已選取。|  
|Unselected|SelectionStates|這個項目未選取。|  
|SelectedUnfocused|SelectionStates|這個項目已選取，但沒有焦點。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## ComboBox ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ComboBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate> 以及關聯的型別。  
  
 [!code-xml[ControlTemplateExamples#ComboBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
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