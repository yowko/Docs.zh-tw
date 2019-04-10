---
title: HOW TO：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期
ms.date: 03/30/2017
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
ms.openlocfilehash: 27b19e47d108b9af43a6d8882264d62c726ffe56
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343258"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="50b8f-102">HOW TO：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期</span><span class="sxs-lookup"><span data-stu-id="50b8f-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="50b8f-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示天以粗體為單數的日期或重複的基礎。</span><span class="sxs-lookup"><span data-stu-id="50b8f-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="50b8f-104">您可以這樣做來強調特殊的日期，例如假日和週末。</span><span class="sxs-lookup"><span data-stu-id="50b8f-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="50b8f-105">三個屬性會控制這項功能。</span><span class="sxs-lookup"><span data-stu-id="50b8f-105">Three properties control this feature.</span></span> <span data-ttu-id="50b8f-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>屬性包含單一的日期。</span><span class="sxs-lookup"><span data-stu-id="50b8f-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="50b8f-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>屬性包含會以粗體顯示每年的日期。</span><span class="sxs-lookup"><span data-stu-id="50b8f-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="50b8f-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性包含每個月會以粗體顯示的日期。</span><span class="sxs-lookup"><span data-stu-id="50b8f-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="50b8f-109">每個屬性包含陣列<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="50b8f-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="50b8f-110">若要新增或移除其中一份清單的日期，您必須新增或移除<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="50b8f-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="50b8f-111">若要以粗體類型顯示日期</span><span class="sxs-lookup"><span data-stu-id="50b8f-111">To make a date appear in bold type</span></span>  
  
1. <span data-ttu-id="50b8f-112">建立<xref:System.DateTime>物件。</span><span class="sxs-lookup"><span data-stu-id="50b8f-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2. <span data-ttu-id="50b8f-113">藉由呼叫，將單一日期變成粗體<xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>方法<xref:System.Windows.Forms.MonthCalendar>控制項。</span><span class="sxs-lookup"><span data-stu-id="50b8f-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="50b8f-114">-或-</span><span class="sxs-lookup"><span data-stu-id="50b8f-114">–or–</span></span>  
  
     <span data-ttu-id="50b8f-115">將一組日期變成粗體全部一次所建立的陣列<xref:System.DateTime>物件並將它指派給其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="50b8f-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="50b8f-116">要以一般字型顯示日期</span><span class="sxs-lookup"><span data-stu-id="50b8f-116">To make a date appear in the regular font</span></span>  
  
1. <span data-ttu-id="50b8f-117">顯示一般字型，藉由呼叫單一的粗體日期<xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="50b8f-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="50b8f-118">-或-</span><span class="sxs-lookup"><span data-stu-id="50b8f-118">–or–</span></span>  
  
     <span data-ttu-id="50b8f-119">從其中三個清單中移除所有的粗體日期，藉由呼叫<xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="50b8f-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. <span data-ttu-id="50b8f-120">透過呼叫更新字型外表<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="50b8f-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="50b8f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50b8f-121">See also</span></span>

- [<span data-ttu-id="50b8f-122">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="50b8f-122">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="50b8f-123">HOW TO：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="50b8f-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="50b8f-124">HOW TO：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="50b8f-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="50b8f-125">HOW TO：在 Windows Forms MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="50b8f-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
