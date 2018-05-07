---
title: 如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期
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
ms.openlocfilehash: 0ee89fb4cfb6ddbf975eb0e85e7dd1bab30f08d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可以顯示天以粗體為單數日期或重複的基礎。 您可能會執行這特別的日期，例如假日和週末的強調。  
  
 三個屬性會控制這項功能。 <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>屬性包含單一日期。 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>屬性包含以粗體顯示每年的日期。 <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>屬性包含每個月會以粗體顯示的日期。 每個屬性包含的陣列<xref:System.DateTime>物件。 若要新增或移除其中一個清單的日期，您必須新增或移除<xref:System.DateTime>物件。  
  
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
  
2.  藉由呼叫，讓單一日期變成粗體<xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>方法<xref:System.Windows.Forms.MonthCalendar>控制項。  
  
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
  
     將一組日期變成粗體一次所建立的陣列<xref:System.DateTime>物件並將其指派給其中一個屬性。  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>以一般字型顯示日期  
  
1.  藉由呼叫一般字型顯示單一的粗體日期<xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>方法。  
  
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
  
     從其中一個三個清單中移除所有的粗體日期，藉由呼叫<xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>方法。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  呼叫來更新之字型的外觀<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>方法。  
  
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
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [操作說明：變更 Windows Forms MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
