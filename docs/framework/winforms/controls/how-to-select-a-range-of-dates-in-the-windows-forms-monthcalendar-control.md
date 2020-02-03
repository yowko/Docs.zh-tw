---
title: 在 MonthCalendar 控制項中選取日期範圍
ms.date: 03/30/2017
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
ms.openlocfilehash: bda96af21a8f86a54d5c0fe0204546b980076d26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732891"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍
Windows Forms <xref:System.Windows.Forms.MonthCalendar> 控制項的一項重要功能是，使用者可以選取某個日期範圍。 這項功能改善了 <xref:System.Windows.Forms.DateTimePicker> 控制項的日期選取功能，只允許使用者選取單一日期/時間值。 您可以設定日期範圍，或使用 <xref:System.Windows.Forms.MonthCalendar> 控制項的屬性來取得使用者所設定的選擇範圍。 下列程式碼範例示範如何設定選取範圍。  
  
### <a name="to-select-a-range-of-dates"></a>選取日期範圍  
  
1. 建立 <xref:System.DateTime> 物件，以代表某個範圍中的第一個和最後一個日期。  
  
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
  
2. 設定 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 屬性。  
  
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
  
     請設定 <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> 和 <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> 屬性。  
  
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

- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
- [操作說明：變更 Windows Forms MonthCalendar 控制項的外觀](how-to-change-monthcalendar-control-appearance.md)
- [操作說明：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份](display-more-than-one-month-wf-monthcalendar-control.md)
