---
title: "如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d6a8d156e6e9a8c5331bd3db1c8e584be5ac154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍
一項重要功能的 Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項是使用者可以選取日期範圍。 這項功能是改良的日期選取功能<xref:System.Windows.Forms.DateTimePicker>控制項，僅可讓使用者選取的單一日期/時間值。 您可以設定的日期範圍，或取得使用者所使用的屬性設定的選取範圍<xref:System.Windows.Forms.MonthCalendar>控制項。 下列程式碼範例示範如何設定選取範圍。  
  
### <a name="to-select-a-range-of-dates"></a>若要選取日期範圍  
  
1.  建立<xref:System.DateTime>代表第一個和最後一個日期範圍內的物件。  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  設定 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 屬性。  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     -或-  
  
     設定 <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> 和 <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> 屬性。  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [操作說明：變更 Windows Forms MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [操作說明：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
