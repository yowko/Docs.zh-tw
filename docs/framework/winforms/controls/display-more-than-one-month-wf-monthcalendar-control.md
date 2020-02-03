---
title: 在 MonthCalendar 控制項中顯示超過一個月
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745894"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>如何：在 Windows Form MonthCalendar 控制項中顯示多個月份
Windows Forms <xref:System.Windows.Forms.MonthCalendar> 控制項一次最多可以顯示12個月。 根據預設，控制項只會顯示一個月，但是您可以指定要顯示的月份數，以及它們在控制項內的相片順序。 當您變更行事曆維度時，控制項會調整大小，因此請確定表單上有足夠的空間來容納新的維度。  
  
### <a name="to-display-multiple-months"></a>顯示多個月份  
  
- 將 [<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>] 屬性設定為水準和垂直顯示的月數。  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>另請參閱

- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
- [操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [操作說明：變更 Windows Forms MonthCalendar 控制項的外觀](how-to-change-monthcalendar-control-appearance.md)
