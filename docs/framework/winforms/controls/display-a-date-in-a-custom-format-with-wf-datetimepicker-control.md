---
title: "如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期"
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
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5f5c7d856991ae8e0bf7caff656bf7010255628
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期
Windows Form<xref:System.Windows.Forms.DateTimePicker>控制項可讓您格式化的日期和時間在控制項中的顯示的彈性。 <xref:System.Windows.Forms.DateTimePicker.Format%2A>屬性可讓您從預先定義的格式，清單中選取<xref:System.Windows.Forms.DateTimePickerFormat>。 其中一個項目是否適合您的目的，您可以建立您自己使用中所列的格式字元的格式樣式<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>。  
  
### <a name="to-display-a-custom-format"></a>若要顯示的自訂格式  
  
1.  將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 `DateTimePickerFormat.Custom`。  
  
2.  設定<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>屬性設為格式字串。  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>將文字加入格式化的值  
  
1.  使用單引號來括住格式字元，例如"M"或類似的分隔符號不是任何字元":"。 例如，下列的格式字串會顯示目前的日期格式 」 現在是： 05:30:31 星期五 2012 年 3 月 02，「 英文 （美國） 文化特性。  
  
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
  
     根據文化特性設定，可能會變更任何不在單引號中的字元。 例如，上述的格式字串會顯示目前的日期格式 」 現在： 05:30:31 星期五 2012 年 3 月 02，「 英文 （美國） 文化特性。 請注意第一個冒號會括在單引號中，因為它不是分隔字元，因為它是"ss"。 另一個文化特性中，格式可能會顯示為 「 目前是： 05.30.31 2012 年 3 月 02 日星期五"。  
  
## <a name="see-also"></a>請參閱  
 [DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [操作說明：使用 Windows Forms DateTimePicker 控制項設定和傳回日期](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
