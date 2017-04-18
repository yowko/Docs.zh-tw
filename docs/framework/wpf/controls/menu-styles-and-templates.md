---
title: "Menu 樣式和範本 | Microsoft Docs"
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
  - "ControlTemplate [WPF], 功能表"
  - "Menu [WPF], 樣式和範本"
  - "組件 [WPF], 功能表"
  - "狀態 [WPF], 功能表"
  - "樣式 [WPF], 功能表"
  - "範本 [WPF], 功能表"
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Menu 樣式和範本
本主題說明 <xref:System.Windows.Controls.Menu> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## Menu 組件  
 <xref:System.Windows.Controls.Menu> 控制項沒有任何具名組件。  
  
 當您建立 <xref:System.Windows.Controls.Menu> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.Menu> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
## Menu 狀態  
 下表列出 <xref:System.Windows.Controls.Menu> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## MenuItem 組件  
 下表列出 <xref:System.Windows.Controls.Menu> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|子功能表區域。|  
  
 當您建立 <xref:System.Windows.Controls.MenuItem> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.MenuItem> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
## MenuItem 狀態  
 下表列出 <xref:System.Windows.Controls.MenuItem> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## Menu 和 MenuItem ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.Menu> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 下列範例顯示如何定義 <xref:System.Windows.Controls.MenuItem> 控制項的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 下列範例會定義前述範例所使用的 `MenuScrollViewer`。  
  
 [!code-xml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <xref:System.Windows.Controls.ControlTemplate> 範例使用了下列一項或多項資源。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整範例，請參閱[使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)