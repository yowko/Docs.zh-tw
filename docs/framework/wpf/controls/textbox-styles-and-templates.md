---
title: "TextBox 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], TextBox"
  - "組件 [WPF], TextBox"
  - "狀態 [WPF], TextBox"
  - "樣式 [WPF], TextBox"
  - "範本 [WPF], TextBox"
  - "TextBox [WPF], 樣式和範本"
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# TextBox 樣式和範本
本主題說明 <xref:System.Windows.Controls.TextBox> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## TextBox 組件  
 下表列出 <xref:System.Windows.Controls.TextBox> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_ContentHost|<xref:System.Windows.FrameworkElement>|可包含 <xref:System.Windows.FrameworkElement> 的視覺化項目。  <xref:System.Windows.Controls.TextBox> 的文字會顯示在此項目中。|  
  
## TextBox 狀態  
 下表列出 <xref:System.Windows.Controls.TextBox> 控制項的可見狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|--------------------|-------------------------|--------|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於控制項上方。|  
|Disabled|CommonStates|控制項已停用。|  
|ReadOnly|CommonStates|使用者無法變更 <xref:System.Windows.Controls.TextBox> 中的文字。|  
|Focused|FocusStates|控制項擁有焦點。|  
|Unfocused|FocusStates|控制項沒有焦點。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## TextBox ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.TextBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
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