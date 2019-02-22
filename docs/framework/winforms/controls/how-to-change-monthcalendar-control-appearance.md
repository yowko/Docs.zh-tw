---
title: HOW TO：變更 Windows Form MonthCalendar 控制項的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: f182a65a74507411f2474aca294c479e3b2b9ca6
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584040"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>HOW TO：變更 Windows Form MonthCalendar 控制項的外觀
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可讓您自訂在許多方面的行事曆的外觀。 例如，您可以設定色彩配置，以及選擇要顯示或隱藏週數和目前的日期。  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>若要變更的月份行事曆的色彩配置  
  
-   設定屬性，例如<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>，<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>和<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>屬性也會決定的字型色彩的一周天數。 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性決定的日期，優先於並遵循顯示的月或幾個月的色彩。  
  
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
    >  開始隨著 Windows Vista，以及每種佈景主題，設定某些屬性可能不會變更行事曆的外觀。 例如，如果 Windows 已設定為使用 Aero 佈景主題，設定<xref:System.Windows.Forms.MonthCalendar.BackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>，或<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性沒有任何作用。 這是因為使用衍生自目前的作業系統主題在執行階段外觀呈現行事曆的更新的版本。 如果您想要使用這些屬性，並啟用舊版的行事曆，您可以停用您的應用程式視覺化樣式。 停用視覺化樣式，可能會影響的外觀和行為的應用程式中其他控制項。 若要停用視覺化樣式，在 Visual Basic 中的，開啟 專案設計工具，並取消核取**啟用 XP 視覺化樣式**核取方塊。 若要停用 C# 中的視覺化樣式，請開啟 Program.cs，並標記為註解`Application.EnableVisualStyles();`。 如需視覺化樣式的詳細資訊，請參閱[啟用視覺化樣式](/windows/desktop/controls/cookbook-overview)。  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>若要在控制項底部顯示目前的日期  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設定為 `true`。 下列範例將顯示和省略表單時按兩下今天的日期之間切換。  
  
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
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>若要顯示週數  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設定為 `true`。 在程式碼中或在 [屬性] 視窗中，您可以設定這個屬性。  
  
     週數字會出現在個別的資料行左邊的一週的第一天。  
  
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
- [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [如何：在 Windows Form MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [如何：粗體的顯示特定日期中的使用 Windows Form MonthCalendar 控制項](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [如何：在 Windows Form MonthCalendar 控制項中顯示超過一個月](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
