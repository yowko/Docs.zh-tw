---
title: "如何：在 Windows Form MonthCalendar 控制項中顯示多個月份 | Microsoft Docs"
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
  - "行事曆, 格式化顯示"
  - "行事曆, 多月"
  - "範例 [Windows Form], Calendar 控制項"
  - "MonthCalendar 控制項 [Windows Form], 格式化顯示"
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：在 Windows Form MonthCalendar 控制項中顯示多個月份
Windows Form <xref:System.Windows.Forms.MonthCalendar> 控制項一次最多能夠顯示十二個月份。  控制項依預設只顯示一個月，但您可以指定顯示幾個月份，也可以指定要如何在控制項內排列這些月份。  當您變更月曆大小 \(Dimension\) 時，控制項會重新調整大小，因此請確定表單上有足夠的空間容納新的大小。  
  
### 若要顯示多個月份  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> 屬性設定為要水平和垂直顯示的月數。  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## 請參閱  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [如何：變更 Windows Form MonthCalendar 控制項的外觀](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)