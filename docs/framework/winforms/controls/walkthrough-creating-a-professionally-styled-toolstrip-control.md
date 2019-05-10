---
title: 逐步解說：建立專業樣式的 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211763"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="1a46a-102">逐步解說：建立專業樣式的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="1a46a-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>

<span data-ttu-id="1a46a-103">您可以提供給您的應用程式<xref:System.Windows.Forms.ToolStrip>撰寫您自己的類別衍生自控制項專業外觀和行為<xref:System.Windows.Forms.ToolStripProfessionalRenderer>型別。</span><span class="sxs-lookup"><span data-stu-id="1a46a-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>

<span data-ttu-id="1a46a-104">本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項，以建立複合控制項，以類似**瀏覽窗格**Microsoft® Outlook® 提供的。</span><span class="sxs-lookup"><span data-stu-id="1a46a-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="1a46a-105">本逐步解說會說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="1a46a-105">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="1a46a-106">建立 Windows 控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="1a46a-106">Creating a Windows Control Library project.</span></span>

- <span data-ttu-id="1a46a-107">設計 StackView 控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-107">Designing the StackView Control.</span></span>

- <span data-ttu-id="1a46a-108">實作自訂轉譯器。</span><span class="sxs-lookup"><span data-stu-id="1a46a-108">Implementing a Custom Renderer.</span></span>

<span data-ttu-id="1a46a-109">當您完成時，您必須使用 Microsoft Office® XP 控制項專業外觀的可重複使用的自訂用戶端控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>

<span data-ttu-id="1a46a-110">若要將此主題中的程式碼複製為單一清單，請參閱[如何：建立專業樣式的 ToolStrip 控制項](how-to-create-a-professionally-styled-toolstrip-control.md)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a46a-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="1a46a-111">Prerequisites</span></span>

<span data-ttu-id="1a46a-112">您將需要 Visual Studio 來完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="1a46a-112">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="1a46a-113">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="1a46a-113">Create the control library project</span></span>

1. <span data-ttu-id="1a46a-114">在 Visual Studio 中建立新的 Windows 控制項程式庫專案，名為`StackViewLibrary`。</span><span class="sxs-lookup"><span data-stu-id="1a46a-114">In Visual Studio, create a new Windows Control Library project named `StackViewLibrary`.</span></span>

