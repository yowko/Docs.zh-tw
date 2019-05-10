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
ms.openlocfilehash: 48531ab1ef3b30b6516e3f2e7b5858a8884cbfe8
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211696"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="68745-102">HOW TO：測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="68745-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="68745-103">當您開發<xref:System.Windows.Forms.UserControl>，您要測試其執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="68745-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="68745-104">您可以建立個別的 Windows 應用程式專案，並將您的控制項上測試表單中，但此程序是很不方便。</span><span class="sxs-lookup"><span data-stu-id="68745-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="68745-105">更快速且輕鬆的方式是使用**UserControl 測試容器**Visual Studio 所提供。</span><span class="sxs-lookup"><span data-stu-id="68745-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="68745-106">直接從您的 Windows 控制項程式庫專案，啟動這個測試容器。</span><span class="sxs-lookup"><span data-stu-id="68745-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68745-107">載入測試容器您<xref:System.Windows.Forms.UserControl>，控制項必須有至少一個公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="68745-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="68745-108">視覺效果C++控制項無法使用測試**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="68745-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="68745-109">測試 UserControl 的執行階段行為</span><span class="sxs-lookup"><span data-stu-id="68745-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="68745-110">在 Visual Studio 中，建立 Windows 控制項程式庫專案，稱為**TestContainerExample**。</span><span class="sxs-lookup"><span data-stu-id="68745-110">In Visual Studio, create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="68745-111">如需詳細資訊，請參閱 < [Windows 控制項程式庫範本](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="68745-111">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="68745-112">在  **Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.Label>控制項從**工具箱**拖曳至控制項的設計介面。</span><span class="sxs-lookup"><span data-stu-id="68745-112">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="68745-113">按下**F5**以建置專案並執行**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="68745-113">Press **F5** to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="68745-114">測試容器會顯示您<xref:System.Windows.Forms.UserControl>中**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="68745-114">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="68745-115">選取 <xref:System.Windows.Forms.Control.BackColor%2A>中顯示的屬性<xref:System.Windows.Forms.PropertyGrid>右邊的控制項**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="68745-115">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="68745-116">變更其值， `ControlDark`。</span><span class="sxs-lookup"><span data-stu-id="68745-116">Change its value to `ControlDark`.</span></span> <span data-ttu-id="68745-117">請注意，控制項就會變更為較深的色彩。</span><span class="sxs-lookup"><span data-stu-id="68745-117">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="68745-118">請嘗試變更其他屬性值，並觀察您的控制項上的效果。</span><span class="sxs-lookup"><span data-stu-id="68745-118">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="68745-119">按一下 **填滿使用者控制項的停駐**下方的核取方塊**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="68745-119">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="68745-120">請注意，調整大小以填滿窗格的控制項。</span><span class="sxs-lookup"><span data-stu-id="68745-120">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="68745-121">調整測試容器的大小，並觀察調整與窗格控制項大小。</span><span class="sxs-lookup"><span data-stu-id="68745-121">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="68745-122">關閉測試容器。</span><span class="sxs-lookup"><span data-stu-id="68745-122">Close the test container.</span></span>

7. <span data-ttu-id="68745-123">將另一個使用者控制項加入**TestContainerExample**專案。</span><span class="sxs-lookup"><span data-stu-id="68745-123">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="68745-124">如需詳細資訊，請參閱[如何：將現有的項目加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="68745-124">For details, see [How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100)).</span></span>

8. <span data-ttu-id="68745-125">在  **Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至控制項的設計介面。</span><span class="sxs-lookup"><span data-stu-id="68745-125">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="68745-126">按 F5 以建置專案，並執行測試容器。</span><span class="sxs-lookup"><span data-stu-id="68745-126">Press F5 to build the project and run the test container.</span></span>

10. <span data-ttu-id="68745-127">按一下 **選取 使用者控制項**<xref:System.Windows.Forms.ComboBox>切換兩個使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="68745-127">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="68745-128">從另一個專案的測試使用者控制項</span><span class="sxs-lookup"><span data-stu-id="68745-128">Test user controls from another project</span></span>

<span data-ttu-id="68745-129">您可以在目前專案的測試容器測試從其他專案的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="68745-129">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="68745-130">建立 Windows 控制項程式庫專案，稱為**TestContainerExample2**。</span><span class="sxs-lookup"><span data-stu-id="68745-130">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="68745-131">如需詳細資訊，請參閱 < [Windows 控制項程式庫範本](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="68745-131">For details, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="68745-132">在  **Windows Form 設計工具**，拖曳<xref:System.Windows.Forms.RadioButton>控制項從**工具箱**拖曳至控制項的設計介面。</span><span class="sxs-lookup"><span data-stu-id="68745-132">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="68745-133">按 F5 以建置專案，並執行測試容器。</span><span class="sxs-lookup"><span data-stu-id="68745-133">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="68745-134">測試容器會顯示您<xref:System.Windows.Forms.UserControl>中**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="68745-134">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="68745-135">按一下 [**負載**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="68745-135">Click the **Load** button.</span></span>

5. <span data-ttu-id="68745-136">在 **開放**對話方塊方塊中，瀏覽至**TestContainerExample**.dll，您在上一個程序中建立。</span><span class="sxs-lookup"><span data-stu-id="68745-136">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="68745-137">選取  **TestContainerExample**.dll，然後按一下**開啟**載入使用者控制項的按鈕</span><span class="sxs-lookup"><span data-stu-id="68745-137">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>

6. <span data-ttu-id="68745-138">使用**選取 使用者控制項**<xref:System.Windows.Forms.ComboBox>切換兩個使用者控制項，從**TestContainerExample**專案。</span><span class="sxs-lookup"><span data-stu-id="68745-138">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="68745-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68745-139">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="68745-140">如何：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="68745-140">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="68745-141">逐步解說：撰寫使用 Visual Basic 複合控制項</span><span class="sxs-lookup"><span data-stu-id="68745-141">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="68745-142">逐步解說：撰寫複合控制項具有視覺效果C#</span><span class="sxs-lookup"><span data-stu-id="68745-142">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- <span data-ttu-id="68745-143">[使用者控制項設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="68745-143">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
