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
ms.openlocfilehash: 49d9ced42572ac06a4ff824ec41a59c14497d215
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460933"
---
# <a name="calendar-styles-and-templates"></a>Calendar 樣式和範本
本主題描述 <xref:System.Windows.Controls.Calendar> 控制項的樣式和範本。 您可以修改預設 <xref:System.Windows.Controls.ControlTemplate>，為控制項提供獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="calendar-parts"></a>行事曆元件  
 下表列出 <xref:System.Windows.Controls.Calendar> 控制項的已命名元件。  
  
|組件|輸入|描述|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|<xref:System.Windows.Controls.Calendar>上目前顯示的月份或年份。|  
|PART_Root|<xref:System.Windows.Controls.Panel>|包含 <xref:System.Windows.Controls.Primitives.CalendarItem>的面板。|  
  
## <a name="calendar-states"></a>行事曆狀態  
 下表列出 <xref:System.Windows.Controls.Calendar> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|----------------------|---------------------------|-----------------|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="calendaritem-parts"></a>CalendarItem 元件  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarItem> 控制項的已命名元件。  
  
|組件|輸入|描述|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|控制項的根。|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|按鈕，會在按下行事曆的上一頁時顯示該頁面。|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|按鈕，會在按下行事曆的下一頁時顯示該頁面。|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|此按鈕可讓您在 [月模式]、[年模式] 和 [十年] 模式之間切換。|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|以月模式主控內容。|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|在年或十年模式下裝載內容。|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|已停用狀態的重迭。|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|描述視覺效果結構的 <xref:System.Windows.DataTemplate>。|  
  
## <a name="calendaritem-states"></a>CalendarItem 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarItem> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|正常狀態|CommonStates|預設狀態。|  
|停用狀態|CommonStates|`false`<xref:System.Windows.UIElement.IsEnabled%2A> 屬性時行事曆的狀態。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton 元件  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> 控制項沒有任何已命名的元件。  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarDayButton> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> 已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.Primitives.CalendarDayButton>上。|  
|按下|CommonStates|已按下 <xref:System.Windows.Controls.Primitives.CalendarDayButton>。|  
|已選取|SelectionStates|已選取此按鈕。|  
|未選取|SelectionStates|未選取此按鈕。|  
|CalendarButtonFocused|CalendarButtonFocusStates|按鈕具有焦點。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|按鈕沒有焦點。|  
|已取得焦點|FocusStates|按鈕具有焦點。|  
|未取得焦點|FocusStates|按鈕沒有焦點。|  
|作用中|ActiveStates|此按鈕為使用中狀態。|  
|非使用中|ActiveStates|此按鈕為非使用中。|  
|RegularDay|DayStates|此按鈕不代表 <xref:System.DateTime.Today%2A?displayProperty=nameWithType>。|  
|今天|DayStates|按鈕代表 <xref:System.DateTime.Today%2A?displayProperty=nameWithType>。|  
|NormalDay|BlackoutDayStates|按鈕代表可選取的日期。|  
|BlackoutDay|BlackoutDayStates|按鈕代表無法選取的日期。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="calendarbutton-parts"></a>CalendarButton 元件  
 <xref:System.Windows.Controls.Primitives.CalendarButton> 控制項沒有任何已命名的元件。  
  
## <a name="calendarbutton-states"></a>CalendarButton 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.CalendarButton> 控制項的視覺狀態。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> 已停用。|  
|MouseOver|CommonStates|滑鼠指標位於 <xref:System.Windows.Controls.Primitives.CalendarButton>上。|  
|按下|CommonStates|已按下 <xref:System.Windows.Controls.Primitives.CalendarButton>。|  
|已選取|SelectionStates|已選取此按鈕。|  
|未選取|SelectionStates|未選取此按鈕。|  
|CalendarButtonFocused|CalendarButtonFocusStates|按鈕具有焦點。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|按鈕沒有焦點。|  
|已取得焦點|FocusStates|按鈕具有焦點。|  
|未取得焦點|FocusStates|按鈕沒有焦點。|  
|作用中|ActiveStates|此按鈕為使用中狀態。|  
|非使用中|ActiveStates|此按鈕為非使用中。|  
|驗證|ValidationStates|控制項使用 <xref:System.Windows.Controls.Validation> 類別，而 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性則 `false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是控制項具有焦點 `true`。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加屬性是 `true` 控制項沒有焦點。|  
  
## <a name="calendar-controltemplate-example"></a>行事曆 ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.Calendar> 控制項和相關聯類型的 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)
