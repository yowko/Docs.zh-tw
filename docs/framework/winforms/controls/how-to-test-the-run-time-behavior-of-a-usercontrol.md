---
title: HOW TO：測試 UserControl 的執行階段行為
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
ms.openlocfilehash: 1719d0461fbb582a1486dcc0726253ec97a07ac6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116489"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="9a64e-102">HOW TO：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="9a64e-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="9a64e-103">當您開發<xref:System.Windows.Forms.UserControl>，您要測試其執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="9a64e-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="9a64e-104">您可以建立個別的 Windows 應用程式專案，並將您的控制項上測試表單中，但此程序是很不方便。</span><span class="sxs-lookup"><span data-stu-id="9a64e-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="9a64e-105">更快速且輕鬆的方式是使用**UserControl 測試容器**Visual Studio 所提供。</span><span class="sxs-lookup"><span data-stu-id="9a64e-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="9a64e-106">直接從您的 Windows 控制項程式庫專案，啟動這個測試容器。</span><span class="sxs-lookup"><span data-stu-id="9a64e-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a64e-107">載入測試容器您<xref:System.Windows.Forms.UserControl>，控制項必須有至少一個公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="9a64e-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a64e-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="9a64e-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9a64e-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="9a64e-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9a64e-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="9a64e-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a64e-111">無法使用測試的 Visual c + + 控制項**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="9a64e-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="9a64e-112">若要測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="9a64e-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="9a64e-113">建立 Windows 控制項程式庫專案，稱為**TestContainerExample**。</span><span class="sxs-lookup"><span data-stu-id="9a64e-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="9a64e-114">如需詳細資訊，請參閱 < [Windows 控制項程式庫範本](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9a64e-114">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="9a64e-115">在  **Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至控制項的設計介面。</span><span class="sxs-lookup"><span data-stu-id="9a64e-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="9a64e-116">按 F5 以建置專案並執行**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="9a64e-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="9a64e-117">測試容器會顯示您<xref:System.Windows.Forms.UserControl>中**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a64e-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="9a64e-118">選取 <xref:System.Windows.Forms.Control.BackColor%2A>中顯示的屬性<xref:System.Windows.Forms.PropertyGrid>右邊的控制項**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a64e-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="9a64e-119">變更其值， `ControlDark`。</span><span class="sxs-lookup"><span data-stu-id="9a64e-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="9a64e-120">請注意，控制項就會變更為較深的色彩。</span><span class="sxs-lookup"><span data-stu-id="9a64e-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="9a64e-121">請嘗試變更其他屬性值，並觀察您的控制項上的效果。</span><span class="sxs-lookup"><span data-stu-id="9a64e-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="9a64e-122">按一下 **填滿使用者控制項的停駐**下方的核取方塊**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a64e-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="9a64e-123">請注意，調整大小以填滿窗格的控制項。</span><span class="sxs-lookup"><span data-stu-id="9a64e-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="9a64e-124">調整測試容器的大小，並觀察調整與窗格控制項大小。</span><span class="sxs-lookup"><span data-stu-id="9a64e-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="9a64e-125">關閉測試容器。</span><span class="sxs-lookup"><span data-stu-id="9a64e-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="9a64e-126">將另一個使用者控制項加入**TestContainerExample**專案。</span><span class="sxs-lookup"><span data-stu-id="9a64e-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="9a64e-127">如需詳細資訊，請參閱[如何：將現有的項目加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9a64e-127">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>  
  
8.  <span data-ttu-id="9a64e-128">在  **Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至控制項的設計介面。</span><span class="sxs-lookup"><span data-stu-id="9a64e-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="9a64e-129">按 F5 以建置專案，並執行測試容器。</span><span class="sxs-lookup"><span data-stu-id="9a64e-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="9a64e-130">按一下 **選取 使用者控制項**<xref:System.Windows.Forms.ComboBox>切換兩個使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="9a64e-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="9a64e-131">從另一個專案的測試使用者控制項</span><span class="sxs-lookup"><span data-stu-id="9a64e-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="9a64e-132">您可以在目前專案的測試容器測試從其他專案的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="9a64e-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="9a64e-133">若要測試另一個專案中的使用者控制項</span><span class="sxs-lookup"><span data-stu-id="9a64e-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="9a64e-134">建立 Windows 控制項程式庫專案，稱為**TestContainerExample2**。</span><span class="sxs-lookup"><span data-stu-id="9a64e-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="9a64e-135">如需詳細資訊，請參閱 < [Windows 控制項程式庫範本](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9a64e-135">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="9a64e-136">在  **Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.RadioButton>控制項從**工具箱**拖曳至控制項的設計介面。</span><span class="sxs-lookup"><span data-stu-id="9a64e-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="9a64e-137">按 F5 以建置專案，並執行測試容器。</span><span class="sxs-lookup"><span data-stu-id="9a64e-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="9a64e-138">測試容器會顯示您<xref:System.Windows.Forms.UserControl>中**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a64e-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="9a64e-139">按一下 [**負載**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9a64e-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="9a64e-140">在 **開放**對話方塊方塊中，瀏覽至**TestContainerExample**.dll，您在上一個程序中建立。</span><span class="sxs-lookup"><span data-stu-id="9a64e-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="9a64e-141">選取  **TestContainerExample**.dll，然後按一下**開啟**載入使用者控制項的按鈕</span><span class="sxs-lookup"><span data-stu-id="9a64e-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="9a64e-142">使用**選取 使用者控制項**<xref:System.Windows.Forms.ComboBox>切換兩個使用者控制項，從**TestContainerExample**專案。</span><span class="sxs-lookup"><span data-stu-id="9a64e-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a64e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a64e-143">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="9a64e-144">HOW TO：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="9a64e-144">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="9a64e-145">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="9a64e-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="9a64e-146">逐步解說：使用 Visual C# 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="9a64e-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="9a64e-147">使用者控制項設計工具</span><span class="sxs-lookup"><span data-stu-id="9a64e-147">User Control Designer</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
