---
title: "如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍 | Microsoft Docs"
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
  - "行事曆, 選取日期範圍"
  - "日期, 選取 Calendar 控制項中的範圍"
  - "範例 [Windows Form], Calendar 控制項"
  - "MonthCalendar 控制項 [Windows Form], 選取日期範圍"
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍
Windows Form <xref:System.Windows.Forms.MonthCalendar> 控制項的其中一項重要功能是，使用者可以選取日期範圍。  這項功能是從 <xref:System.Windows.Forms.DateTimePicker> 控制項的日期選取功能改進而來，原來的功能只能讓使用者選取單一的日期\/時間值。  您可以使用 <xref:System.Windows.Forms.MonthCalendar> 控制項的屬性來設定日期範圍或取得使用者所設定的選取範圍。  下列程式碼範例會示範如何設定選取範圍。  
  
### 若要選取日期範圍  
  
1.  建立用來表示範圍中第一個及最後一個日期的 <xref:System.DateTime> 物件。  
  
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
  
2.  設定 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 屬性。  
  
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
  
     \- 或 \-  
  
     設定 <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> 和 <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> 屬性。  
  
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
  
## 請參閱  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [如何：變更 Windows Form MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)   
 [如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)   
 [如何：在 Windows Form MonthCalendar 控制項中顯示多個月份](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)