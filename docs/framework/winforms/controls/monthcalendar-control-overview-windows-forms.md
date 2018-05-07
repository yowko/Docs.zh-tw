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
ms.openlocfilehash: 7ed917afe2640fe2ffef4904a3795c5f0e84ded9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項提供直覺式的圖形化介面，以便讓使用者檢視並設定日期資訊。 控制項會顯示行事曆： 包含編號的日期的月份，在底下的反白顯示的日期選取範圍的每週天數的資料行中排列方格。 您可以透過按一下月份標題的任一邊的箭號按鈕選取不同的月份。 不同於類似<xref:System.Windows.Forms.DateTimePicker>控制項，您可以選取多個與這個控制項的日期。 如需有關<xref:System.Windows.Forms.DateTimePicker>控制，請參閱[DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)。  
  
## <a name="configuring-the-monthcalendar-control"></a>設定的 MonthCalendar 控制項  
 <xref:System.Windows.Forms.MonthCalendar>控制項的外觀會高度設定的基礎。 根據預設，今天的日期會顯示為圈選起來，而且也會註明在方格的底部。 您可以變更這項功能，藉由設定<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>和<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A>屬性`false`。 您也可以加入至行事曆週數，方法是設定<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>屬性`true`。 藉由設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>屬性，您可以有多個顯示月份的水平或垂直。 根據預設，星期日會顯示為每週的第一天，但您可使用指定任何一天<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>屬性。  
  
 您也可以設定顯示在特定日期一次，每年，或每月粗體加<xref:System.DateTime>物件加入至<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>，和<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性。 如需詳細資訊，請參閱[How to： 在 Windows Form MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)。  
  
 索引鍵內容<xref:System.Windows.Forms.MonthCalendar>控制項是<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>，控制項中選取日期範圍。 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>值不能超過可選取、 在 設定最大天數<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>屬性。 使用者可以選取的最早和最新日期由<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>和<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MonthCalendar>  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
