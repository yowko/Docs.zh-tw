---
title: MonthCalendar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 8928a78735392920d893661c70554bd35eba2886
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768481"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項提供直覺式圖形介面，以便讓使用者檢視並設定日期資訊。 控制項顯示的行事曆： 方格，其中包含月、 星期、 天，其中反白顯示的日期選取範圍下方的資料行中排列已編號的天數。 您可以在月份標題的任一邊的箭號按鈕，即可選取不同的月份。 不同於類似<xref:System.Windows.Forms.DateTimePicker>控制項，您可以選取多個與這個控制項的日期。 如需詳細資訊<xref:System.Windows.Forms.DateTimePicker>控制項，請參閱[DateTimePicker 控制項](datetimepicker-control-windows-forms.md)。  
  
## <a name="configuring-the-monthcalendar-control"></a>設定的 MonthCalendar 控制項  
 <xref:System.Windows.Forms.MonthCalendar>控制項的外觀進行大幅設定。 根據預設，今天的日期會圈選起來，會顯示，並且也會註明方格的底部。 您可以變更這項功能，藉由設定<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>並<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A>屬性，以`false`。 您也可以新增到行事曆週數字，藉由設定<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>屬性設`true`。 藉由設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>屬性，您可以有多個顯示月份的水平和垂直大小。 根據預設，星期日會顯示為一週當中的第一天，但您可以指定任何一天，使用<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>屬性。  
  
 您也可以設定要顯示在特定日期一次，每年或每月粗體加<xref:System.DateTime>物件至<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>，和<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性。 如需詳細資訊，請參閱[如何：粗體的顯示特定日期中的使用 Windows Form MonthCalendar 控制項](display-specific-days-in-bold-with-wf-monthcalendar-control.md)。  
  
 索引鍵內容<xref:System.Windows.Forms.MonthCalendar>控制項是<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>，控制項中選取的日期範圍。 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>值不能超過可被選取，在中設定最大天數<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>屬性。 使用者可以選取最早和最新日期由<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>和<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
