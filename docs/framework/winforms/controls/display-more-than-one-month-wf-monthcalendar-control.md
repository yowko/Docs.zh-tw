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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="18a62-102">如何：在 Windows Form MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="18a62-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="18a62-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> 控制項一次最多可以顯示12個月。</span><span class="sxs-lookup"><span data-stu-id="18a62-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="18a62-104">根據預設，控制項只會顯示一個月，但是您可以指定要顯示的月份數，以及它們在控制項內的相片順序。</span><span class="sxs-lookup"><span data-stu-id="18a62-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="18a62-105">當您變更行事曆維度時，控制項會調整大小，因此請確定表單上有足夠的空間來容納新的維度。</span><span class="sxs-lookup"><span data-stu-id="18a62-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="18a62-106">顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="18a62-106">To display multiple months</span></span>  
  
- <span data-ttu-id="18a62-107">將 [<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>] 屬性設定為水準和垂直顯示的月數。</span><span class="sxs-lookup"><span data-stu-id="18a62-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="18a62-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="18a62-108">See also</span></span>

- [<span data-ttu-id="18a62-109">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="18a62-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="18a62-110">操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="18a62-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="18a62-111">操作說明：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="18a62-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
