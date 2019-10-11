---
title: 作法：測試 UserControl 的執行階段行為
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180199"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="d50fa-102">作法：測試 UserControl 的執行時間行為</span><span class="sxs-lookup"><span data-stu-id="d50fa-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="d50fa-103">當您開發 <xref:System.Windows.Forms.UserControl> 時，您需要測試其執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="d50fa-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="d50fa-104">您可以建立個別的 Windows 應用程式專案，並將控制項放在測試表單上，但此程式並不方便。</span><span class="sxs-lookup"><span data-stu-id="d50fa-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="d50fa-105">更快速且更簡單的方式，就是使用 Visual Studio 所提供的**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="d50fa-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="d50fa-106">此測試容器會直接從您的 Windows 控制項程式庫專案開始。</span><span class="sxs-lookup"><span data-stu-id="d50fa-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d50fa-107">若要讓測試容器載入您的 <xref:System.Windows.Forms.UserControl>，控制項必須至少有一個公用的函式。</span><span class="sxs-lookup"><span data-stu-id="d50fa-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="d50fa-108">視覺效果C++控制項無法使用**UserControl 測試容器**進行測試。</span><span class="sxs-lookup"><span data-stu-id="d50fa-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="d50fa-109">測試 UserControl 的執行時間行為</span><span class="sxs-lookup"><span data-stu-id="d50fa-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="d50fa-110">在 Visual Studio 中，建立 Windows 控制項程式庫專案，並將其命名為**TestContainerExample**。</span><span class="sxs-lookup"><span data-stu-id="d50fa-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="d50fa-111">在  **Windows Form 設計工具**中，從 **工具箱** 將 @no__t 1 控制項拖曳至控制項的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="d50fa-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="d50fa-112">按<kbd>F5</kbd>以建立專案，並執行**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="d50fa-112">Press <kbd>F5</kbd> to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="d50fa-113">測試容器會在**預覽**窗格中顯示 <xref:System.Windows.Forms.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="d50fa-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="d50fa-114">選取 [**預覽**] 窗格右邊的 [<xref:System.Windows.Forms.PropertyGrid>] 控制項中所顯示的 [<xref:System.Windows.Forms.Control.BackColor%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="d50fa-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="d50fa-115">將其值變更為**ControlDark**。</span><span class="sxs-lookup"><span data-stu-id="d50fa-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="d50fa-116">觀察控制項是否變更為較暗的色彩。</span><span class="sxs-lookup"><span data-stu-id="d50fa-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="d50fa-117">請嘗試變更其他屬性值，並觀察對控制項的影響。</span><span class="sxs-lookup"><span data-stu-id="d50fa-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="d50fa-118">按一下**預覽**窗格下方的 [停**駐填滿使用者控制項**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d50fa-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="d50fa-119">觀察控制項已調整大小以填滿窗格。</span><span class="sxs-lookup"><span data-stu-id="d50fa-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="d50fa-120">調整測試容器的大小，並觀察控制項是否隨著窗格調整大小。</span><span class="sxs-lookup"><span data-stu-id="d50fa-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="d50fa-121">關閉測試容器。</span><span class="sxs-lookup"><span data-stu-id="d50fa-121">Close the test container.</span></span>

7. <span data-ttu-id="d50fa-122">將另一個使用者控制項加入至**TestContainerExample**專案。</span><span class="sxs-lookup"><span data-stu-id="d50fa-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="d50fa-123">在  **Windows Form 設計工具**中，從 **工具箱** 將 @no__t 1 控制項拖曳至控制項的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="d50fa-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="d50fa-124">按<kbd>F5</kbd>以建立專案並執行測試容器。</span><span class="sxs-lookup"><span data-stu-id="d50fa-124">Press <kbd>F5</kbd> to build the project and run the test container.</span></span>

10. <span data-ttu-id="d50fa-125">按一下 [**選取使用者控制項**<xref:System.Windows.Forms.ComboBox>]，在兩個使用者控制項之間切換。</span><span class="sxs-lookup"><span data-stu-id="d50fa-125">Click the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="d50fa-126">從另一個專案測試使用者控制項</span><span class="sxs-lookup"><span data-stu-id="d50fa-126">Test user controls from another project</span></span>

<span data-ttu-id="d50fa-127">您可以在目前專案的測試容器中，測試其他專案的使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="d50fa-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="d50fa-128">在 Visual Studio 中，建立 Windows 控制項程式庫專案，並將其命名為**TestContainerExample2**。</span><span class="sxs-lookup"><span data-stu-id="d50fa-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="d50fa-129">在  **Windows Form 設計工具**中，從 **工具箱** 將 @no__t 1 控制項拖曳至控制項的設計介面上。</span><span class="sxs-lookup"><span data-stu-id="d50fa-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="d50fa-130">按<kbd>F5</kbd>以建立專案並執行測試容器。</span><span class="sxs-lookup"><span data-stu-id="d50fa-130">Press <kbd>F5</kbd> to build the project and run the test container.</span></span> <span data-ttu-id="d50fa-131">測試容器會在**預覽**窗格中顯示 <xref:System.Windows.Forms.UserControl>。</span><span class="sxs-lookup"><span data-stu-id="d50fa-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="d50fa-132">按一下 [**載入**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d50fa-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="d50fa-133">在 [**開啟**] 對話方塊中，流覽至您在上一個程式中建立的*TestContainerExample。*</span><span class="sxs-lookup"><span data-stu-id="d50fa-133">In the **Open** dialog box, navigate to *TestContainerExample.dll*, which you built in the previous procedure.</span></span> <span data-ttu-id="d50fa-134">選取 [ *TestContainerExample* ]，然後按一下 [**開啟**] 按鈕以載入使用者控制項。</span><span class="sxs-lookup"><span data-stu-id="d50fa-134">Select *TestContainerExample.dll* and click the **Open** button to load the user controls.</span></span>

6. <span data-ttu-id="d50fa-135">使用 [**選取使用者控制項**<xref:System.Windows.Forms.ComboBox>]，從**TestContainerExample**專案中的兩個使用者控制項之間切換。</span><span class="sxs-lookup"><span data-stu-id="d50fa-135">Use the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="d50fa-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d50fa-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <span data-ttu-id="d50fa-137">[如何：撰寫複合控制項 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="d50fa-137">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>
- <span data-ttu-id="d50fa-138">[逐步解說：撰寫複合控制項 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="d50fa-138">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>
- <span data-ttu-id="d50fa-139">[使用者控制項設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d50fa-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
