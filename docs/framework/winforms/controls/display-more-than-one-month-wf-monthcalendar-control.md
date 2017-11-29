---
title: "如何：在 Windows Form MonthCalendar 控制項中顯示多個月份"
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
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cf236f93fa3352e536c71000f6bb110abf02fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>如何：在 Windows Form MonthCalendar 控制項中顯示多個月份
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示最多 12 個月一次。 根據預設，控制項會顯示一個月，但是您可以指定幾個月的顯示，並且在控制項中的排列方式。 當您變更行事曆維度時，調整控制項大小的因此請務必表單上的新維度沒有足夠的空間。  
  
### <a name="to-display-multiple-months"></a>若要顯示數個月  
  
-   設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>水平及垂直顯示之月份的數字屬性。  
  
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
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [操作說明：變更 Windows Forms MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
