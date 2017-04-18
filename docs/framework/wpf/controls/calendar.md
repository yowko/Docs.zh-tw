---
title: "Calendar | Microsoft Docs"
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
  - "Calendar 控制項 [WPF]"
  - "控制項 [WPF], Calendar"
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Calendar
行事曆可以讓使用者使用視覺化行事曆顯示來選取日期。  
  
 <xref:System.Windows.Controls.Calendar> 控制項可以獨自使用，或是當做 <xref:System.Windows.Controls.DatePicker> 控制項的下拉式部分使用。  如需詳細資訊，請參閱 <xref:System.Windows.Controls.DatePicker>。  
  
 下圖顯示兩個 <xref:System.Windows.Controls.Calendar> 控制項，一個控制項有包含選取範圍和停機日，另一個則沒有。  
  
 ![Calendar 控制項](../../../../docs/framework/wpf/controls/media/ndp-calendarcontrols.png "NDP\_CalendarControls")  
Calendar 控制項  
  
 下表提供通常與 <xref:System.Windows.Controls.Calendar> 相關聯之工作的相關資訊。  
  
|工作|實作|  
|--------|--------|  
|指定不能選取的日期。|使用 <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> 屬性。|  
|讓 <xref:System.Windows.Controls.Calendar> 顯示一個月、一整年或十年。|將 <xref:System.Windows.Controls.Calendar.DisplayMode%2A> 屬性設定為 \[月\]、\[年\] 或 \[十年\]。|  
|指定使用者是否可以選取日期、日期範圍，或多個範圍的日期。|使用 <xref:System.Windows.Controls.Calendar.SelectionMode%2A>|  
|指定 <xref:System.Windows.Controls.Calendar> 顯示的日期範圍。|請使用 <xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> 和 <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> 屬性。|  
|指定是否反白顯示目前的日期。|使用 <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> 屬性。  根據預設，<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> 為 `true`。|  
|變更 <xref:System.Windows.Controls.Calendar> 的大小。|使用 <xref:System.Windows.Controls.Viewbox>，或將 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性設定為 <xref:System.Windows.Media.ScaleTransform>。  請注意，如果您設定 <xref:System.Windows.Controls.Calendar> 的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性，真正的日曆不會變更其大小。|  
  
 <xref:System.Windows.Controls.Calendar> 控制項會提供使用滑鼠或鍵盤的基本巡覽。  下表摘要列出鍵盤巡覽。  
  
|組合鍵|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|動作|  
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|--------|  
|方向鍵|<xref:System.Windows.Controls.CalendarMode>|如果 <xref:System.Windows.Controls.Calendar.SelectionMode%2A> 屬性未設為 <xref:System.Windows.Controls.CalendarSelectionMode>，則變更 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 屬性。|  
|方向鍵|<xref:System.Windows.Controls.CalendarMode>|變更 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 屬性的月份。  請注意，<xref:System.Windows.Controls.Calendar.SelectedDate%2A> 並不會變更。|  
|方向鍵|<xref:System.Windows.Controls.CalendarMode>|變更 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的年份。  請注意，<xref:System.Windows.Controls.Calendar.SelectedDate%2A> 並不會變更。|  
|SHIFT\+方向鍵|<xref:System.Windows.Controls.CalendarMode>|如果 <xref:System.Windows.Controls.Calendar.SelectionMode%2A> 未設為 <xref:System.Windows.Controls.CalendarSelectionMode> 或 <xref:System.Windows.Controls.CalendarSelectionMode>，則延伸選取日期範圍。|  
|HOME|<xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 變更為目前月份的第一天。|  
|HOME|<xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的月份變更為該年的第一個月。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 並不會變更。|  
|HOME|<xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的年份變更為十年中的第一年。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 並不會變更。|  
|END|<xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 變更為目前月份的最後一天。|  
|END|<xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的月份變更為該年的最後一個月。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 並不會變更。|  
|END|<xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 的年份變更為十年中的最後一年。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> 並不會變更。|  
|CTRL\+ 向上鍵|Any|切換至下一個更大的 <xref:System.Windows.Controls.Calendar.DisplayMode%2A>。  如果 <xref:System.Windows.Controls.Calendar.DisplayMode%2A> 已經是 <xref:System.Windows.Controls.CalendarMode>，則不會採取任何動作。|  
|CTRL\+ 向下鍵|Any|切換至下一個更小的 <xref:System.Windows.Controls.Calendar.DisplayMode%2A>。  如果 <xref:System.Windows.Controls.Calendar.DisplayMode%2A> 已經是 <xref:System.Windows.Controls.CalendarMode>，則不會採取任何動作。|  
|空白鍵或 ENTER|<xref:System.Windows.Controls.CalendarMode> 或 <xref:System.Windows.Controls.CalendarMode>|將 <xref:System.Windows.Controls.Calendar.DisplayMode%2A> 切換至焦點項目所表示的 <xref:System.Windows.Controls.CalendarMode> 或 <xref:System.Windows.Controls.CalendarMode>。|  
  
## 請參閱  
 [控制項](../../../../docs/framework/wpf/controls/index.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)