---
title: 如何： 變更 Windows Form MonthCalendar 控制項&#39;s 外觀
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d2a3f12368d5215f7fe7611aa2f06e6b0fb1192
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a><span data-ttu-id="8bca0-102">如何： 變更 Windows Form MonthCalendar 控制項&#39;s 外觀</span><span class="sxs-lookup"><span data-stu-id="8bca0-102">How to: Change the Windows Forms MonthCalendar Control&#39;s Appearance</span></span>
<span data-ttu-id="8bca0-103">Windows Form<xref:System.Windows.Forms.MonthCalendar>控制項可讓您自訂在許多方面的行事曆的外觀。</span><span class="sxs-lookup"><span data-stu-id="8bca0-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="8bca0-104">例如，您可以設定色彩配置，以及選擇要顯示或隱藏週數和目前的日期。</span><span class="sxs-lookup"><span data-stu-id="8bca0-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="8bca0-105">若要變更月曆的色彩配置</span><span class="sxs-lookup"><span data-stu-id="8bca0-105">To change the month calendar's color scheme</span></span>  
  
-   <span data-ttu-id="8bca0-106">設定屬性，例如<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>，<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>和<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>。</span><span class="sxs-lookup"><span data-stu-id="8bca0-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="8bca0-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>屬性也會決定的字型色彩的每週天數。</span><span class="sxs-lookup"><span data-stu-id="8bca0-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="8bca0-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性會決定日期前後的前面顯示的月或月份的色彩。</span><span class="sxs-lookup"><span data-stu-id="8bca0-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    >  <span data-ttu-id="8bca0-109">從開始使用 Windows Vista，並根據佈景主題，設定某些屬性可能不會變更行事曆外觀。</span><span class="sxs-lookup"><span data-stu-id="8bca0-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="8bca0-110">例如，如果 Windows 設定為使用 Aero 的佈景主題，設定<xref:System.Windows.Forms.MonthCalendar.BackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>， <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>，或<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>屬性沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="8bca0-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="8bca0-111">這是因為在執行階段衍生自目前作業系統的佈景主題的外觀呈現行事曆的更新的版本。</span><span class="sxs-lookup"><span data-stu-id="8bca0-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="8bca0-112">如果您想要使用這些屬性並啟用行事曆的舊版，您可以停用您的應用程式視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="8bca0-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="8bca0-113">停用視覺化樣式，可能會影響的外觀和行為的應用程式中其他控制項。</span><span class="sxs-lookup"><span data-stu-id="8bca0-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="8bca0-114">若要停用在 Visual Basic 中的視覺化樣式，請開啟 專案設計工具並取消核取**啟用 XP 視覺化樣式**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8bca0-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="8bca0-115">若要停用 C# 中的視覺化樣式，請開啟 Program.cs 並標記為註解`Application.EnableVisualStyles();`。</span><span class="sxs-lookup"><span data-stu-id="8bca0-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="8bca0-116">如需視覺化樣式的詳細資訊，請參閱[How to： 啟用 Windows XP 視覺化樣式](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f)。</span><span class="sxs-lookup"><span data-stu-id="8bca0-116">For more information about visual styles, see [How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="8bca0-117">若要在控制項底部顯示目前的日期</span><span class="sxs-lookup"><span data-stu-id="8bca0-117">To display the current date at the bottom of the control</span></span>  
  
-   <span data-ttu-id="8bca0-118">將 <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8bca0-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="8bca0-119">下列範例將顯示和省略按兩下表單時的目前日期之間切換。</span><span class="sxs-lookup"><span data-stu-id="8bca0-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="8bca0-120">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8bca0-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="8bca0-121">若要顯示週數</span><span class="sxs-lookup"><span data-stu-id="8bca0-121">To display week numbers</span></span>  
  
-   <span data-ttu-id="8bca0-122">將 <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="8bca0-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="8bca0-123">在程式碼中或在 [屬性] 視窗中，您可以設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="8bca0-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="8bca0-124">週數會出現在個別的資料行左邊的一週的第一天。</span><span class="sxs-lookup"><span data-stu-id="8bca0-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8bca0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bca0-125">See Also</span></span>  
 [<span data-ttu-id="8bca0-126">MonthCalendar 控制項</span><span class="sxs-lookup"><span data-stu-id="8bca0-126">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="8bca0-127">操作說明：在 Windows Forms 的 MonthCalendar 控制項中選取一個日期範圍</span><span class="sxs-lookup"><span data-stu-id="8bca0-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="8bca0-128">操作說明：使用 Windows Forms MonthCalendar 控制項以粗體顯示特定日期</span><span class="sxs-lookup"><span data-stu-id="8bca0-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="8bca0-129">操作說明：在 Windows Forms MonthCalendar 控制項中顯示多個月份</span><span class="sxs-lookup"><span data-stu-id="8bca0-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
