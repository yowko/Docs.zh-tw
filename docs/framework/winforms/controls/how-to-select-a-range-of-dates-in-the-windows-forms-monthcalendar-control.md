---
title: HOW TO：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍
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
ms.openlocfilehash: 82d0499cb40f79a3110b8432fbee66774bcc14a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332231"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="23241-102">HOW TO：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="23241-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="23241-103">一項重要功能的 Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項是使用者可以選取日期範圍。</span><span class="sxs-lookup"><span data-stu-id="23241-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="23241-104">這項功能是改良的日期選取項目功能<xref:System.Windows.Forms.DateTimePicker>控制項，只讓使用者可以選取單一日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="23241-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="23241-105">您可以設定日期範圍，或取得使用者所使用的屬性設定的選取範圍<xref:System.Windows.Forms.MonthCalendar>控制項。</span><span class="sxs-lookup"><span data-stu-id="23241-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="23241-106">下列程式碼範例示範如何設定選取範圍。</span><span class="sxs-lookup"><span data-stu-id="23241-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="23241-107">若要選取的日期範圍</span><span class="sxs-lookup"><span data-stu-id="23241-107">To select a range of dates</span></span>  
  
1. <span data-ttu-id="23241-108">建立<xref:System.DateTime>代表第一個和最後一個日期範圍中的物件。</span><span class="sxs-lookup"><span data-stu-id="23241-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2. <span data-ttu-id="23241-109">設定 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="23241-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="23241-110">-或-</span><span class="sxs-lookup"><span data-stu-id="23241-110">–or–</span></span>  
  
     <span data-ttu-id="23241-111">設定 <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> 和 <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="23241-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23241-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23241-112">See also</span></span>

- [<span data-ttu-id="23241-113">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="23241-113">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="23241-114">如何：變更 Windows Form MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="23241-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="23241-115">如何：粗體的顯示特定日期中的使用 Windows Form MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="23241-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="23241-116">如何：在 Windows Form MonthCalendar 控制項中顯示超過一個月</span><span class="sxs-lookup"><span data-stu-id="23241-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
