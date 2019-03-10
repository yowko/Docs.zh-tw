---
title: HOW TO：使用 Windows Form DateTimePicker 控制項設定和傳回日期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: 73c40a48a75955d1ba44decae6b50ca641a63f7b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703210"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>HOW TO：使用 Windows Form DateTimePicker 控制項設定和傳回日期
在 Windows Form <xref:System.Windows.Forms.DateTimePicker> 控制項中目前選取的日期或時間取決於 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性。 您可以在顯示控制項之前 (例如，在設計階段或在表單的 <xref:System.Windows.Forms.Form.Load> 事件) 設定 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性來判斷在控制項中一開始所選取的日期。 根據預設，此控制項的 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 設為目前的日期。 如果您在程式碼中變更控制項的 <xref:System.Windows.Forms.DateTimePicker.Value%2A>，控制項會在表單上自動更新以反映新的設定。  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性傳回 <xref:System.DateTime> 結構做為其值。 有幾個 <xref:System.DateTime> 結構的屬性會傳回所顯示日期的特定資訊。 這些屬性只可以用來傳回值；請勿使用這些來設定值。  
  
-   對於日期值，<xref:System.DateTime.Month%2A> <xref:System.DateTime.Day%2A>和 <xref:System.DateTime.Year%2A> 屬性會傳回所選取日期之時間單位的整數值。 <xref:System.DateTime.DayOfWeek%2A> 屬性會傳回值，表示所選取的是星期幾 (可能的值會列在 <xref:System.DayOfWeek> 列舉中)。  
  
-   對於時間值，<xref:System.DateTime.Hour%2A>、<xref:System.DateTime.Minute%2A>、<xref:System.DateTime.Second%2A> 和 <xref:System.DateTime.Millisecond%2A> 屬性會傳回時間單位的整數值。 若要設定控制項來顯示時間，請參閱[How to:使用 DateTimePicker 控制項顯示時間](how-to-display-time-with-the-datetimepicker-control.md)。  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>設定控制項的日期和時間值  
  
-   設定 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性為日期或時間值。  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>傳回日期和時間值  
  
-   呼叫 <xref:System.Windows.Forms.DateTimePicker.Text%2A> 屬性來傳回整個值為控制項中的格式，或呼叫 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性的適當方法，以傳回值的一部分。 使用 <xref:System.Windows.Forms.DateTimePicker.ToString%2A> 將資訊轉換成可以向使用者顯示的字串。  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a>另請參閱
- [DateTimePicker 控制項](datetimepicker-control-windows-forms.md)
- [如何：使用 Windows Form DateTimePicker 控制項的自訂格式來顯示日期](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
