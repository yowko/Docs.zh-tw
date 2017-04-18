---
title: "Calendar 樣式和範本 | Microsoft Docs"
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
  - "Calendar [WPF], 樣式和範本"
  - "ControlTemplate [WPF], Calendar"
  - "組件 [WPF], Calendar"
  - "狀態 [WPF], Calendar"
  - "樣式 [WPF], Calendar"
  - "範本 [WPF], Calendar"
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Calendar 樣式和範本
本主題說明 <xref:System.Windows.Controls.Calendar> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## Calendar 組件  
 下表列出 <xref:System.Windows.Controls.Calendar> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|<xref:System.Windows.Controls.Calendar> 上目前顯示的月份或年份。|  
|PART\_Root|<xref:System.Windows.Controls.Panel>|包含 <xref:System.Windows.Controls.Primitives.CalendarItem> 的面板。|  
  
## Calendar 狀態  
 下表列出 <xref:System.Windows.Controls.Calendar> 控制項的可見狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|--------------------|-------------------------|--------|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## CalendarItem 組件  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarItem> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_Root|<xref:System.Windows.FrameworkElement>|控制項的根目錄。|  
|PART\_PreviousButton|<xref:System.Windows.Controls.Button>|按下時會顯示行事曆上一頁的按鈕。|  
|PART\_NextButton|<xref:System.Windows.Controls.Button>|按下時會顯示行事曆下一頁的按鈕。|  
|PART\_HeaderButton|<xref:System.Windows.Controls.Button>|可在月模式、年模式和十年模式之間切換的按鈕。|  
|PART\_MonthView|<xref:System.Windows.Controls.Grid>|採用月模式時裝載內容。|  
|PART\_YearView|<xref:System.Windows.Controls.Grid>|採用年或十年模式時裝載內容。|  
|PART\_DisabledVisual|<xref:System.Windows.FrameworkElement>|停用狀態的重疊。|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|描述視覺化結構的 <xref:System.Windows.DataTemplate>。|  
  
## CalendarItem 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarItem> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal State|CommonStates|預設狀態。|  
|Disabled State|CommonStates|<xref:System.Windows.UIElement.IsEnabled%2A> 屬性是 `false` 時的行事曆狀態。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## CalendarDayButton 組件  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> 控制項沒有任何具名組件。  
  
## CalendarDayButton 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarDayButton> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> 已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.Primitives.CalendarDayButton> 上方。|  
|Pressed|CommonStates|已按下 <xref:System.Windows.Controls.Primitives.CalendarDayButton>。|  
|Selected|SelectionStates|按鈕已選取。|  
|Unselected|SelectionStates|按鈕未選取。|  
|CalendarButtonFocused|CalendarButtonFocusStates|按鈕擁有焦點。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|按鈕沒有焦點。|  
|Focused|FocusStates|按鈕擁有焦點。|  
|Unfocused|FocusStates|按鈕沒有焦點。|  
|Active|ActiveStates|按鈕為作用中。|  
|Inactive|ActiveStates|按鈕非作用中。|  
|RegularDay|DayStates|按鈕不是代表 <xref:System.DateTime.Today%2A?displayProperty=fullName>。|  
|Today|DayStates|按鈕代表 <xref:System.DateTime.Today%2A?displayProperty=fullName>。|  
|NormalDay|BlackoutDayStates|按鈕代表一個可以選取的日子。|  
|BlackoutDay|BlackoutDayStates|按鈕代表一個不可選取的日子。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## CalendarButton 組件  
 <xref:System.Windows.Controls.Primitives.CalendarButton> 控制項沒有任何具名組件。  
  
## CalendarButton 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarButton> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> 已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.Primitives.CalendarButton> 上方。|  
|Pressed|CommonStates|已按下 <xref:System.Windows.Controls.Primitives.CalendarButton>。|  
|Selected|SelectionStates|按鈕已選取。|  
|Unselected|SelectionStates|按鈕未選取。|  
|CalendarButtonFocused|CalendarButtonFocusStates|按鈕擁有焦點。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|按鈕沒有焦點。|  
|Focused|FocusStates|按鈕擁有焦點。|  
|Unfocused|FocusStates|按鈕沒有焦點。|  
|Active|ActiveStates|按鈕為作用中。|  
|Inactive|ActiveStates|按鈕非作用中。|  
|Valid|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，且 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項擁有焦點。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 附加屬性為 `true` 且控制項沒有焦點。|  
  
## Calendar ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.Calendar> 控制項的 <xref:System.Windows.Controls.ControlTemplate> 以及關聯的型別。  
  
 [!code-xml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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