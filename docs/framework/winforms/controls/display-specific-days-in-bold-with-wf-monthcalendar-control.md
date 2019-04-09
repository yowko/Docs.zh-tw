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
ms.openlocfilehash: cf3ec21aa0272f60599f5659d78214120bcfcaf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073692"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>HOW TO：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示天以粗體為單數的日期或重複的基礎。 您可以這樣做來強調特殊的日期，例如假日和週末。  
  
 三個屬性會控制這項功能。 <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>屬性包含單一的日期。 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>屬性包含會以粗體顯示每年的日期。 <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性包含每個月會以粗體顯示的日期。 每個屬性包含陣列<xref:System.DateTime>物件。 若要新增或移除其中一份清單的日期，您必須新增或移除<xref:System.DateTime>物件。  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>若要以粗體類型顯示日期  
  
1.  建立<xref:System.DateTime>物件。  
  
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
  
2.  藉由呼叫，將單一日期變成粗體<xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>方法<xref:System.Windows.Forms.MonthCalendar>控制項。  
  
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
  
     將一組日期變成粗體全部一次所建立的陣列<xref:System.DateTime>物件並將它指派給其中一個屬性。  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>要以一般字型顯示日期  
  
1.  顯示一般字型，藉由呼叫單一的粗體日期<xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>方法。  
  
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
  
     從其中三個清單中移除所有的粗體日期，藉由呼叫<xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>方法。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  透過呼叫更新字型外表<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>方法。  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>另請參閱

- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
- [HOW TO：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [HOW TO：變更 Windows Forms MonthCalendar 控制項的外觀](how-to-change-monthcalendar-control-appearance.md)
- [HOW TO：在 Windows Forms MonthCalendar 控制項中顯示多個月份](display-more-than-one-month-wf-monthcalendar-control.md)
