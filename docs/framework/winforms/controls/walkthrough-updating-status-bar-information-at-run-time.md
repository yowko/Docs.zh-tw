---
title: 逐步解說：在執行階段更新狀態列資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930977"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="4bf42-102">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="4bf42-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="4bf42-103"><xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel>和控制項會取代和加入和<xref:System.Windows.Forms.StatusBarPanel>控制項的功能; 不過, 如果您這樣做, 和控制項就會保留, 以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>決定.</span><span class="sxs-lookup"><span data-stu-id="4bf42-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4bf42-104">通常，程式會為您呼叫，根據應用程式狀態或其他使用者互動的變更，在執行階段以動態方式更新狀態列面板的內容。</span><span class="sxs-lookup"><span data-stu-id="4bf42-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="4bf42-105">這是常見的方法來通知使用者，例如 CAPS LOCK、NUM LOCK 或 SCROLL LOCK 鍵已啟用，或者提供日期或時鐘以做為方便參考。</span><span class="sxs-lookup"><span data-stu-id="4bf42-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="4bf42-106">在下列範例中, 您將使用<xref:System.Windows.Forms.StatusBarPanel>類別的實例來裝載時鐘。</span><span class="sxs-lookup"><span data-stu-id="4bf42-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="4bf42-107">若要準備狀態列進行更新</span><span class="sxs-lookup"><span data-stu-id="4bf42-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="4bf42-108">建立新的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="4bf42-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="4bf42-109">新增 <xref:System.Windows.Forms.StatusBar> 控制項至表單。</span><span class="sxs-lookup"><span data-stu-id="4bf42-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="4bf42-110">如需詳細資訊，請參閱[如何：將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="4bf42-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="4bf42-111">將狀態列面板新增至您<xref:System.Windows.Forms.StatusBar>的控制項。</span><span class="sxs-lookup"><span data-stu-id="4bf42-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="4bf42-112">如需詳細資訊，請參閱[如何：將面板加入至狀態列控制項](how-to-add-panels-to-a-statusbar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="4bf42-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="4bf42-113">針對您<xref:System.Windows.Forms.StatusBar>新增至表單的控制項, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A>將屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="4bf42-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="4bf42-114">將 Windows Forms <xref:System.Windows.Forms.Timer>元件新增至表單。</span><span class="sxs-lookup"><span data-stu-id="4bf42-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4bf42-115">Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>元件是針對 Windows Forms 環境所設計。</span><span class="sxs-lookup"><span data-stu-id="4bf42-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="4bf42-116">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="4bf42-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="4bf42-117">將 <xref:System.Windows.Forms.Timer.Enabled%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4bf42-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="4bf42-118">將的<xref:System.Windows.Forms.Timer>屬性設定為30000。 <xref:System.Windows.Forms.Timer.Interval%2A></span><span class="sxs-lookup"><span data-stu-id="4bf42-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4bf42-119"><xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Interval%2A>的屬性會設定為30秒 (30000 毫秒), 以確保正確的時間會反映在所顯示的時間內。</span><span class="sxs-lookup"><span data-stu-id="4bf42-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="4bf42-120">若要實作計時器以更新狀態列</span><span class="sxs-lookup"><span data-stu-id="4bf42-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="4bf42-121">將下列程式碼插入<xref:System.Windows.Forms.Timer>元件的事件處理常式, 以更新<xref:System.Windows.Forms.StatusBar>控制項的面板。</span><span class="sxs-lookup"><span data-stu-id="4bf42-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     <span data-ttu-id="4bf42-122">此時，您已經準備好執行應用程式，並且觀察在狀態列面板中執行的時鐘。</span><span class="sxs-lookup"><span data-stu-id="4bf42-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="4bf42-123">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="4bf42-123">To test the application</span></span>  
  
1. <span data-ttu-id="4bf42-124">針對應用程式進行偵錯，並且按下 F5 鍵以執行它。</span><span class="sxs-lookup"><span data-stu-id="4bf42-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="4bf42-125">如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="4bf42-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4bf42-126">需要大約 30 秒的時間讓時鐘出現在狀態列中。</span><span class="sxs-lookup"><span data-stu-id="4bf42-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="4bf42-127">這是為了盡可能取得最準確的時間。</span><span class="sxs-lookup"><span data-stu-id="4bf42-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="4bf42-128">相反地, 若要讓時鐘更快出現, 您可以減少在上<xref:System.Windows.Forms.Timer.Interval%2A>一個程式的步驟7中設定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="4bf42-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf42-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bf42-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="4bf42-130">如何：將面板新增至狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="4bf42-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="4bf42-131">如何：判斷按一下 Windows Forms 狀態列控制項中的哪一個面板</span><span class="sxs-lookup"><span data-stu-id="4bf42-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="4bf42-132">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="4bf42-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
