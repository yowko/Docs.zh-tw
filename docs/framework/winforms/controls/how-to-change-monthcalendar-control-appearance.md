---
title: 作法：變更 Windows Forms MonthCalendar 控制項的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 5582624d881b2d8039bcd5e8ac45e548c7b38f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929040"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>作法：變更 Windows Forms MonthCalendar 控制項的外觀
Windows Forms <xref:System.Windows.Forms.MonthCalendar>控制項可讓您以許多方式來自訂行事曆的外觀。 例如, 您可以設定色彩配置, 並選擇顯示或隱藏周數和目前日期。  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>變更月曆的色彩配置  
  
- 設定屬性<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, 例如、 <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>和<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>屬性也會決定星期幾的字型色彩。 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性會決定在顯示的月份或月份之前和之後的日期色彩。  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    > 從 Windows Vista 開始, 視主題而定, 設定某些屬性可能不會變更行事曆的外觀。 例如, 如果 Windows 設定為使用 Aero <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>主題, 則設定、 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、 <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>或<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性不會有任何作用。 這是因為已更新的行事曆版本會呈現在執行時間從目前作業系統主題衍生的外觀。 如果您想要使用這些屬性並啟用舊版行事曆, 您可以停用應用程式的視覺化樣式。 停用視覺化樣式可能會影響應用程式中其他控制項的外觀和行為。 若要在 Visual Basic 中停用視覺化樣式, 請開啟 [專案設計工具], 然後取消選取 [**啟用 XP 視覺化樣式**] 核取方塊。 若要在中停C#用視覺化樣式, 請開啟`Application.EnableVisualStyles();`Program.cs 並將其批註。 如需視覺化樣式的詳細資訊, 請參閱[啟用視覺化樣式](/windows/desktop/controls/cookbook-overview)。  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>若要在控制項底部顯示目前的日期  
  
- 將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設定為 `true`。 下列範例會在按兩下表單時, 切換顯示和省略今天的日期。  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>若要顯示周數  
  
- 將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設定為 `true`。 您可以在程式碼或屬性視窗中設定此屬性。  
  
     周數會出現在一周第一天左邊的個別資料行中。  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>另請參閱

- [MonthCalendar 控制項](monthcalendar-control-windows-forms.md)
- [如何：在 Windows Forms MonthCalendar 控制項中選取日期範圍](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [如何：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [如何：在 Windows Forms MonthCalendar 控制項中顯示一個以上的月份](display-more-than-one-month-wf-monthcalendar-control.md)
