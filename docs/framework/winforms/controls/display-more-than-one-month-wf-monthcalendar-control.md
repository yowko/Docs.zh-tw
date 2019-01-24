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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="6c0d4-102">HOW TO：在 Windows Form MonthCalendar 控制項中顯示超過一個月</span><span class="sxs-lookup"><span data-stu-id="6c0d4-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="6c0d4-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示最多 12 個月一次。</span><span class="sxs-lookup"><span data-stu-id="6c0d4-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="6c0d4-104">根據預設，控制項會顯示一個月，但是您可以指定幾個月會顯示，而且在控制項內的排列方式。</span><span class="sxs-lookup"><span data-stu-id="6c0d4-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="6c0d4-105">當您變更行事曆維度時，控制項調整大小時，因此請務必針對新的維度在表單上沒有足夠的空間。</span><span class="sxs-lookup"><span data-stu-id="6c0d4-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="6c0d4-106">若要顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="6c0d4-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="6c0d4-107">設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>要顯示水平和垂直的月數的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c0d4-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6c0d4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c0d4-108">See also</span></span>
- [<span data-ttu-id="6c0d4-109">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="6c0d4-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="6c0d4-110">如何：在 Windows Form MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="6c0d4-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="6c0d4-111">如何：變更 Windows Form MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="6c0d4-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
