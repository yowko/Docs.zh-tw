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
ms.openlocfilehash: 49722d5dadf694e8ee3037646652b921ddda3e91
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542599"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="b2b40-102">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="b2b40-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b2b40-103"><xref:System.Windows.Forms.StatusStrip>及<xref:System.Windows.Forms.ToolStripStatusLabel>控制項會取代及新增功能<xref:System.Windows.Forms.StatusBar>並<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項保留回溯相容性和未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="b2b40-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b2b40-104">通常，程式會為您呼叫，根據應用程式狀態或其他使用者互動的變更，在執行階段以動態方式更新狀態列面板的內容。</span><span class="sxs-lookup"><span data-stu-id="b2b40-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="b2b40-105">這是常見的方法來通知使用者，例如 CAPS LOCK、NUM LOCK 或 SCROLL LOCK 鍵已啟用，或者提供日期或時鐘以做為方便參考。</span><span class="sxs-lookup"><span data-stu-id="b2b40-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="b2b40-106">在下列範例中，您將使用的執行個體<xref:System.Windows.Forms.StatusBarPanel>類別來裝載時鐘。</span><span class="sxs-lookup"><span data-stu-id="b2b40-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="b2b40-107">若要準備狀態列進行更新</span><span class="sxs-lookup"><span data-stu-id="b2b40-107">To get the status bar ready for updating</span></span>  
  
1.  <span data-ttu-id="b2b40-108">建立新的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="b2b40-108">Create a new Windows form.</span></span>  
  
2.  <span data-ttu-id="b2b40-109">新增 <xref:System.Windows.Forms.StatusBar> 控制項至表單。</span><span class="sxs-lookup"><span data-stu-id="b2b40-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="b2b40-110">如需詳細資訊，請參閱[如何：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b40-110">For details, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="b2b40-111">加入至狀態列面板您<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="b2b40-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="b2b40-112">如需詳細資訊，請參閱[如何：將面板新增至 StatusBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b2b40-112">For details, see [How to: Add Panels to a StatusBar Control](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4.  <span data-ttu-id="b2b40-113">針對<xref:System.Windows.Forms.StatusBar>控制項新增至表單，設定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="b2b40-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="b2b40-114">加入 Windows Form<xref:System.Windows.Forms.Timer>元件至表單。</span><span class="sxs-lookup"><span data-stu-id="b2b40-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2b40-115">Windows Form<xref:System.Windows.Forms.Timer?displayProperty=nameWithType>元件專為 Windows Form 環境。</span><span class="sxs-lookup"><span data-stu-id="b2b40-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="b2b40-116">如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。</span><span class="sxs-lookup"><span data-stu-id="b2b40-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
6.  <span data-ttu-id="b2b40-117">將 <xref:System.Windows.Forms.Timer.Enabled%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b2b40-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7.  <span data-ttu-id="b2b40-118">設定<xref:System.Windows.Forms.Timer.Interval%2A>屬性<xref:System.Windows.Forms.Timer>為 30000。</span><span class="sxs-lookup"><span data-stu-id="b2b40-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2b40-119"><xref:System.Windows.Forms.Timer.Interval%2A>屬性<xref:System.Windows.Forms.Timer>元件會設定為 30 秒 （30,000 毫秒），以確保正確的時間會反映在顯示的時間。</span><span class="sxs-lookup"><span data-stu-id="b2b40-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="b2b40-120">若要實作計時器以更新狀態列</span><span class="sxs-lookup"><span data-stu-id="b2b40-120">To implement the timer to update the status bar</span></span>  
  
1.  <span data-ttu-id="b2b40-121">下列程式碼插入的事件處理常式<xref:System.Windows.Forms.Timer>元件，以更新的面板<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="b2b40-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="b2b40-122">此時，您已經準備好執行應用程式，並且觀察在狀態列面板中執行的時鐘。</span><span class="sxs-lookup"><span data-stu-id="b2b40-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="b2b40-123">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="b2b40-123">To test the application</span></span>  
  
1.  <span data-ttu-id="b2b40-124">針對應用程式進行偵錯，並且按下 F5 鍵以執行它。</span><span class="sxs-lookup"><span data-stu-id="b2b40-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="b2b40-125">如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="b2b40-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2b40-126">需要大約 30 秒的時間讓時鐘出現在狀態列中。</span><span class="sxs-lookup"><span data-stu-id="b2b40-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="b2b40-127">這是為了盡可能取得最準確的時間。</span><span class="sxs-lookup"><span data-stu-id="b2b40-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="b2b40-128">相反地，若要讓時鐘更早出現，您可以減少的值<xref:System.Windows.Forms.Timer.Interval%2A>您在之前程序中的步驟 7 中設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b40-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b40-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b40-129">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="b2b40-130">操作說明：將面板新增至 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="b2b40-130">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [<span data-ttu-id="b2b40-131">操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="b2b40-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="b2b40-132">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b2b40-132">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
