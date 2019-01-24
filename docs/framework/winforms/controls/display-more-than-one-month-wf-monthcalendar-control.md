---
title: HOW TO：在 Windows Form MonthCalendar 控制項中顯示超過一個月
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
ms.openlocfilehash: 164369ab1a94249470b57e546db64be8e17b99bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582025"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>HOW TO：在 Windows Form MonthCalendar 控制項中顯示超過一個月
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示最多 12 個月一次。 根據預設，控制項會顯示一個月，但是您可以指定幾個月會顯示，而且在控制項內的排列方式。 當您變更行事曆維度時，控制項調整大小時，因此請務必針對新的維度在表單上沒有足夠的空間。  
  
### <a name="to-display-multiple-months"></a>若要顯示多個月份  
  
-   設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>要顯示水平和垂直的月數的屬性。  
  
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
- [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [如何：在 Windows Form MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [如何：變更 Windows Form MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
