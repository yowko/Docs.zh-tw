---
title: "如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "行事曆, 以粗體字顯示日期"
  - "範例 [Windows Form], Calendar 控制項"
  - "GetDayBold 事件"
  - "MonthCalendar 控制項 [Windows Form], 以粗體字顯示的日期"
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期
Windows Form 的 <xref:System.Windows.Forms.MonthCalendar> 控制項能夠以粗體類型顯示日期，無論是顯示為單一日期或是數個日期皆可。  這麼做可以將注意力放在特別的日期上，例如假日和週末。  
  
 這個功能是由以下三個屬性控制。  <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> 屬性包含單一日期。  <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> 屬性包含每年以粗體顯示的日期。  <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> 屬性包含每月以粗體顯示的日期。  這些屬性都包含 <xref:System.DateTime> 物件的陣列。  若要從這些清單加入或移除日期，您必須加入或移除 <xref:System.DateTime> 物件。  
  
### 若要以粗體類型顯示日期  
  
1.  建立 <xref:System.DateTime> 物件。  
  
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
  
2.  呼叫 <xref:System.Windows.Forms.MonthCalendar> 控制項的 <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>、<xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A> 或 <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> 方法，以粗體顯示單一日期。  
  
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
  
     \- 或 \-  
  
     建立 <xref:System.DateTime> 物件的陣列並將任一屬性指派給它，一次將日期設為粗體。  
  
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
  
### 若要以標準字型顯示日期  
  
1.  呼叫 <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>、<xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A> 或 <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> 方法，將單一粗體日期以標準字型顯示。  
  
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
  
     \- 或 \-  
  
     呼叫 <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>、<xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A> 或 <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> 方法，從任一清單移除所有粗體日期。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  呼叫 <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> 方法來更新字型外觀。  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## 請參閱  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [如何：變更 Windows Form MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)   
 [如何：在 Windows Form MonthCalendar 控制項中顯示多個月份](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)