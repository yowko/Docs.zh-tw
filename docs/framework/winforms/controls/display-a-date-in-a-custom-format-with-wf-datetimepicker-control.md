---
title: 使用 DateTimePicker 控制項以自訂格式顯示日期
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
ms.openlocfilehash: a27dbe737b81af86c0ac50b791bcd87bafe05b4f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745941"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期
Windows Forms <xref:System.Windows.Forms.DateTimePicker> 控制項可讓您彈性地在控制項中格式化日期和時間的顯示。 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性可讓您從 <xref:System.Windows.Forms.DateTimePickerFormat>中所列的預先定義格式進行選取。 如果這些都不適合您的用途，您可以使用 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>中列出的格式字元來建立自己的格式樣式。  
  
### <a name="to-display-a-custom-format"></a>若要顯示自訂格式  
  
1. 將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設為 `DateTimePickerFormat.Custom`。  
  
2. 將 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 屬性設定為格式字串。  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>若要將文字加入至格式化的值  
  
1. 使用單引號來括住任何不是格式字元的字元，例如 "M" 或 "：" 之類的分隔符號。 例如，下面的格式字串會以英文（美國）文化特性的格式，顯示目前的日期，其格式為「今天是：05:30:31，2012年3月2日星期五」。  
  
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
  
     根據文化特性設定，未以單引號括住的任何字元可能會變更。 例如，上方的格式字串會以英文（美國）文化特性的格式顯示目前的日期，其格式為「今日為：05:30:31，2012年3月2日星期五」。 請注意，第一個冒號是以單引號括住，因為它不適合做為 "hh： mm： ss" 中的分隔字元。 在另一種文化特性中，格式可能會顯示為「今天是：05.30.31 星期五，2012」。  
  
## <a name="see-also"></a>另請參閱

- [DateTimePicker 控制項](datetimepicker-control-windows-forms.md)
- [操作說明：使用 Windows Forms DateTimePicker 控制項設定和傳回日期](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
