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
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="69eff-102">作法：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="69eff-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="69eff-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar>控制項可讓您以許多方式來自訂行事曆的外觀。</span><span class="sxs-lookup"><span data-stu-id="69eff-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="69eff-104">例如, 您可以設定色彩配置, 並選擇顯示或隱藏周數和目前日期。</span><span class="sxs-lookup"><span data-stu-id="69eff-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="69eff-105">變更月曆的色彩配置</span><span class="sxs-lookup"><span data-stu-id="69eff-105">To change the month calendar's color scheme</span></span>  
  
- <span data-ttu-id="69eff-106">設定屬性<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, 例如、 <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>和<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>。</span><span class="sxs-lookup"><span data-stu-id="69eff-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="69eff-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>屬性也會決定星期幾的字型色彩。</span><span class="sxs-lookup"><span data-stu-id="69eff-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="69eff-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性會決定在顯示的月份或月份之前和之後的日期色彩。</span><span class="sxs-lookup"><span data-stu-id="69eff-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    > <span data-ttu-id="69eff-109">從 Windows Vista 開始, 視主題而定, 設定某些屬性可能不會變更行事曆的外觀。</span><span class="sxs-lookup"><span data-stu-id="69eff-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="69eff-110">例如, 如果 Windows 設定為使用 Aero <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>主題, 則設定、 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、 <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>或<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="69eff-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="69eff-111">這是因為已更新的行事曆版本會呈現在執行時間從目前作業系統主題衍生的外觀。</span><span class="sxs-lookup"><span data-stu-id="69eff-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="69eff-112">如果您想要使用這些屬性並啟用舊版行事曆, 您可以停用應用程式的視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="69eff-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="69eff-113">停用視覺化樣式可能會影響應用程式中其他控制項的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="69eff-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="69eff-114">若要在 Visual Basic 中停用視覺化樣式, 請開啟 [專案設計工具], 然後取消選取 [**啟用 XP 視覺化樣式**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="69eff-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="69eff-115">若要在中停C#用視覺化樣式, 請開啟`Application.EnableVisualStyles();`Program.cs 並將其批註。</span><span class="sxs-lookup"><span data-stu-id="69eff-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="69eff-116">如需視覺化樣式的詳細資訊, 請參閱[啟用視覺化樣式](/windows/desktop/controls/cookbook-overview)。</span><span class="sxs-lookup"><span data-stu-id="69eff-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="69eff-117">若要在控制項底部顯示目前的日期</span><span class="sxs-lookup"><span data-stu-id="69eff-117">To display the current date at the bottom of the control</span></span>  
  
- <span data-ttu-id="69eff-118">將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="69eff-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="69eff-119">下列範例會在按兩下表單時, 切換顯示和省略今天的日期。</span><span class="sxs-lookup"><span data-stu-id="69eff-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="69eff-120">(視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="69eff-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="69eff-121">若要顯示周數</span><span class="sxs-lookup"><span data-stu-id="69eff-121">To display week numbers</span></span>  
  
- <span data-ttu-id="69eff-122">將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="69eff-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="69eff-123">您可以在程式碼或屬性視窗中設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="69eff-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="69eff-124">周數會出現在一周第一天左邊的個別資料行中。</span><span class="sxs-lookup"><span data-stu-id="69eff-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="69eff-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69eff-125">See also</span></span>

- [<span data-ttu-id="69eff-126">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="69eff-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="69eff-127">如何：在 Windows Forms MonthCalendar 控制項中選取日期範圍</span><span class="sxs-lookup"><span data-stu-id="69eff-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="69eff-128">如何：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期</span><span class="sxs-lookup"><span data-stu-id="69eff-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="69eff-129">如何：在 Windows Forms MonthCalendar 控制項中顯示一個以上的月份</span><span class="sxs-lookup"><span data-stu-id="69eff-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
