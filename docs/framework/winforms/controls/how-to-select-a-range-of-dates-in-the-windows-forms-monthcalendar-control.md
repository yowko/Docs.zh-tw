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
ms.workload: dotnet
ms.openlocfilehash: 32555097c25a23ca1de6e20308a420d3ec70caf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="56966-102">如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="56966-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="56966-103">一項重要功能的 Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項是使用者可以選取日期範圍。</span><span class="sxs-lookup"><span data-stu-id="56966-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="56966-104">這項功能是改良的日期選取功能<xref:System.Windows.Forms.DateTimePicker>控制項，僅可讓使用者選取的單一日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="56966-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="56966-105">您可以設定的日期範圍，或取得使用者所使用的屬性設定的選取範圍<xref:System.Windows.Forms.MonthCalendar>控制項。</span><span class="sxs-lookup"><span data-stu-id="56966-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="56966-106">下列程式碼範例示範如何設定選取範圍。</span><span class="sxs-lookup"><span data-stu-id="56966-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="56966-107">若要選取日期範圍</span><span class="sxs-lookup"><span data-stu-id="56966-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="56966-108">建立<xref:System.DateTime>代表第一個和最後一個日期範圍內的物件。</span><span class="sxs-lookup"><span data-stu-id="56966-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2.  <span data-ttu-id="56966-109">設定 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="56966-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="56966-110">-或-</span><span class="sxs-lookup"><span data-stu-id="56966-110">–or–</span></span>  
  
     <span data-ttu-id="56966-111">設定 <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> 和 <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="56966-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="56966-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="56966-112">See Also</span></span>  
 [<span data-ttu-id="56966-113">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="56966-113">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="56966-114">操作說明：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="56966-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="56966-115">操作說明：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期</span><span class="sxs-lookup"><span data-stu-id="56966-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="56966-116">操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="56966-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
