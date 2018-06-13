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
ms.openlocfilehash: 2d2443f1f7153ed35aecbbb9d69c9e1421269e24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541602"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="64838-102">逐步解說：建立專業樣式的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="64838-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="64838-103">您可以提供您的應用程式<xref:System.Windows.Forms.ToolStrip>撰寫您自己的類別衍生自控制項專業外觀和行為<xref:System.Windows.Forms.ToolStripProfessionalRenderer>型別。</span><span class="sxs-lookup"><span data-stu-id="64838-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="64838-104">本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項建立複合控制項，以類似**瀏覽窗格**Microsoft® Outlook® 提供的。</span><span class="sxs-lookup"><span data-stu-id="64838-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="64838-105">在本逐步解說說明下列工作：</span><span class="sxs-lookup"><span data-stu-id="64838-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="64838-106">建立 Windows 控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="64838-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="64838-107">StackView 控制項的設計。</span><span class="sxs-lookup"><span data-stu-id="64838-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="64838-108">實作自訂轉譯器。</span><span class="sxs-lookup"><span data-stu-id="64838-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="64838-109">當您完成時，您必須使用 Microsoft Office () XP 控制項專業外觀的可重複使用的自訂用戶端控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="64838-110">若要為單一列出本主題中複製的程式碼，請參閱[How to： 建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md)。</span><span class="sxs-lookup"><span data-stu-id="64838-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64838-111">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="64838-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="64838-112">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="64838-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="64838-113">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="64838-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="64838-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="64838-114">Prerequisites</span></span>  
 <span data-ttu-id="64838-115">若要完成這個逐步解說，您將需要：</span><span class="sxs-lookup"><span data-stu-id="64838-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="64838-116">若要能夠建立及安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="64838-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="64838-117">建立 Windows 控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="64838-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="64838-118">第一個步驟是建立控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="64838-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="64838-119">若要建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="64838-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="64838-120">建立新的 Windows 控制項程式庫專案，名為`StackViewLibrary`。</span><span class="sxs-lookup"><span data-stu-id="64838-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="64838-121">在**方案總管 中**，藉由刪除來源檔案，視您所選擇的語言而定，名為"UserControl1.cs"或"UserControl1.vb"，刪除專案的預設控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="64838-122">如需詳細資訊，請參閱[NIB： 如何： 移除、 刪除和排除的項目](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。</span><span class="sxs-lookup"><span data-stu-id="64838-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="64838-123">加入新<xref:System.Windows.Forms.UserControl>項目**StackViewLibrary**專案。</span><span class="sxs-lookup"><span data-stu-id="64838-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="64838-124">提供新的來源檔案的基底名稱`StackView`。</span><span class="sxs-lookup"><span data-stu-id="64838-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="64838-125">設計 StackView 控制項</span><span class="sxs-lookup"><span data-stu-id="64838-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="64838-126">`StackView`控制項是具有一個子系的複合控制項<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="64838-127">如需複合控制項的詳細資訊，請參閱[須自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="64838-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="64838-128">設計 StackView 控制項</span><span class="sxs-lookup"><span data-stu-id="64838-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="64838-129">從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStrip>至設計介面的控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="64838-130">在**屬性**視窗中，將<xref:System.Windows.Forms.ToolStrip>根據下表的控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="64838-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="64838-131">屬性</span><span class="sxs-lookup"><span data-stu-id="64838-131">Property</span></span>|<span data-ttu-id="64838-132">值</span><span class="sxs-lookup"><span data-stu-id="64838-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="64838-133">名稱</span><span class="sxs-lookup"><span data-stu-id="64838-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="64838-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="64838-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="64838-135">停駐</span><span class="sxs-lookup"><span data-stu-id="64838-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="64838-136">字型</span><span class="sxs-lookup"><span data-stu-id="64838-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="64838-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="64838-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="64838-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="64838-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="64838-139">與邊框距離</span><span class="sxs-lookup"><span data-stu-id="64838-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="64838-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="64838-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="64838-141">在 Windows Form 設計工具中，按一下 <xref:System.Windows.Forms.ToolStrip>控制項的**新增**按鈕，然後加入<xref:System.Windows.Forms.ToolStripButton>至`stackStrip`控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="64838-142">在**屬性**視窗中，將<xref:System.Windows.Forms.ToolStripButton>根據下表的控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="64838-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="64838-143">屬性</span><span class="sxs-lookup"><span data-stu-id="64838-143">Property</span></span>|<span data-ttu-id="64838-144">值</span><span class="sxs-lookup"><span data-stu-id="64838-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="64838-145">名稱</span><span class="sxs-lookup"><span data-stu-id="64838-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="64838-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="64838-146">CheckOnClick</span></span>|<span data-ttu-id="64838-147">true</span><span class="sxs-lookup"><span data-stu-id="64838-147">true</span></span>|  
    |<span data-ttu-id="64838-148">已核取 CheckState</span><span class="sxs-lookup"><span data-stu-id="64838-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="64838-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="64838-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="64838-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="64838-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="64838-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="64838-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="64838-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="64838-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="64838-153">邊界</span><span class="sxs-lookup"><span data-stu-id="64838-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="64838-154">與邊框距離</span><span class="sxs-lookup"><span data-stu-id="64838-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="64838-155">Text</span><span class="sxs-lookup"><span data-stu-id="64838-155">Text</span></span>|<span data-ttu-id="64838-156">**郵件**</span><span class="sxs-lookup"><span data-stu-id="64838-156">**Mail**</span></span>|  
    |<span data-ttu-id="64838-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="64838-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="64838-158">重複步驟 7 的三個<xref:System.Windows.Forms.ToolStripButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="64838-159">命名控制項`calendarStackButton`， `contactsStackButton`，和`tasksStackButton`。</span><span class="sxs-lookup"><span data-stu-id="64838-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="64838-160">值設定<xref:System.Windows.Forms.Control.Text%2A>屬性**行事曆**，**連絡人**，和**工作**分別。</span><span class="sxs-lookup"><span data-stu-id="64838-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="64838-161">處理事件</span><span class="sxs-lookup"><span data-stu-id="64838-161">Handling Events</span></span>  
 <span data-ttu-id="64838-162">重要的兩個事件`StackView`控制項正確運作。</span><span class="sxs-lookup"><span data-stu-id="64838-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="64838-163">處理<xref:System.Windows.Forms.UserControl.Load>正確放置控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="64838-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="64838-164">處理<xref:System.Windows.Forms.ToolStripItem.Click>每個事件<xref:System.Windows.Forms.ToolStripButton>以便`StackView`控制狀態行為類似於<xref:System.Windows.Forms.RadioButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="64838-165">若要處理事件</span><span class="sxs-lookup"><span data-stu-id="64838-165">To handle events</span></span>  
  
1.  <span data-ttu-id="64838-166">在 Windows Form 設計工具中，選取 `StackView`控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="64838-167">在**屬性**視窗中，按一下 **事件**。</span><span class="sxs-lookup"><span data-stu-id="64838-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="64838-168">按兩下 Load 事件，以產生`StackView_Load`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64838-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="64838-169">在 `StackView_Load` 事件處理常式中，複製並貼入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="64838-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="64838-170">在 Windows Form 設計工具中，選取 `mailStackButton`控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="64838-171">在**屬性**視窗中，按一下 **事件**。</span><span class="sxs-lookup"><span data-stu-id="64838-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="64838-172">按兩下 Click 事件。</span><span class="sxs-lookup"><span data-stu-id="64838-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="64838-173">Windows Form 設計工具會產生`mailStackButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64838-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="64838-174">重新命名`mailStackButton_Click`事件處理常式來`stackButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="64838-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="64838-175">如需詳細資訊，請參閱[如何： 重新命名識別項 (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c)。</span><span class="sxs-lookup"><span data-stu-id="64838-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="64838-176">插入下列程式碼`stackButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64838-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="64838-177">在 Windows Form 設計工具中，選取 `calendarStackButton`控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="64838-178">在**屬性**視窗中，若要將 Click 事件`stackButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64838-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="64838-179">重複步驟 10 和 11 for`contactsStackButton`和`tasksStackButton`控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="64838-180">定義圖示</span><span class="sxs-lookup"><span data-stu-id="64838-180">Defining Icons</span></span>  
 <span data-ttu-id="64838-181">每個`StackView`按鈕具有相關聯的圖示。</span><span class="sxs-lookup"><span data-stu-id="64838-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="64838-182">為了方便起見，每個圖示表示為 Base64 編碼的字串，這會還原序列化前<xref:System.Drawing.Bitmap>從它所建立。</span><span class="sxs-lookup"><span data-stu-id="64838-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="64838-183">在生產環境中，您將點陣圖資料儲存為資源，並圖示會出現在 Windows Form 設計工具。</span><span class="sxs-lookup"><span data-stu-id="64838-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="64838-184">如需詳細資訊，請參閱[如何： 加入背景影像加入 Windows Form](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff)。</span><span class="sxs-lookup"><span data-stu-id="64838-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="64838-185">若要定義圖示</span><span class="sxs-lookup"><span data-stu-id="64838-185">To define icons</span></span>  
  
1.  <span data-ttu-id="64838-186">在程式碼編輯器中，插入下列程式碼`StackView`類別定義。</span><span class="sxs-lookup"><span data-stu-id="64838-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="64838-187">這個程式碼初始化的點陣圖<xref:System.Windows.Forms.ToolStripButton>圖示。</span><span class="sxs-lookup"><span data-stu-id="64838-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="64838-188">將呼叫加入`InitializeImages`方法中的`StackView`類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="64838-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="64838-189">實作自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="64838-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="64838-190">您可以自訂的大部分元素`StackView`控制我實作衍生自類別<xref:System.Windows.Forms.ToolStripRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="64838-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="64838-191">在此程序，您將實作<xref:System.Windows.Forms.ToolStripProfessionalRenderer>類別，自訂的底框，並且畫出漸層背景<xref:System.Windows.Forms.ToolStripButton>控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="64838-192">若要實作自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="64838-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="64838-193">插入下列程式碼`StackView`控制定義。</span><span class="sxs-lookup"><span data-stu-id="64838-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="64838-194">這是針對定義`StackRenderer`類別，它會覆寫<xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>， <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>，和<xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground>方法來產生自訂的外觀。</span><span class="sxs-lookup"><span data-stu-id="64838-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="64838-195">在`StackView`控制項的建構函式，建立的新執行個體`StackRenderer`類別，並指派至這個執行個體`stackStrip`控制項的<xref:System.Windows.Forms.ToolStrip.Renderer%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="64838-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="64838-196">測試 StackView 控制項</span><span class="sxs-lookup"><span data-stu-id="64838-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="64838-197">`StackView`控制項衍生自<xref:System.Windows.Forms.UserControl>類別。</span><span class="sxs-lookup"><span data-stu-id="64838-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="64838-198">因此，您可以測試具有控制項**UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="64838-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="64838-199">如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="64838-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="64838-200">若要測試 StackView 控制項</span><span class="sxs-lookup"><span data-stu-id="64838-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="64838-201">按 F5 以建置專案並開始**UserControl Test Container**。</span><span class="sxs-lookup"><span data-stu-id="64838-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="64838-202">將指標移的按鈕`StackView`控制項，然後再按一下按鈕，請參閱所選取之狀態的外觀。</span><span class="sxs-lookup"><span data-stu-id="64838-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="64838-203">後續步驟</span><span class="sxs-lookup"><span data-stu-id="64838-203">Next Steps</span></span>  
 <span data-ttu-id="64838-204">在本逐步解說中，您已建立的可重複使用的自訂用戶端控制項專業外觀的 Office XP 控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="64838-205">您可以使用<xref:System.Windows.Forms.ToolStrip>系列用於許多其他用途的控制項：</span><span class="sxs-lookup"><span data-stu-id="64838-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="64838-206">建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="64838-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="64838-207">如需詳細資訊，請參閱[ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="64838-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="64838-208">建立表單，以自動填入的標準功能表。</span><span class="sxs-lookup"><span data-stu-id="64838-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="64838-209">如需詳細資訊，請參閱[逐步解說： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="64838-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="64838-210">建立多個文件介面 (MDI) 表單上具有停駐<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="64838-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="64838-211">如需詳細資訊，請參閱[How to： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="64838-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64838-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64838-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="64838-213">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="64838-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="64838-214">操作說明：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="64838-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
