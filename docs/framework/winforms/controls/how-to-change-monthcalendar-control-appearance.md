---
title: HOW TO：變更 Windows Forms MonthCalendar 控制項的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 9bd44a2d1f0db2652280e4875659c17916b033a6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612141"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="ce6e3-102">HOW TO：變更 Windows Forms MonthCalendar 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="ce6e3-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="ce6e3-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可讓您自訂在許多方面的行事曆的外觀。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="ce6e3-104">例如，您可以設定色彩配置，以及選擇要顯示或隱藏週數和目前的日期。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="ce6e3-105">若要變更的月份行事曆的色彩配置</span><span class="sxs-lookup"><span data-stu-id="ce6e3-105">To change the month calendar's color scheme</span></span>  
  
- <span data-ttu-id="ce6e3-106">設定屬性，例如<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>，<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>和<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="ce6e3-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>屬性也會決定的字型色彩的一周天數。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="ce6e3-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性決定的日期，優先於並遵循顯示的月或幾個月的色彩。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    >  <span data-ttu-id="ce6e3-109">開始隨著 Windows Vista，以及每種佈景主題，設定某些屬性可能不會變更行事曆的外觀。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="ce6e3-110">例如，如果 Windows 已設定為使用 Aero 佈景主題，設定<xref:System.Windows.Forms.MonthCalendar.BackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>，或<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="ce6e3-111">這是因為使用衍生自目前的作業系統主題在執行階段外觀呈現行事曆的更新的版本。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="ce6e3-112">如果您想要使用這些屬性，並啟用舊版的行事曆，您可以停用您的應用程式視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="ce6e3-113">停用視覺化樣式，可能會影響的外觀和行為的應用程式中其他控制項。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="ce6e3-114">若要停用視覺化樣式，在 Visual Basic 中的，開啟 專案設計工具，並取消核取**啟用 XP 視覺化樣式**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="ce6e3-115">若要停用 C# 中的視覺化樣式，請開啟 Program.cs，並標記為註解`Application.EnableVisualStyles();`。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="ce6e3-116">如需視覺化樣式的詳細資訊，請參閱[啟用視覺化樣式](/windows/desktop/controls/cookbook-overview)。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="ce6e3-117">若要在控制項底部顯示目前的日期</span><span class="sxs-lookup"><span data-stu-id="ce6e3-117">To display the current date at the bottom of the control</span></span>  
  
- <span data-ttu-id="ce6e3-118">將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="ce6e3-119">下列範例將顯示和省略表單時按兩下今天的日期之間切換。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="ce6e3-120">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="ce6e3-121">若要顯示週數</span><span class="sxs-lookup"><span data-stu-id="ce6e3-121">To display week numbers</span></span>  
  
- <span data-ttu-id="ce6e3-122">將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="ce6e3-123">在程式碼中或在 [屬性] 視窗中，您可以設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="ce6e3-124">週數字會出現在個別的資料行左邊的一週的第一天。</span><span class="sxs-lookup"><span data-stu-id="ce6e3-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce6e3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce6e3-125">See also</span></span>

- [<span data-ttu-id="ce6e3-126">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="ce6e3-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="ce6e3-127">如何：在 Windows Form MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="ce6e3-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="ce6e3-128">如何：粗體的顯示特定日期中的使用 Windows Form MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="ce6e3-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="ce6e3-129">如何：在 Windows Form MonthCalendar 控制項中顯示超過一個月</span><span class="sxs-lookup"><span data-stu-id="ce6e3-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
