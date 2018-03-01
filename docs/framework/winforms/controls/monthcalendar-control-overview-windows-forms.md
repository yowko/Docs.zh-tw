---
title: "MonthCalendar 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a22667e4227067dfbf0baaad1838ab520e0ac7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="monthcalendar-control-overview-windows-forms"></a><span data-ttu-id="a9d7b-102">MonthCalendar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a9d7b-102">MonthCalendar Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a9d7b-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項提供直覺式的圖形化介面，以便讓使用者檢視並設定日期資訊。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control presents an intuitive graphical interface for users to view and set date information.</span></span> <span data-ttu-id="a9d7b-104">控制項會顯示行事曆： 包含編號的日期的月份，在底下的反白顯示的日期選取範圍的每週天數的資料行中排列方格。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-104">The control displays a calendar: a grid containing the numbered days of the month, arranged in columns underneath the days of the week, with the selected range of dates highlighted.</span></span> <span data-ttu-id="a9d7b-105">您可以透過按一下月份標題的任一邊的箭號按鈕選取不同的月份。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-105">You can select a different month by clicking the arrow buttons on either side of the month caption.</span></span> <span data-ttu-id="a9d7b-106">不同於類似<xref:System.Windows.Forms.DateTimePicker>控制項，您可以選取多個與這個控制項的日期。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-106">Unlike the similar <xref:System.Windows.Forms.DateTimePicker> control, you can select more than one date with this control.</span></span> <span data-ttu-id="a9d7b-107">如需有關<xref:System.Windows.Forms.DateTimePicker>控制，請參閱[DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-107">For more information about the <xref:System.Windows.Forms.DateTimePicker> control, see [DateTimePicker Control](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md).</span></span>  
  
## <a name="configuring-the-monthcalendar-control"></a><span data-ttu-id="a9d7b-108">設定的 MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="a9d7b-108">Configuring the MonthCalendar Control</span></span>  
 <span data-ttu-id="a9d7b-109"><xref:System.Windows.Forms.MonthCalendar>控制項的外觀會高度設定的基礎。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-109">The <xref:System.Windows.Forms.MonthCalendar> control's appearance is highly configurable.</span></span> <span data-ttu-id="a9d7b-110">根據預設，今天的日期會顯示為圈選起來，而且也會註明在方格的底部。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-110">By default, today's date is displayed as circled, and is also noted at the bottom of the grid.</span></span> <span data-ttu-id="a9d7b-111">您可以變更這項功能，藉由設定<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>和<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-111">You can change this feature by setting the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> and <xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A> properties to `false`.</span></span> <span data-ttu-id="a9d7b-112">您也可以加入至行事曆週數，方法是設定<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-112">You can also add week numbers to the calendar by setting the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="a9d7b-113">藉由設定<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>屬性，您可以有多個顯示月份的水平或垂直。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-113">By setting the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property, you can have multiple months displayed horizontally and vertically.</span></span> <span data-ttu-id="a9d7b-114">根據預設，星期日會顯示為每週的第一天，但您可使用指定任何一天<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-114">By default, Sunday is shown as the first day of the week, but any day can be designated using the <xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A> property.</span></span>  
  
 <span data-ttu-id="a9d7b-115">您也可以設定顯示在特定日期一次，每年，或每月粗體加<xref:System.DateTime>物件加入至<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>，和<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-115">You can also set certain dates to be displayed in bold on a one-time basis, annually, or monthly, by adding <xref:System.DateTime> objects to the <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>, and <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> properties.</span></span> <span data-ttu-id="a9d7b-116">如需詳細資訊，請參閱[How to： 在 Windows Form MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-116">For more information, see [How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md).</span></span>  
  
 <span data-ttu-id="a9d7b-117">索引鍵內容<xref:System.Windows.Forms.MonthCalendar>控制項是<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>，控制項中選取日期範圍。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-117">The key property of the <xref:System.Windows.Forms.MonthCalendar> control is <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>, the range of dates selected in the control.</span></span> <span data-ttu-id="a9d7b-118"><xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>值不能超過可選取、 在 設定最大天數<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-118">The <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> value cannot exceed the maximum number of days that can be selected, set in the <xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A> property.</span></span> <span data-ttu-id="a9d7b-119">使用者可以選取的最早和最新日期由<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>和<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a9d7b-119">The earliest and latest dates the user can select are determined by the <xref:System.Windows.Forms.MonthCalendar.MaxDate%2A> and <xref:System.Windows.Forms.MonthCalendar.MinDate%2A> properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d7b-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9d7b-120">See Also</span></span>  
 <xref:System.Windows.Forms.MonthCalendar>  
 [<span data-ttu-id="a9d7b-121">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="a9d7b-121">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
