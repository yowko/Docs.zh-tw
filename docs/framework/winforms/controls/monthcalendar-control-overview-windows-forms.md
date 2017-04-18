---
title: "MonthCalendar 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MonthCalendar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Calendar 控制項, Windows Form"
  - "行事曆, Windows Form 控制項"
  - "MonthCalendar 控制項 [Windows Form], 設定一週的第一天"
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# MonthCalendar 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.MonthCalendar> 控制項為使用者提供直覺式圖形介面，以檢視和設定日期資訊。  這個控制項會顯示月曆：方格中包含月份中的編號日期，分別排列在星期的天數之下並反白顯示選取的日期範圍。  您可以按一下月份標題兩側的箭頭按鈕來選取不同的月份。  與相似的 <xref:System.Windows.Forms.DateTimePicker> 控制項不同的是，可以使用這個控制項選取一個以上日期。  如需 <xref:System.Windows.Forms.DateTimePicker> 控制項的詳細資訊，請參閱 [DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)。  
  
## 設定 MonthCalendar 控制項  
 <xref:System.Windows.Forms.MonthCalendar> 控制項的外觀可隨意設定。  依預設會將今天的日期以圓形圈出，並且將其附註在方格的下方。  只要將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 和 <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> 屬性設為 `false`，即可變更這項功能。  也可以將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設為 `true`，即可在月曆中加入週數。  設定 <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> 屬性即能以水平方式和垂直方式顯示多個月份。  根據預設，星期日是每週的第一天，但是使用 <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> 屬性就可以將任一天指定為第一天。  
  
 也可以藉由將 <xref:System.DateTime> 物件加入至 <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>、<xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> 和 <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> 屬性，將特定日期設定為單次、每年或每月以粗體字顯示。  如需詳細資訊，請參閱 [如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)。  
  
 <xref:System.Windows.Forms.MonthCalendar> 控制項的主要屬性是 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>，表示在此控制項中已選取的日期範圍。  <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 值不能超過 <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> 屬性中所設定的可選取最多天數。  <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> 和 <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> 屬性決定使用者可選取的最早和最晚日期。  
  
## 請參閱  
 <xref:System.Windows.Forms.MonthCalendar>   
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)