---
title: "如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期"
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
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18a199592a8bfbef2e4a15b056e37af6d885f5f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="3a138-102">如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期</span><span class="sxs-lookup"><span data-stu-id="3a138-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="3a138-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示天以粗體為單數日期或重複的基礎。</span><span class="sxs-lookup"><span data-stu-id="3a138-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="3a138-104">您可能會執行這特別的日期，例如假日和週末的強調。</span><span class="sxs-lookup"><span data-stu-id="3a138-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="3a138-105">三個屬性會控制這項功能。</span><span class="sxs-lookup"><span data-stu-id="3a138-105">Three properties control this feature.</span></span> <span data-ttu-id="3a138-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>屬性包含單一日期。</span><span class="sxs-lookup"><span data-stu-id="3a138-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="3a138-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>屬性包含以粗體顯示每年的日期。</span><span class="sxs-lookup"><span data-stu-id="3a138-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="3a138-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性包含每個月會以粗體顯示的日期。</span><span class="sxs-lookup"><span data-stu-id="3a138-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="3a138-109">每個屬性包含的陣列<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="3a138-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="3a138-110">若要新增或移除其中一個清單的日期，您必須新增或移除<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="3a138-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="3a138-111">若要以粗體類型顯示日期</span><span class="sxs-lookup"><span data-stu-id="3a138-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="3a138-112">建立<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="3a138-112">Create the <xref:System.DateTime> objects.</span></span>  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2.  <span data-ttu-id="3a138-113">藉由呼叫，讓單一日期變成粗體<xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>方法<xref:System.Windows.Forms.MonthCalendar>控制項。</span><span class="sxs-lookup"><span data-stu-id="3a138-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     <span data-ttu-id="3a138-114">-或-</span><span class="sxs-lookup"><span data-stu-id="3a138-114">–or–</span></span>  
  
     <span data-ttu-id="3a138-115">將一組日期變成粗體一次所建立的陣列<xref:System.DateTime>物件並將其指派給其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="3a138-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="3a138-116">以一般字型顯示日期</span><span class="sxs-lookup"><span data-stu-id="3a138-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="3a138-117">藉由呼叫一般字型顯示單一的粗體日期<xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3a138-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     <span data-ttu-id="3a138-118">-或-</span><span class="sxs-lookup"><span data-stu-id="3a138-118">–or–</span></span>  
  
     <span data-ttu-id="3a138-119">從其中一個三個清單中移除所有的粗體日期，藉由呼叫<xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3a138-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="3a138-120">呼叫來更新之字型的外觀<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3a138-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3a138-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a138-121">See Also</span></span>  
 [<span data-ttu-id="3a138-122">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="3a138-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="3a138-123">操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="3a138-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="3a138-124">操作說明：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="3a138-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="3a138-125">操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="3a138-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
