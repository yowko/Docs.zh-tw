---
title: Calendar 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: 5398828d1526436ab5abbbd2e87515018b0cd8bf
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="calendar-styles-and-templates"></a>Calendar 樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.Calendar>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="calendar-parts"></a>行事曆組件  
 下表列出的具名組件<xref:System.Windows.Controls.Calendar>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|目前顯示的月或年<xref:System.Windows.Controls.Calendar>。|  
|PART_Root|<xref:System.Windows.Controls.Panel>|包含的面板<xref:System.Windows.Controls.Primitives.CalendarItem>。|  
  
## <a name="calendar-states"></a>行事曆狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Calendar>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="calendaritem-parts"></a>CalendarItem 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.CalendarItem>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|控制項的根目錄。|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|按下時會顯示行事曆的上一頁按鈕。|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|按下時會顯示行事曆的下一頁按鈕。|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|允許月模式、 年模式和十年模式之間切換按鈕。|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|裝載在月模式中的內容。|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|裝載在年份或十年模式中的內容。|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|停用狀態的重疊。|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate>視覺化結構描述。|  
  
## <a name="calendaritem-states"></a>CalendarItem 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.CalendarItem>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般狀態|CommonStates|預設狀態。|  
|停用狀態|CommonStates|行事曆的狀態時<xref:System.Windows.UIElement.IsEnabled%2A>屬性是`false`。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton 組件  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton>控制項沒有任何已命名的組件。  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.CalendarDayButton>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton>已停用。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.Primitives.CalendarDayButton>。|  
|按下|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton>按下。|  
|已選取|SelectionStates|選取 [] 按鈕。|  
|未選取|SelectionStates|未選取 [] 按鈕。|  
|CalendarButtonFocused|CalendarButtonFocusStates|按鈕具有焦點。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|按鈕沒有焦點。|  
|已取得焦點|FocusStates|按鈕具有焦點。|  
|未取得焦點|FocusStates|按鈕沒有焦點。|  
|作用中|ActiveStates|作用中 按鈕。|  
|非使用中|ActiveStates|[] 按鈕未作用中。|  
|RegularDay|DayStates|不代表按鈕<xref:System.DateTime.Today%2A?displayProperty=nameWithType>。|  
|今天|DayStates|表示按鈕<xref:System.DateTime.Today%2A?displayProperty=nameWithType>。|  
|NormalDay|BlackoutDayStates|[] 按鈕，表示可以選取一天。|  
|BlackoutDay|BlackoutDayStates|[] 按鈕，表示不選取一天。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="calendarbutton-parts"></a>CalendarButton 組件  
 <xref:System.Windows.Controls.Primitives.CalendarButton>控制項沒有任何已命名的組件。  
  
## <a name="calendarbutton-states"></a>CalendarButton 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.CalendarButton>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton>已停用。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.Primitives.CalendarButton>。|  
|按下|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton>按下。|  
|已選取|SelectionStates|選取 [] 按鈕。|  
|未選取|SelectionStates|未選取 [] 按鈕。|  
|CalendarButtonFocused|CalendarButtonFocusStates|按鈕具有焦點。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|按鈕沒有焦點。|  
|已取得焦點|FocusStates|按鈕具有焦點。|  
|未取得焦點|FocusStates|按鈕沒有焦點。|  
|作用中|ActiveStates|作用中 按鈕。|  
|非使用中|ActiveStates|[] 按鈕未作用中。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="calendar-controltemplate-example"></a>行事曆 ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Calendar>控制項和相關聯的類型。  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
