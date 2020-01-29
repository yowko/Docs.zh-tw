---
title: MonthCalendar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: a9b56164339d03b380a564b21855f6d94ec06af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734935"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.MonthCalendar> 控制項呈現直覺的圖形化介面，讓使用者能夠查看和設定日期資訊。 控制項會顯示一個行事曆：一個方格，其中包含月份的編號日期，並在一周中的資料行下排列，並醒目提示選取的日期範圍。 您可以按一下月份標題任一側的箭號按鈕，以選取不同的月份。 不同于類似的 <xref:System.Windows.Forms.DateTimePicker> 控制項，您可以使用此控制項選取一個以上的日期。 如需 <xref:System.Windows.Forms.DateTimePicker> 控制項的詳細資訊，請參閱[DateTimePicker 控制項](datetimepicker-control-windows-forms.md)。  
  
## <a name="configuring-the-monthcalendar-control"></a>設定 MonthCalendar 控制項  
 <xref:System.Windows.Forms.MonthCalendar> 控制項的外觀可高度設定。 根據預設，今天的日期會顯示為圓形，而且也會在方格底部注明。 您可以將 [<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>] 和 [<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> 屬性] 設定為 [`false`] 來變更此功能。 您也可以將 [<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>] 屬性設定為 [`true`]，以將周數加入行事曆。 藉由設定 [<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>] 屬性，您可以讓多個月以水準和垂直方式顯示。 根據預設，星期日會顯示為一周的第一天，但可以使用 [<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>] 屬性指定任何一天。  
  
 您也可以在 [<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>]、[<xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>] 和 [<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>] 屬性中加入 <xref:System.DateTime> 物件，將特定日期設定為每年一次或每月以粗體顯示。 如需詳細資訊，請參閱[如何：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期](display-specific-days-in-bold-with-wf-monthcalendar-control.md)。  
  
 <xref:System.Windows.Forms.MonthCalendar> 控制項的索引鍵屬性會 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>，也就是在控制項中選取的日期範圍。 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 值不能超過可選取的最多天數，請在 <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> 屬性中設定。 使用者可以選取的最早和最晚日期取決於 [<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>] 和 [<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>] 屬性。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