2. <span data-ttu-id="1a46a-115">在 [**方案總管] 中**，藉由刪除原始程式檔，視您選擇的語言而定，名為"UserControl1.cs 」 或 「 UserControl1.vb"，刪除專案的預設控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-115">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

     <span data-ttu-id="1a46a-116">如需詳細資訊，請參閱[如何：移除，請刪除，並排除項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1a46a-116">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="1a46a-117">加入新<xref:System.Windows.Forms.UserControl>項目**StackViewLibrary**專案。</span><span class="sxs-lookup"><span data-stu-id="1a46a-117">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="1a46a-118">提供新的原始程式檔的基底名稱`StackView`。</span><span class="sxs-lookup"><span data-stu-id="1a46a-118">Give the new source file a base name of `StackView`.</span></span>

## <a name="design-the-stackview-control"></a><span data-ttu-id="1a46a-119">設計 StackView 控制項</span><span class="sxs-lookup"><span data-stu-id="1a46a-119">Design the StackView control</span></span>

<span data-ttu-id="1a46a-120">`StackView`控制項是具有一個子系的複合控制項<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-120">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="1a46a-121">如需有關複合控制項的詳細資訊，請參閱[各種自訂控制項](varieties-of-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-121">For more information about composite controls, see [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

1. <span data-ttu-id="1a46a-122">從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStrip>控制項至設計介面。</span><span class="sxs-lookup"><span data-stu-id="1a46a-122">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>

2. <span data-ttu-id="1a46a-123">在 **屬性**視窗中，將<xref:System.Windows.Forms.ToolStrip>根據下表的控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a46a-123">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>

    |<span data-ttu-id="1a46a-124">屬性</span><span class="sxs-lookup"><span data-stu-id="1a46a-124">Property</span></span>|<span data-ttu-id="1a46a-125">值</span><span class="sxs-lookup"><span data-stu-id="1a46a-125">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1a46a-126">名稱</span><span class="sxs-lookup"><span data-stu-id="1a46a-126">Name</span></span>|`stackStrip`|
    |<span data-ttu-id="1a46a-127">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="1a46a-127">CanOverflow</span></span>|`false`|
    |<span data-ttu-id="1a46a-128">停駐</span><span class="sxs-lookup"><span data-stu-id="1a46a-128">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |<span data-ttu-id="1a46a-129">字型</span><span class="sxs-lookup"><span data-stu-id="1a46a-129">Font</span></span>|`Tahoma, 10pt, style=Bold`|
    |<span data-ttu-id="1a46a-130">GripStyle</span><span class="sxs-lookup"><span data-stu-id="1a46a-130">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |<span data-ttu-id="1a46a-131">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="1a46a-131">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |<span data-ttu-id="1a46a-132">與邊框距離</span><span class="sxs-lookup"><span data-stu-id="1a46a-132">Padding</span></span>|`0, 7, 0, 0`|
    |<span data-ttu-id="1a46a-133">RenderMode</span><span class="sxs-lookup"><span data-stu-id="1a46a-133">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. <span data-ttu-id="1a46a-134">在 Windows Form 設計工具中，按一下<xref:System.Windows.Forms.ToolStrip>控制項的**新增**按鈕，然後新增<xref:System.Windows.Forms.ToolStripButton>到`stackStrip`控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-134">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>

4. <span data-ttu-id="1a46a-135">在 **屬性**視窗中，將<xref:System.Windows.Forms.ToolStripButton>根據下表的控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a46a-135">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>

    |<span data-ttu-id="1a46a-136">屬性</span><span class="sxs-lookup"><span data-stu-id="1a46a-136">Property</span></span>|<span data-ttu-id="1a46a-137">值</span><span class="sxs-lookup"><span data-stu-id="1a46a-137">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1a46a-138">名稱</span><span class="sxs-lookup"><span data-stu-id="1a46a-138">Name</span></span>|`mailStackButton`|
    |<span data-ttu-id="1a46a-139">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="1a46a-139">CheckOnClick</span></span>|<span data-ttu-id="1a46a-140">true</span><span class="sxs-lookup"><span data-stu-id="1a46a-140">true</span></span>|
    |<span data-ttu-id="1a46a-141">CheckState</span><span class="sxs-lookup"><span data-stu-id="1a46a-141">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|
    |<span data-ttu-id="1a46a-142">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="1a46a-142">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |<span data-ttu-id="1a46a-143">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="1a46a-143">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |<span data-ttu-id="1a46a-144">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="1a46a-144">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |<span data-ttu-id="1a46a-145">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="1a46a-145">ImageTransparentColor</span></span>|`238, 238, 238`|
    |<span data-ttu-id="1a46a-146">邊界</span><span class="sxs-lookup"><span data-stu-id="1a46a-146">Margin</span></span>|`0, 0, 0, 0`|
    |<span data-ttu-id="1a46a-147">與邊框距離</span><span class="sxs-lookup"><span data-stu-id="1a46a-147">Padding</span></span>|`3, 3, 3, 3`|
    |<span data-ttu-id="1a46a-148">文字</span><span class="sxs-lookup"><span data-stu-id="1a46a-148">Text</span></span>|<span data-ttu-id="1a46a-149">**郵件**</span><span class="sxs-lookup"><span data-stu-id="1a46a-149">**Mail**</span></span>|
    |<span data-ttu-id="1a46a-150">TextAlign</span><span class="sxs-lookup"><span data-stu-id="1a46a-150">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. <span data-ttu-id="1a46a-151">重複步驟 7 的另外三個<xref:System.Windows.Forms.ToolStripButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-151">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

     <span data-ttu-id="1a46a-152">控制項`calendarStackButton`， `contactsStackButton`，和`tasksStackButton`。</span><span class="sxs-lookup"><span data-stu-id="1a46a-152">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="1a46a-153">設定的值<xref:System.Windows.Forms.Control.Text%2A>屬性，以**行事曆**，**連絡人**，和**工作**分別。</span><span class="sxs-lookup"><span data-stu-id="1a46a-153">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>

## <a name="handle-events"></a><span data-ttu-id="1a46a-154">處理事件</span><span class="sxs-lookup"><span data-stu-id="1a46a-154">Handle events</span></span>

<span data-ttu-id="1a46a-155">兩個事件都必須能夠讓`StackView`控制項正常運作。</span><span class="sxs-lookup"><span data-stu-id="1a46a-155">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="1a46a-156">處理<xref:System.Windows.Forms.UserControl.Load>正確放置控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="1a46a-156">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="1a46a-157">處理<xref:System.Windows.Forms.ToolStripItem.Click>針對每個事件<xref:System.Windows.Forms.ToolStripButton>提供給`StackView`控制狀態行為類似於<xref:System.Windows.Forms.RadioButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-157">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>

1. <span data-ttu-id="1a46a-158">在 Windows Form 設計工具中，選取 `StackView`控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-158">In the Windows Forms Designer, select the `StackView` control.</span></span>

2. <span data-ttu-id="1a46a-159">在 [屬性] 視窗中按一下 [事件]。</span><span class="sxs-lookup"><span data-stu-id="1a46a-159">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="1a46a-160">按兩下 Load 事件，以產生`StackView_Load`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1a46a-160">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>

4. <span data-ttu-id="1a46a-161">在 `StackView_Load` 事件處理常式中，複製並貼入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a46a-161">In the `StackView_Load` event handler, copy and paste the following code.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. <span data-ttu-id="1a46a-162">在 Windows Form 設計工具中，選取 `mailStackButton`控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-162">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>

6. <span data-ttu-id="1a46a-163">在 [屬性] 視窗中按一下 [事件]。</span><span class="sxs-lookup"><span data-stu-id="1a46a-163">In the **Properties** window, click **Events**.</span></span>

7. <span data-ttu-id="1a46a-164">按兩下 Click 事件。</span><span class="sxs-lookup"><span data-stu-id="1a46a-164">Double-click the Click event.</span></span>

     <span data-ttu-id="1a46a-165">Windows Form 設計工具產生`mailStackButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1a46a-165">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>

8. <span data-ttu-id="1a46a-166">重新命名`mailStackButton_Click`事件處理常式來`stackButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="1a46a-166">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>

     <span data-ttu-id="1a46a-167">如需詳細資訊，請參閱 <<c0> [ 重新命名重構程式碼符號](/visualstudio/ide/reference/rename)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-167">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

9. <span data-ttu-id="1a46a-168">插入下列程式碼插入`stackButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1a46a-168">Insert the following code into the `stackButton_Click` event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. <span data-ttu-id="1a46a-169">在 Windows Form 設計工具中，選取 `calendarStackButton`控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-169">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>

11. <span data-ttu-id="1a46a-170">在 **屬性**視窗中，若要將 Click 事件`stackButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1a46a-170">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>

12. <span data-ttu-id="1a46a-171">重複步驟 10 和 11 for`contactsStackButton`和`tasksStackButton`控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-171">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>

## <a name="define-icons"></a><span data-ttu-id="1a46a-172">定義圖示</span><span class="sxs-lookup"><span data-stu-id="1a46a-172">Define icons</span></span>

<span data-ttu-id="1a46a-173">每個`StackView`按鈕有一個相關聯的圖示。</span><span class="sxs-lookup"><span data-stu-id="1a46a-173">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="1a46a-174">為了方便起見，每個圖示表示為 Base64 編碼字串時，這會還原序列化之前<xref:System.Drawing.Bitmap>從它所建立。</span><span class="sxs-lookup"><span data-stu-id="1a46a-174">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="1a46a-175">在生產環境中，您將點陣圖資料儲存為資源，並圖示會出現在 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="1a46a-175">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="1a46a-176">如需詳細資訊，請參閱[如何：將背景影像加入至 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1a46a-176">For more information, see [How to: Add Background Images to Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span></span>

1. <span data-ttu-id="1a46a-177">在程式碼編輯器中，插入下列程式碼插入`StackView`類別定義。</span><span class="sxs-lookup"><span data-stu-id="1a46a-177">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="1a46a-178">此程式碼會初始化的點陣圖<xref:System.Windows.Forms.ToolStripButton>圖示。</span><span class="sxs-lookup"><span data-stu-id="1a46a-178">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. <span data-ttu-id="1a46a-179">將呼叫加入`InitializeImages`方法中的`StackView`類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="1a46a-179">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a><span data-ttu-id="1a46a-180">實作自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="1a46a-180">Implement a custom renderer</span></span>

<span data-ttu-id="1a46a-181">您可以自訂的大部分項目`StackView`控制我的實作類別衍生自<xref:System.Windows.Forms.ToolStripRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="1a46a-181">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="1a46a-182">在此程序中，您將實作<xref:System.Windows.Forms.ToolStripProfessionalRenderer>類別可自訂的底框，並繪製漸層背景<xref:System.Windows.Forms.ToolStripButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-182">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

1. <span data-ttu-id="1a46a-183">插入下列程式碼插入`StackView`控制定義。</span><span class="sxs-lookup"><span data-stu-id="1a46a-183">Insert the following code into the `StackView` control definition.</span></span>

     <span data-ttu-id="1a46a-184">這是針對定義`StackRenderer`類別，它會覆寫<xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>， <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>，和<xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground>方法來產生自訂的外觀。</span><span class="sxs-lookup"><span data-stu-id="1a46a-184">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. <span data-ttu-id="1a46a-185">在 `StackView`控制項的建構函式，建立的新執行個體`StackRenderer`類別，將指派到這個執行個體`stackStrip`控制項的<xref:System.Windows.Forms.ToolStrip.Renderer%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1a46a-185">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a><span data-ttu-id="1a46a-186">測試 StackView 控制項</span><span class="sxs-lookup"><span data-stu-id="1a46a-186">Test the StackView control</span></span>

<span data-ttu-id="1a46a-187">`StackView`控制項是衍生自<xref:System.Windows.Forms.UserControl>類別。</span><span class="sxs-lookup"><span data-stu-id="1a46a-187">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="1a46a-188">因此，您可以測試具有的控制項**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="1a46a-188">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="1a46a-189">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-189">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

1. <span data-ttu-id="1a46a-190">按下**F5**以建置專案並啟動**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="1a46a-190">Press **F5** to build the project and start the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="1a46a-191">將指標移的按鈕`StackView`控制項，然後再按一下按鈕，請參閱其選取狀態的外觀。</span><span class="sxs-lookup"><span data-stu-id="1a46a-191">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1a46a-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1a46a-192">Next steps</span></span>

<span data-ttu-id="1a46a-193">在本逐步解說中，您已建立可重複使用的自訂用戶端控制項專業外觀的 Office XP 控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-193">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="1a46a-194">您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：</span><span class="sxs-lookup"><span data-stu-id="1a46a-194">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="1a46a-195">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="1a46a-195">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="1a46a-196">如需詳細資訊，請參閱 < [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-196">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="1a46a-197">使用自動填入的標準功能表中建立的表單。</span><span class="sxs-lookup"><span data-stu-id="1a46a-197">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="1a46a-198">如需詳細資訊，請參閱[逐步解說：對表單提供標準功能表項目](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-198">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="1a46a-199">建立多個文件介面 (MDI) 表單使用停駐<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="1a46a-199">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="1a46a-200">如需詳細資訊，請參閱[如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="1a46a-200">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a46a-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a46a-201">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="1a46a-202">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="1a46a-202">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="1a46a-203">如何：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="1a46a-203">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
