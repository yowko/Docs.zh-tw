---
title: "如何：變更 Windows Form MonthCalendar 控制項的外觀 | Microsoft Docs"
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
  - "範例 [Windows Form], Calendar 控制項"
  - "MonthBackColor 屬性"
  - "MonthCalendar 控制項 [Windows Form], 格式化顯示"
  - "TitleBackColor 屬性"
  - "TitleForeColor 屬性"
  - "TrailingForeColor 屬性"
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：變更 Windows Form MonthCalendar 控制項的外觀
Windows Form <xref:System.Windows.Forms.MonthCalendar> 控制項允許您以各種不同的方式自訂月曆的外觀。  例如，您可以設定色彩配置並選擇要顯示或隱藏週數和目前的日期。  
  
### 若要變更月曆的色彩配置  
  
-   設定 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> 和 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> 等屬性。  <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> 屬性也可決定星期天數的字型色彩。  <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> 屬性決定顯示月份之前和之後日期的色彩。  
  
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
    >  從 Windows Vista 開始，依據背景主題而定，設定部分屬性可能不會變更行事曆的外觀。  例如，如果 Windows 設定為使用 Aero 背景主題，則設定 <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> 或 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> 屬性不會有任何作用。  這是因為更新的行事曆版本會使用在執行階段從目前作業系統背景主題衍生的外觀呈現。  如果您想要使用這些屬性並且啟用舊版行事曆，可以停用應用程式的視覺化樣式。  停用視覺化樣式可能會影響應用程式中其他控制項的外觀和行為。  若要在 Visual Basic 中停用視覺化樣式，請開啟 \[專案設計工具\]，並且取消核取 \[**啟用 XP 視覺化樣式**\] 核取方塊。  若要在 C\# 中停用視覺化樣式，請開啟 \[Program.cs\]，並且註解 `Application.EnableVisualStyles();`。  如需視覺化樣式的詳細資訊，請參閱 [How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/zh-tw/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f)。  
  
### 若要在控制項下方顯示目前日期  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設為 `true`。  當按兩下表單時，以下範例將在顯示和省略今天日期之間切換。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### 若要顯示週數  
  
-   將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設為 `true`。  您可以用程式碼或在 \[屬性\] 視窗中設定這項屬性。  
  
     週數會顯示在每週第一天左方個別的行中。  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## 請參閱  
 [MonthCalendar 控制項](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [如何：在 Windows Form 的 MonthCalendar 控制項中選取一個日期範圍](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [如何：使用 Windows Form MonthCalendar 控制項以粗體顯示特定日期](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)   
 [如何：在 Windows Form MonthCalendar 控制項中顯示多個月份](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)