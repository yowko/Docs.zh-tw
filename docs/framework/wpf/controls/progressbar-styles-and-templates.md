---
title: "ProgressBar 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], ProgressBar"
  - "組件 [WPF], ProgressBar"
  - "ProgressBar [WPF], 樣式和範本"
  - "狀態 [WPF], ProgressBar"
  - "樣式 [WPF], ProgressBar"
  - "範本 [WPF], ProgressBar"
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# ProgressBar 樣式和範本
本主題說明 <xref:System.Windows.Controls.ProgressBar> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## ProgressBar 組件  
 下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_Indicator|<xref:System.Windows.FrameworkElement>|指示進度的物件。|  
|PART\_Track|<xref:System.Windows.FrameworkElement>|定義進度列指示器路徑的物件。|  
|PART\_GlowRect|<xref:System.Windows.FrameworkElement>|裝飾進度列的物件。|  
  
## ProgressBar 狀態  
 下表列出 <xref:System.Windows.Controls.ProgressBar> 控制項的可見狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|--------------------|-------------------------|--------|  
|Determinate|CommonStates|<xref:System.Windows.Controls.ProgressBar> 是以 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> 屬性為基礎來報告進度。|  
|Indeterminate|CommonStates|<xref:System.Windows.Controls.ProgressBar> 會報告具有重複模式的一般進度。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## ProgressBar ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.ProgressBar> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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