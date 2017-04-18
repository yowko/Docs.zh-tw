---
title: "ToggleButton 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], ToggleButton"
  - "組件 [WPF], ToggleButton"
  - "狀態 [WPF], ToggleButton"
  - "樣式 [WPF], ToggleButton"
  - "範本 [WPF], ToggleButton"
  - "ToggleButton [WPF], 樣式和範本"
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# ToggleButton 樣式和範本
本主題說明 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## ToggleButton 組件  
 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項沒有任何具名組件。  
  
## ToggleButton 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於控制項上方。|  
|Pressed|CommonStates|已按下控制項。|  
|Disabled|CommonStates|控制項已停用。|  
|Focused|FocusStates|控制項擁有焦點。|  
|Unfocused|FocusStates|控制項沒有焦點。|  
|Checked|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `true`。|  
|Unchecked|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `false`。|  
|Indeterminate|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> 為 `true`，而 <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> 為 `null`。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
> [!NOTE]
>  如果控制項範本沒有不定視覺狀態，未核取視覺狀態就會做為預設視覺狀態。  
  
## ToggleButton ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.Primitives.ToggleButton> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
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