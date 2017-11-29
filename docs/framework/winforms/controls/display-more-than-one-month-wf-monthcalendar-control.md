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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="8e60b-102">如何：在 Windows Form MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="8e60b-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="8e60b-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示最多 12 個月一次。</span><span class="sxs-lookup"><span data-stu-id="8e60b-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="8e60b-104">根據預設，控制項會顯示一個月，但是您可以指定幾個月的顯示，並且在控制項中的排列方式。</span><span class="sxs-lookup"><span data-stu-id="8e60b-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="8e60b-105">當您變更行事曆維度時，調整控制項大小的因此請務必表單上的新維度沒有足夠的空間。</span><span class="sxs-lookup"><span data-stu-id="8e60b-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="8e60b-106">若要顯示數個月</span><span class="sxs-lookup"><span data-stu-id="8e60b-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="8e60b-107">設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>水平及垂直顯示之月份的數字屬性。</span><span class="sxs-lookup"><span data-stu-id="8e60b-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8e60b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e60b-108">See Also</span></span>  
 [<span data-ttu-id="8e60b-109">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="8e60b-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="8e60b-110">操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="8e60b-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="8e60b-111">操作說明：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="8e60b-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
