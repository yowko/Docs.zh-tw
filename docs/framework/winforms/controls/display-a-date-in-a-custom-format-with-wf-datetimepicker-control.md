---
title: "如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期 | Microsoft Docs"
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
  - "日期, 在 DateTimePicker 控制項中顯示"
  - "DateTimePicker 控制項 [Windows Form], 顯示樣式"
  - "範例 [Windows Form], DateTimePicker 控制項"
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期
Windows Form <xref:System.Windows.Forms.DateTimePicker> 控制項在格式化控制項中的日期和時間顯示方面，提供了彈性。  <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性允許您選取列於 <xref:System.Windows.Forms.DateTimePickerFormat> 的預先定義格式。  如果這些都不符合您的需求，您可以使用列在 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 中的格式字元來建立您自己的格式樣式。  
  
### 若要顯示自訂格式  
  
1.  將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 `DateTimePickerFormat.Custom`。  
  
2.  將 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 屬性設定為格式字串 \(Format String\)。  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### 若要加入文字至格式值  
  
1.  使用單引號將不是格式字元 \(例如 "M"\) 或分隔符號 \(Delimiter\) \(例如 ":"\) 的任何字元括起來。  例如，以下的格式字串顯示目前日期，格式為英文 \(美國\) 文化特性的 "Today is: 05:30:31 Friday March 02, 2012"。  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     根據文化設定而定，可變更任何不在單引號中的字元。  例如，以上的格式字串會顯示目前日期，格式為英文 \(美國\) 文化特性的「Today is: 05:30:31 Friday March 02, 2012」。  請注意，第一個冒號是包含在單引號中，因為它不是用來當做如同在 "hh:mm:ss" 中的分隔字元。  在其他文化特性中，格式就可能是 "Today is: 05.30.31 Friday March 02, 2012"。  
  
## 請參閱  
 [DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)   
 [如何：使用 Windows Form DateTimePicker 控制項設定和傳回日期](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)