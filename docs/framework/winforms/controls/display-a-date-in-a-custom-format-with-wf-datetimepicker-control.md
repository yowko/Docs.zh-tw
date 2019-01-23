---
title: HOW TO：使用 Windows Form DateTimePicker 控制項的自訂格式來顯示日期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 489a31474b8ae3e56ba69e59f6d613ecf892a93c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531287"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>HOW TO：使用 Windows Form DateTimePicker 控制項的自訂格式來顯示日期
Windows Form<xref:System.Windows.Forms.DateTimePicker>控制項可讓您彈性地格式化日期和時間在控制項中的顯示。 <xref:System.Windows.Forms.DateTimePicker.Format%2A>屬性可讓您從預先定義的格式，在列出選取<xref:System.Windows.Forms.DateTimePickerFormat>。 其中一個項目是否適合您的目的，您可以建立您自己使用中所列的格式字元的格式樣式<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>。  
  
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
  
1.  使用單引號來括住的任何字元不是像"M"的格式字元或分隔符號，例如":"。 例如，下列的格式字串會顯示目前的日期格式 」 目前是：05:30:31 星期五年 3 月 02、 2012 「 英文 （美國） 文化特性中。  
  
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
  
     根據文化特性設定，可能會變更任何沒有單引號括住的字元。 例如，上述的格式字串會顯示目前的日期格式 」 目前是：05:30:31 星期五年 3 月 02、 2012 「 英文 （美國） 文化特性中。 請注意第一個冒號會括在單引號括住，因為它不是會分隔字元，因為它是"ss"。 在另一個文化特性的格式可能會顯示為 「 目前是：05.30.31 星期五年 3 月 02、 2012"。  
  
## <a name="see-also"></a>另請參閱
- [DateTimePicker 控制項](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
- [如何：使用 Windows Form DateTimePicker 控制項設定和傳回日期](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
