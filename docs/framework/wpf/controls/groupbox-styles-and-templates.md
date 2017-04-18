---
title: "GroupBox 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], GroupBox"
  - "GroupBox [WPF], 樣式和範本"
  - "組件 [WPF], GroupBox"
  - "狀態 [WPF], GroupBox"
  - "樣式 [WPF], GroupBox"
  - "範本 [WPF], GroupBox"
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GroupBox 樣式和範本
<a name="introduction"></a> 本主題說明 <xref:System.Windows.Controls.GroupBox> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
<a name="groupbox_parts"></a>   
## GroupBox 組件  
 <xref:System.Windows.Controls.GroupBox> 控制項沒有任何具名組件。  
  
<a name="groupbox_states"></a>   
## GroupBox 狀態  
 下表列出 <xref:System.Windows.Controls.GroupBox> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
<a name="groupbox_controltemplate_example"></a>   
## GroupBox ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.GroupBox> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <xref:System.Windows.Controls.ControlTemplate> 使用下列一個或多個資源。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整範例，請參閱[使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)