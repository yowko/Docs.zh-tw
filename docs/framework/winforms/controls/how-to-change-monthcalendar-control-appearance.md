---
title: "如何： 變更 Windows Form MonthCalendar 控制項 &#39; s 外觀"
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
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89aa2d57e7990bb2b0016fa4936cf1487578db01
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>如何： 變更 Windows Form MonthCalendar 控制項 &#39; s 外觀
Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可讓您自訂在許多方面的行事曆的外觀。 例如，您可以設定色彩配置，以及選擇要顯示或隱藏週數和目前的日期。  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>若要變更月曆的色彩配置  
  
-   設定屬性，例如<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>，<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>和<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>屬性也會決定的字型色彩的每週天數。 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性會決定日期前後的前面顯示的月或月份的色彩。  
  
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
    >  從開始使用 Windows Vista，並根據佈景主題，設定某些屬性可能不會變更行事曆外觀。 例如，如果 Windows 設定為使用 Aero 的佈景主題，設定<xref:System.Windows.Forms.MonthCalendar.BackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>，或<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性沒有任何作用。 這是因為在執行階段衍生自目前作業系統的佈景主題的外觀呈現行事曆的更新的版本。 如果您想要使用這些屬性並啟用行事曆的舊版，您可以停用您的應用程式視覺化樣式。 停用視覺化樣式，可能會影響的外觀和行為的應用程式中其他控制項。 若要停用在 Visual Basic 中的視覺化樣式，請開啟 專案設計工具並取消核取**啟用 XP 視覺化樣式**核取方塊。 若要停用 C# 中的視覺化樣式，請開啟 Program.cs 並標記為註解`Application.EnableVisualStyles();`。 如需視覺化樣式的詳細資訊，請參閱[How to： 啟用 Windows XP 視覺化樣式](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f)。  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>若要在控制項底部顯示目前的日期  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設定為 `true`。 下列範例將顯示和省略按兩下表單時的目前日期之間切換。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>若要顯示週數  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設定為 `true`。 在程式碼中或在 [屬性] 視窗中，您可以設定這個屬性。  
  
     週數會出現在個別的資料行左邊的一週的第一天。  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>請參閱  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [操作說明：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
