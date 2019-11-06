---
title: 行事曆
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: e99a716e7ca8f7b2c9ed11543f37e0b8cb7422a6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460817"
---
# <a name="calendar"></a>行事曆
行事曆可讓使用者使用視覺行事曆顯示來選取日期。  
  
 <xref:System.Windows.Controls.Calendar> 控制項可以單獨使用，或做為 <xref:System.Windows.Controls.DatePicker> 控制項的下拉部分。 如需詳細資訊，請參閱<xref:System.Windows.Controls.DatePicker>。  
  
 下圖顯示兩個 <xref:System.Windows.Controls.Calendar> 控制項，一個包含選取專案和中斷日期，另一個沒有。  
  
 ![行事曆控制項](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
Calendar 控制項  
  
 下表提供通常與 <xref:System.Windows.Controls.Calendar>相關聯之工作的資訊。  
  
|工作|實作|  
|----------|--------------------|  
|指定無法選取的日期。|請使用 <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> 屬性。|  
|讓 <xref:System.Windows.Controls.Calendar> 顯示一個月、一年，或十年。|將 [<xref:System.Windows.Controls.Calendar.DisplayMode%2A>] 屬性設定為 [月]、[年] 或 [十年]。|  
|指定使用者是否可以選取日期、日期範圍或多個日期範圍。|使用 <xref:System.Windows.Controls.Calendar.SelectionMode%2A>。|  
|指定 <xref:System.Windows.Controls.Calendar> 顯示的日期範圍。|使用 <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> 和 <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> 屬性。|  
|指定是否要反白顯示目前的日期。|請使用 <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> 屬性。 預設會 `true`<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>。|  
|變更 <xref:System.Windows.Controls.Calendar>的大小。|使用 <xref:System.Windows.Controls.Viewbox>，或將 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性設定為 <xref:System.Windows.Media.ScaleTransform>。 請注意，如果您設定 <xref:System.Windows.Controls.Calendar>的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性，實際的行事曆不會變更其大小。|  
  
 <xref:System.Windows.Controls.Calendar> 控制項提供使用滑鼠或鍵盤的基本導覽。 下表摘要說明鍵盤導覽。  
  
|按鍵組合|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|動作|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|箭號|<xref:System.Windows.Controls.CalendarMode.Month>|如果 [<xref:System.Windows.Controls.Calendar.SelectionMode%2A>] 屬性未設定為 [<xref:System.Windows.Controls.CalendarSelectionMode.None>]，則變更 [<xref:System.Windows.Controls.Calendar.SelectedDate%2A>] 屬性。|  
|箭號|<xref:System.Windows.Controls.CalendarMode.Year>|變更 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 屬性的月份。 請注意，<xref:System.Windows.Controls.Calendar.SelectedDate%2A> 不會變更。|  
|箭號|<xref:System.Windows.Controls.CalendarMode.Decade>|變更 <xref:System.Windows.Controls.Calendar.DisplayDate%2A>的年份。 請注意，<xref:System.Windows.Controls.Calendar.SelectedDate%2A> 不會變更。|  
|SHIFT + 箭號|<xref:System.Windows.Controls.CalendarMode.Month>|如果 <xref:System.Windows.Controls.Calendar.SelectionMode%2A> 未設定為 [<xref:System.Windows.Controls.CalendarSelectionMode.SingleDate>] 或 [<xref:System.Windows.Controls.CalendarSelectionMode.None>]，則會擴充所選日期的範圍。|  
|首頁|<xref:System.Windows.Controls.CalendarMode.Month>|將 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 變更為當月的第一天。|  
|首頁|<xref:System.Windows.Controls.CalendarMode.Year>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的月份變更為年份的第一個月。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 不會變更。|  
|首頁|<xref:System.Windows.Controls.CalendarMode.Decade>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 年份變更為十年的第一年。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 不會變更。|  
|END|<xref:System.Windows.Controls.CalendarMode.Month>|將 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 變更為當月的最後一天。|  
|END|<xref:System.Windows.Controls.CalendarMode.Year>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的月份變更為一年中的最後一個月。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 不會變更。|  
|END|<xref:System.Windows.Controls.CalendarMode.Decade>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的年份變更為十年的最後一年內。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 不會變更。|  
|CTRL+向上鍵|Any|切換至下一個較大的 <xref:System.Windows.Controls.Calendar.DisplayMode%2A>。 如果已 <xref:System.Windows.Controls.CalendarMode.Decade><xref:System.Windows.Controls.Calendar.DisplayMode%2A>，則不會執行任何動作。|  
|CTRL+向下鍵|Any|切換至下一個較小的 <xref:System.Windows.Controls.Calendar.DisplayMode%2A>。 如果已 <xref:System.Windows.Controls.CalendarMode.Month><xref:System.Windows.Controls.Calendar.DisplayMode%2A>，則不會執行任何動作。|  
|空格鍵或 ENTER|<xref:System.Windows.Controls.CalendarMode.Year> 或 <xref:System.Windows.Controls.CalendarMode.Decade>|將 <xref:System.Windows.Controls.Calendar.DisplayMode%2A> 切換至以焦點專案表示的 <xref:System.Windows.Controls.CalendarMode.Month> 或 <xref:System.Windows.Controls.CalendarMode.Year>。|  
  
## <a name="see-also"></a>請參閱

- [控制項](index.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
