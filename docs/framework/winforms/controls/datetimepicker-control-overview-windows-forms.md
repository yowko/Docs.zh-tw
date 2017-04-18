---
title: "DateTimePicker 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "DateTimePicker"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "日期時間選擇器控制項"
  - "DateTimePicker 控制項 [Windows Form], 關於"
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DateTimePicker 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.DateTimePicker> 控制項允許使用者從日期或時間清單中選取單一項目。  當用來表示日期時，它有兩個部分：用文字顯示日期的下拉式清單 \(Drop\-Down List\)，和按一下清單旁的向下箭頭時所出現的方格。  方格看起來像是可以用來選取多個日期的 <xref:System.Windows.Forms.MonthCalendar> 控制項。  如需 <xref:System.Windows.Forms.MonthCalendar> 控制項的詳細資訊，請參閱[MonthCalendar 控制項概觀](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md)。  
  
## 主要屬性  
 如果希望 <xref:System.Windows.Forms.DateTimePicker> 顯示為選擇或編輯時間 \(而非日期\) 的控制項，請將 <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> 屬性設為 `true` 並且將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設為 <xref:System.Windows.Forms.DateTimePickerFormat>。  如需詳細資訊，請參閱[如何：使用 DateTimePicker 控制項顯示時間](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md)。  
  
 當將 <xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A> 屬性設為 `true` 時，控制項中所選取的日期旁會出現核取方塊。  當選取核取方塊時，可以更新選取的日期時間值。  當核取方塊為空白時，就無法選取值。  
  
 控制項的 <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> 和 <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> 屬性可決定日期和時間的範圍。  <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性包含設定控制項的目前日期和時間。  如需詳細資訊，請參閱 [如何：使用 Windows Form DateTimePicker 控制項設定和傳回日期](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)。  此值可用以下四種格式顯示，這些格式是由 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定：<xref:System.Windows.Forms.DateTimePickerFormat>、<xref:System.Windows.Forms.DateTimePickerFormat>、<xref:System.Windows.Forms.DateTimePickerFormat> 或 <xref:System.Windows.Forms.DateTimePickerFormat>。  如果選取自訂格式，必須將 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 屬性設為適當的字串。  如需詳細資訊，請參閱 [如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)。  
  
## 請參閱  
 [如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)   
 [如何：使用 Windows Form DateTimePicker 控制項設定和傳回日期](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)