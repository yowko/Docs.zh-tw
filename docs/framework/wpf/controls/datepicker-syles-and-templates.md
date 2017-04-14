---
title: "DatePicker 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], DatePicker"
  - "DatePicker [WPF], 樣式和範本"
  - "組件 [WPF], DatePicker"
  - "狀態 [WPF], DatePicker"
  - "樣式 [WPF], DatePicker"
  - "範本 [WPF], DatePicker"
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# DatePicker 樣式和範本
本主題說明 <xref:System.Windows.Controls.DatePicker> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## DatePicker 組件  
 下表列出 <xref:System.Windows.Controls.DatePicker> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_Root|<xref:System.Windows.Controls.Grid>|控制項的根目錄。|  
|PART\_Button|<xref:System.Windows.Controls.Button>|會開啟及關閉 <xref:System.Windows.Controls.Calendar> 的按鈕。|  
|PART\_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|可讓您輸入日期的文字方塊。|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|<xref:System.Windows.Controls.DatePicker> 控制項的快顯功能表。|  
  
## DatePicker 狀態  
 下表列出 <xref:System.Windows.Controls.DatePicker> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.DatePicker> 已停用。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## DatePickerTextBox 組件  
 下表列出 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_Watermark|<xref:System.Windows.Controls.ContentControl>|項目，包含 <xref:System.Windows.Controls.DatePicker> 中的初始文字。|  
|PART\_ContentElement|<xref:System.Windows.FrameworkElement>|可包含 <xref:System.Windows.FrameworkElement> 的視覺化項目。  <xref:System.Windows.Controls.TextBox> 的文字會顯示在此項目中。|  
  
## DatePickerTextBox 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> 已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 上方。|  
|ReadOnly|CommonStates|使用者無法變更 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 中的文字。|  
|Focused|FocusStates|控制項擁有焦點。|  
|Unfocused|FocusStates|控制項沒有焦點。|  
|Watermarked|WatermarkStates|控制項會顯示其初始文字。  使用者尚未輸入文字或選取日期時，<xref:System.Windows.Controls.Primitives.DatePickerTextBox> 會處於此狀態。|  
|Unwatermarked|WatermarkStates|使用者已在 <xref:System.Windows.Controls.Primitives.DatePickerTextBox> 中輸入文字，或在 <xref:System.Windows.Controls.DatePicker> 中選取日期。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## DatePicker ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.DatePicker> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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