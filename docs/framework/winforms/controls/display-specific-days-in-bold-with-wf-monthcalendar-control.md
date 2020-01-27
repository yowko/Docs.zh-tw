---
title: 使用 MonthCalendar 控制項以粗體顯示特定日期
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
ms.openlocfilehash: 377eb76f562fff20aae2136ddb7130516d2d76f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745890"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期
Windows Forms <xref:System.Windows.Forms.MonthCalendar> 控制項可以將日期顯示為粗體類型，不論是以單數日期或重複的方式來表示。 您可能會這麼做，以特別注意假日和週末之類的特殊日期。  
  
 有三個屬性會控制這項功能。 <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> 屬性包含單一日期。 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> 屬性包含每年以粗體顯示的日期。 <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> 屬性包含每個月以粗體顯示的日期。 其中每個屬性都包含 <xref:System.DateTime> 物件的陣列。 若要加入或移除其中一個清單中的日期，您必須加入或移除 <xref:System.DateTime> 物件。  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>若要讓日期顯示為粗體類型  
  
1. 建立 <xref:System.DateTime> 物件。  
  
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
  
2. 藉由呼叫 <xref:System.Windows.Forms.MonthCalendar> 控制項的 <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>、<xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>或 <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> 方法，讓單一日期變成粗體。  
  
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
  
     -或-  
  
     建立 <xref:System.DateTime> 物件的陣列，並將其指派給其中一個屬性，以一次將一組日期全部以粗體顯示。  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>若要讓日期以一般字型顯示  
  
1. 藉由呼叫 <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>、<xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>或 <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> 方法，讓單一的粗體日期顯示為一般字型。  
  
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
  
     -或-  
  
     藉由呼叫 <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>、<xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>或 <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> 方法，從三個清單的其中一個移除所有粗體的日期。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. 藉由呼叫 <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> 方法來更新字型的外觀。  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>請參閱

- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
- [操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [操作說明：變更 Windows Forms MonthCalendar 控制項的外觀](how-to-change-monthcalendar-control-appearance.md)
- [操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份](display-more-than-one-month-wf-monthcalendar-control.md)
