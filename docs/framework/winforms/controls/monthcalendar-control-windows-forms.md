---
title: "MonthCalendar 控制項 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar controls
- MonthCalendar control [Windows Forms]
- dates [Windows Forms], controls
- calendars
ms.assetid: 051c6518-e0ca-426b-855c-f9bf70972970
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4823b7d7411b7896e723683b70021292dd989aa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="monthcalendar-control-windows-forms"></a><span data-ttu-id="8a44a-102">MonthCalendar 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="8a44a-102">MonthCalendar Control (Windows Forms)</span></span>
<span data-ttu-id="8a44a-103">Windows Form`MonthCalendar`控制項提供直覺式的圖形化介面，以便讓使用者檢視並設定日期資訊。</span><span class="sxs-lookup"><span data-stu-id="8a44a-103">The Windows Forms `MonthCalendar` control presents an intuitive graphical interface for users to view and set date information.</span></span> <span data-ttu-id="8a44a-104">控制項會顯示包含編號的日期的月份，在下一周天數的資料行中排列方格。</span><span class="sxs-lookup"><span data-stu-id="8a44a-104">The control displays a grid containing the numbered days of the month, arranged in columns underneath the days of the week.</span></span> <span data-ttu-id="8a44a-105">您可以透過按一下月份標題的任一邊的箭號按鈕選取不同的月份。</span><span class="sxs-lookup"><span data-stu-id="8a44a-105">You can select a different month by clicking the arrow buttons on either side of the month caption.</span></span> <span data-ttu-id="8a44a-106">不同於類似<xref:System.Windows.Forms.DateTimePicker>控制項，您可以選取範圍的日期與此控制項; 不過，<xref:System.Windows.Forms.DateTimePicker>控制項可讓您設定的時間以及日期。</span><span class="sxs-lookup"><span data-stu-id="8a44a-106">Unlike the similar <xref:System.Windows.Forms.DateTimePicker> control, you can select a range of dates with this control; however, the <xref:System.Windows.Forms.DateTimePicker> control allows you to set times as well as dates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a44a-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="8a44a-107">In This Section</span></span>  
 [<span data-ttu-id="8a44a-108">MonthCalendar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="8a44a-108">MonthCalendar Control Overview</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md)  
 <span data-ttu-id="8a44a-109">導入的一般概念`MonthCalendar`控制項，可讓使用者檢視和設定應用程式的日期資訊。</span><span class="sxs-lookup"><span data-stu-id="8a44a-109">Introduces the general concepts of the `MonthCalendar` control, which allows users to view and set date information for an application.</span></span>  
  
 [<span data-ttu-id="8a44a-110">操作說明：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="8a44a-110">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 <span data-ttu-id="8a44a-111">描述如何自訂的外觀`MonthCalendar`控制項。</span><span class="sxs-lookup"><span data-stu-id="8a44a-111">Describes how to customize the appearance of the `MonthCalendar` control.</span></span>  
  
 [<span data-ttu-id="8a44a-112">操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="8a44a-112">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)  
 <span data-ttu-id="8a44a-113">描述如何設定`MonthCalendar`控制項來顯示幾個月同時。</span><span class="sxs-lookup"><span data-stu-id="8a44a-113">Describes how to configure the `MonthCalendar` control to display several months simultaneously.</span></span>  
  
 [<span data-ttu-id="8a44a-114">操作說明：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期</span><span class="sxs-lookup"><span data-stu-id="8a44a-114">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 <span data-ttu-id="8a44a-115">說明如何設定特定的日期，以顯示為粗體。</span><span class="sxs-lookup"><span data-stu-id="8a44a-115">Explains how to set certain dates to appear bold.</span></span>  
  
 [<span data-ttu-id="8a44a-116">操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="8a44a-116">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 <span data-ttu-id="8a44a-117">說明如何以程式設計方式選取的日期範圍`MonthCalendar`控制項。</span><span class="sxs-lookup"><span data-stu-id="8a44a-117">Explains how to programmatically select a range of dates from the `MonthCalendar` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8a44a-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="8a44a-118">Reference</span></span>  
 <xref:System.Windows.Forms.MonthCalendar>  
 <span data-ttu-id="8a44a-119">提供這個類別及其成員的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="8a44a-119">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8a44a-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="8a44a-120">Related Sections</span></span>  
 [<span data-ttu-id="8a44a-121">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="8a44a-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="8a44a-122">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="8a44a-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="8a44a-123">DateTimePicker 控制項</span><span class="sxs-lookup"><span data-stu-id="8a44a-123">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 <span data-ttu-id="8a44a-124">描述類似的控制項<xref:System.Windows.Forms.MonthCalendar>，不過<xref:System.Windows.Forms.DateTimePicker>控制項也可讓您選取的時間，且不允許您選取的日期範圍。</span><span class="sxs-lookup"><span data-stu-id="8a44a-124">Describes a control similar to <xref:System.Windows.Forms.MonthCalendar>, although the <xref:System.Windows.Forms.DateTimePicker> control also allows you to select a time and does not allow you to select a range of dates.</span></span>
