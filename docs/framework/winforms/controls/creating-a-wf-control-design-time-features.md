---
title: 逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: c8d04725a576c9e24a4b7d4aec1251516a8c544c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666235"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a><span data-ttu-id="f4497-102">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-102">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>

<span data-ttu-id="f4497-103">您可以撰寫相關聯的自訂設計工具來增強自訂控制項的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="f4497-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="f4497-104">本逐步解說將說明如何建立自訂控制項的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-104">This walkthrough illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="f4497-105">您將會執行`MarqueeControl`名`MarqueeControlRootDesigner`為的型別和相關聯的設計工具類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-105">You will implement a `MarqueeControl` type and an associated designer class, called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="f4497-106">`MarqueeControl`型別會執行類似劇院天棚的顯示, 具有動畫燈和閃爍的文字。</span><span class="sxs-lookup"><span data-stu-id="f4497-106">The `MarqueeControl` type implements a display similar to a theater marquee, with animated lights and flashing text.</span></span>

<span data-ttu-id="f4497-107">此控制項的設計工具會與設計環境互動, 以提供自訂的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="f4497-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="f4497-108">在自訂設計工具中, 您可以使用`MarqueeControl`動畫光源組合自訂的執行, 並在許多組合中使用閃爍的文字。</span><span class="sxs-lookup"><span data-stu-id="f4497-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="f4497-109">您可以在表單上使用群組控制項, 就像任何其他 Windows Forms 控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="f4497-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="f4497-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="f4497-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="f4497-111">建立專案</span><span class="sxs-lookup"><span data-stu-id="f4497-111">Creating the Project</span></span>

- <span data-ttu-id="f4497-112">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="f4497-112">Creating a Control Library Project</span></span>

- <span data-ttu-id="f4497-113">參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="f4497-113">Referencing the Custom Control Project</span></span>

- <span data-ttu-id="f4497-114">定義自訂控制項及其自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="f4497-114">Defining a Custom Control and Its Custom Designer</span></span>

- <span data-ttu-id="f4497-115">建立自訂控制項的實例</span><span class="sxs-lookup"><span data-stu-id="f4497-115">Creating an Instance of Your Custom Control</span></span>

- <span data-ttu-id="f4497-116">設定專案以進行設計階段的偵錯工具</span><span class="sxs-lookup"><span data-stu-id="f4497-116">Setting Up the Project for Design-Time Debugging</span></span>

- <span data-ttu-id="f4497-117">執行您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-117">Implementing Your Custom Control</span></span>

- <span data-ttu-id="f4497-118">建立自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-118">Creating a Child Control for Your Custom Control</span></span>

- <span data-ttu-id="f4497-119">建立 MarqueeBorder 子控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-119">Create the MarqueeBorder Child Control</span></span>

- <span data-ttu-id="f4497-120">建立自訂設計工具以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="f4497-120">Creating a Custom Designer to Shadow and Filter Properties</span></span>

- <span data-ttu-id="f4497-121">處理元件變更</span><span class="sxs-lookup"><span data-stu-id="f4497-121">Handling Component Changes</span></span>

- <span data-ttu-id="f4497-122">將設計工具動詞新增至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="f4497-122">Adding Designer Verbs to your Custom Designer</span></span>

- <span data-ttu-id="f4497-123">建立自訂 UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="f4497-123">Creating a Custom UITypeEditor</span></span>

- <span data-ttu-id="f4497-124">在設計工具中測試您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-124">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="f4497-125">當您完成時, 您的自訂控制項看起來會像下面這樣:</span><span class="sxs-lookup"><span data-stu-id="f4497-125">When you are finished, your custom control will look something like the following:</span></span>

![應用程式會顯示文字和 [開始] 和 [停止] 按鈕的提示。](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="f4497-127">如需完整的程式代碼清單[, 請參閱如何:建立會利用設計階段功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-127">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4497-128">必要條件</span><span class="sxs-lookup"><span data-stu-id="f4497-128">Prerequisites</span></span>

<span data-ttu-id="f4497-129">為了完成此逐步解說, 您需要 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f4497-129">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="f4497-130">建立專案</span><span class="sxs-lookup"><span data-stu-id="f4497-130">Creating the Project</span></span>

<span data-ttu-id="f4497-131">第一個步驟是建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-131">The first step is to create the application project.</span></span> <span data-ttu-id="f4497-132">您將使用此專案來建立裝載自訂控制項的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4497-132">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="f4497-133">開啟 Visual Studio 並建立名為 "MarqueeControlTest" 的 Windows Forms 應用程式  > 專案 ([檔案] [**新增** > ] [**專案** > ]**視覺效果C#** 或**Visual Basic**  > **傳統桌面** **Windows Forms 應用程式)。**  > </span><span class="sxs-lookup"><span data-stu-id="f4497-133">Open Visual Studio and create a Windows Forms Application project called "MarqueeControlTest" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="creating-a-control-library-project"></a><span data-ttu-id="f4497-134">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="f4497-134">Creating a Control Library Project</span></span>

<span data-ttu-id="f4497-135">下一個步驟是建立控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-135">The next step is to create the control library project.</span></span> <span data-ttu-id="f4497-136">您將建立新的自訂控制項及其對應的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-136">You will create a new custom control and its corresponding custom designer.</span></span>

### <a name="to-create-the-control-library-project"></a><span data-ttu-id="f4497-137">若要建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="f4497-137">To create the control library project</span></span>

1. <span data-ttu-id="f4497-138">將 Windows Forms 控制項程式庫專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="f4497-138">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="f4497-139">將專案命名為 "MarqueeControlLibrary"。</span><span class="sxs-lookup"><span data-stu-id="f4497-139">Name the project "MarqueeControlLibrary."</span></span>

2. <span data-ttu-id="f4497-140">使用**方案總管**, 根據您選擇的語言刪除名為 "UserControl1.cs" 或 "UserControl1" 的來源檔案, 以刪除專案的預設控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-140">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span> <span data-ttu-id="f4497-141">如需詳細資訊，請參閱[如何：移除、刪除和排除專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f4497-141">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="f4497-142">將新<xref:System.Windows.Forms.UserControl>專案加入`MarqueeControlLibrary`至專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-142">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-143">為新的來源檔案提供 "MarqueeControl" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="f4497-143">Give the new source file a base name of "MarqueeControl."</span></span>

4. <span data-ttu-id="f4497-144">使用**方案總管**, 在`MarqueeControlLibrary`專案中建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4497-144">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-145">如需詳細資訊，請參閱[如何：加入新的專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-145">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="f4497-146">將新資料夾命名為「設計」。</span><span class="sxs-lookup"><span data-stu-id="f4497-146">Name the new folder "Design."</span></span>

5. <span data-ttu-id="f4497-147">以滑鼠右鍵按一下 [**設計**] 資料夾, 並加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-147">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="f4497-148">將來源檔案的基底名稱指定為 "MarqueeControlRootDesigner"。</span><span class="sxs-lookup"><span data-stu-id="f4497-148">Give the source file a base name of "MarqueeControlRootDesigner."</span></span>

6. <span data-ttu-id="f4497-149">您必須使用來自 system.servicemodel 元件的類型, 因此請將此參考新增至`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-149">You will need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f4497-150">若要使用 System.object 元件, 您的專案必須以 .NET Framework 的完整版本為目標, 而不是 .NET Framework 的用戶端設定檔。</span><span class="sxs-lookup"><span data-stu-id="f4497-150">To use the System.Design assembly, your project must target the full version of the .NET Framework, not the .NET Framework Client Profile.</span></span> <span data-ttu-id="f4497-151">若要變更目標 framework, 請[參閱如何:以一個 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。</span><span class="sxs-lookup"><span data-stu-id="f4497-151">To change the target framework, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

## <a name="referencing-the-custom-control-project"></a><span data-ttu-id="f4497-152">參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="f4497-152">Referencing the Custom Control Project</span></span>

<span data-ttu-id="f4497-153">您將使用`MarqueeControlTest`專案來測試自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-153">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="f4497-154">當您將專案參考`MarqueeControlLibrary`加入元件時, 測試專案將會察覺自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-154">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

### <a name="to-reference-the-custom-control-project"></a><span data-ttu-id="f4497-155">若要參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="f4497-155">To reference the custom control project</span></span>

- <span data-ttu-id="f4497-156">在專案中, 將專案參考新增`MarqueeControlLibrary`至元件。 `MarqueeControlTest`</span><span class="sxs-lookup"><span data-stu-id="f4497-156">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="f4497-157">請務必使用 [**加入參考**] 對話方塊中的 [**專案**] 索引標籤, `MarqueeControlLibrary`而不是直接參考元件。</span><span class="sxs-lookup"><span data-stu-id="f4497-157">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="defining-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="f4497-158">定義自訂控制項及其自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="f4497-158">Defining a Custom Control and Its Custom Designer</span></span>
 <span data-ttu-id="f4497-159">您的<xref:System.Windows.Forms.UserControl>自訂控制項將衍生自類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-159">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="f4497-160">這可讓您的控制項包含其他控制項, 並讓您的控制項有很多的預設功能。</span><span class="sxs-lookup"><span data-stu-id="f4497-160">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

 <span data-ttu-id="f4497-161">您的自訂控制項將會有相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-161">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="f4497-162">這可讓您建立專為您的自訂控制項量身打造的獨特設計經驗。</span><span class="sxs-lookup"><span data-stu-id="f4497-162">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

 <span data-ttu-id="f4497-163">您可以使用<xref:System.ComponentModel.DesignerAttribute>類別, 將控制項與設計工具產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f4497-163">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="f4497-164">因為您正在開發自訂控制項的整個設計階段行為, 所以自訂設計工具會執行<xref:System.ComponentModel.Design.IRootDesigner>介面。</span><span class="sxs-lookup"><span data-stu-id="f4497-164">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="f4497-165">若要定義自訂控制項和其自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="f4497-165">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="f4497-166">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="f4497-166">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-167">在檔案的頂端, 匯入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-167">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="f4497-168">將加入<xref:System.ComponentModel.DesignerAttribute> `MarqueeControl`至類別宣告。</span><span class="sxs-lookup"><span data-stu-id="f4497-168">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="f4497-169">這會使自訂控制項與其設計工具產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f4497-169">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="f4497-170">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="f4497-170">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-171">在檔案的頂端, 匯入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-171">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="f4497-172">將的`MarqueeControlRootDesigner`宣告變更為繼承<xref:System.Windows.Forms.Design.DocumentDesigner>自類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-172">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="f4497-173">套用以指定設計工具與工具箱的互動。 <xref:System.ComponentModel.ToolboxItemFilterAttribute></span><span class="sxs-lookup"><span data-stu-id="f4497-173">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

     <span data-ttu-id="f4497-174">**注意**`MarqueeControlRootDesigner`類別的定義已包含在名為 "MarqueeControlLibrary" 的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="f4497-174">**Note** The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called "MarqueeControlLibrary.Design."</span></span> <span data-ttu-id="f4497-175">這個宣告會將設計工具放在保留給設計相關類型的特殊命名空間中。</span><span class="sxs-lookup"><span data-stu-id="f4497-175">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="f4497-176">定義`MarqueeControlRootDesigner`類別的「構造函式」。</span><span class="sxs-lookup"><span data-stu-id="f4497-176">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="f4497-177">在函式主體中插入語句。<xref:System.Diagnostics.Trace.WriteLine%2A></span><span class="sxs-lookup"><span data-stu-id="f4497-177">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="f4497-178">這在進行調試時很有用。</span><span class="sxs-lookup"><span data-stu-id="f4497-178">This will be useful for debugging purposes.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a><span data-ttu-id="f4497-179">建立自訂控制項的實例</span><span class="sxs-lookup"><span data-stu-id="f4497-179">Creating an Instance of Your Custom Control</span></span>
 <span data-ttu-id="f4497-180">若要觀察控制項的自訂設計階段行為, 您要將控制項的實例放在`MarqueeControlTest` project 的表單上。</span><span class="sxs-lookup"><span data-stu-id="f4497-180">To observe the custom design-time behavior of your control, you will place an instance of your control on the form in `MarqueeControlTest` project.</span></span>

### <a name="to-create-an-instance-of-your-custom-control"></a><span data-ttu-id="f4497-181">若要建立自訂控制項的實例</span><span class="sxs-lookup"><span data-stu-id="f4497-181">To create an instance of your custom control</span></span>

1. <span data-ttu-id="f4497-182">將新<xref:System.Windows.Forms.UserControl>專案加入`MarqueeControlTest`至專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-182">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="f4497-183">為新的來源檔案提供 "DemoMarqueeControl" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="f4497-183">Give the new source file a base name of "DemoMarqueeControl."</span></span>

2. <span data-ttu-id="f4497-184">在程式碼編輯器中開啟檔案。 `DemoMarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="f4497-184">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-185">在檔案的頂端, 匯入`MarqueeControlLibrary`命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-185">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. <span data-ttu-id="f4497-186">將的`DemoMarqueeControl`宣告變更為繼承`MarqueeControl`自類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-186">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

2. <span data-ttu-id="f4497-187">建置專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-187">Build the project.</span></span>

3. <span data-ttu-id="f4497-188">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="f4497-188">Open `Form1` in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="f4497-189">在 [**工具箱**] 中尋找 [ **MarqueeControlTest 元件**] 索引標籤, 並加以開啟。</span><span class="sxs-lookup"><span data-stu-id="f4497-189">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="f4497-190">將從 [工具箱] 拖曳至表單。 `DemoMarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="f4497-190">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="f4497-191">建置專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-191">Build the project.</span></span>

## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f4497-192">設定專案以進行設計階段的偵錯工具</span><span class="sxs-lookup"><span data-stu-id="f4497-192">Setting Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="f4497-193">當您開發自訂的設計階段體驗時, 必須先將控制項和元件進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-193">When you are developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="f4497-194">有一種簡單的方式可設定您的專案, 以允許在設計階段進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-194">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="f4497-195">如需詳細資訊，請參閱[逐步解說：在設計階段時](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md), 對自訂 Windows Forms 控制項進行調試。</span><span class="sxs-lookup"><span data-stu-id="f4497-195">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f4497-196">設定專案進行設計階段的偵錯工具</span><span class="sxs-lookup"><span data-stu-id="f4497-196">To set up the project for design-time debugging</span></span>

1. <span data-ttu-id="f4497-197">以滑鼠右鍵按一下`MarqueeControlLibrary`專案, 然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="f4497-197">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="f4497-198">在 [MarqueeControlLibrary 屬性頁] 對話方塊中, 選取 [ **Debug** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="f4497-198">In the "MarqueeControlLibrary Property Pages" dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="f4497-199">在 [**起始動作**] 區段中, 選取 [**啟動外部程式**]。</span><span class="sxs-lookup"><span data-stu-id="f4497-199">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="f4497-200">您將會 Visual Studio 的個別實例進行偵錯工具, 因此請按一下省略號![([](./media/visual-studio-ellipsis-button.png)Visual Studio 屬性視窗中的省略號按鈕 (...)] 按鈕, 以流覽 Visual Studio IDE。</span><span class="sxs-lookup"><span data-stu-id="f4497-200">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="f4497-201">可執行檔的名稱為 devenv, 如果您安裝到預設位置, 其路徑為%programfiles%\Microsoft Visual Studio 9.0 \ Common7\IDE\devenv.exe。</span><span class="sxs-lookup"><span data-stu-id="f4497-201">The name of the executable file is devenv.exe, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

4. <span data-ttu-id="f4497-202">按一下 [確定] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f4497-202">Click OK to close the dialog box.</span></span>

5. <span data-ttu-id="f4497-203">以滑鼠右鍵按一下`MarqueeControlLibrary`專案, 然後選取 [設定為啟始專案] 以啟用此調試設定。</span><span class="sxs-lookup"><span data-stu-id="f4497-203">Right-click the `MarqueeControlLibrary` project and select "Set as StartUp Project" to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="f4497-204">檢查點</span><span class="sxs-lookup"><span data-stu-id="f4497-204">Checkpoint</span></span>

<span data-ttu-id="f4497-205">您現在已準備好要開始進行自訂控制項的設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="f4497-205">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="f4497-206">一旦確定已正確設定偵錯工具環境, 就會測試自訂控制項和自訂設計工具之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f4497-206">Once you have determined that the debugging environment is set up correctly, you will test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="f4497-207">測試調試環境和設計工具關聯</span><span class="sxs-lookup"><span data-stu-id="f4497-207">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="f4497-208">在程式**代碼編輯器**中開啟<xref:System.Diagnostics.Trace.WriteLine%2A> 原始程式檔,並將中斷點放在語句上。`MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="f4497-208">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="f4497-209">按 F5 啟動「調試」會話。</span><span class="sxs-lookup"><span data-stu-id="f4497-209">Press F5 to start the debugging session.</span></span> <span data-ttu-id="f4497-210">請注意, 會建立新的 Visual Studio 實例。</span><span class="sxs-lookup"><span data-stu-id="f4497-210">Note that a new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="f4497-211">在 Visual Studio 的新實例中, 開啟 "MarqueeControlTest" 解決方案。</span><span class="sxs-lookup"><span data-stu-id="f4497-211">In the new instance of Visual Studio, open the "MarqueeControlTest" solution.</span></span> <span data-ttu-id="f4497-212">您可以從 [檔案] 功能表選取 [**最近使用**的專案], 輕鬆地找到解決方案。</span><span class="sxs-lookup"><span data-stu-id="f4497-212">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="f4497-213">"MarqueeControlTest" 方案檔會列為最近使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="f4497-213">The "MarqueeControlTest.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="f4497-214">`DemoMarqueeControl`在設計工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="f4497-214">Open the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="f4497-215">請注意, Visual Studio 的偵錯工具實例會取得焦點, 而執行則會在您的中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="f4497-215">Note that the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="f4497-216">按 F5 繼續執行調試會話。</span><span class="sxs-lookup"><span data-stu-id="f4497-216">Press F5 to continue the debugging session.</span></span>

<span data-ttu-id="f4497-217">此時, 所有專案都已準備就緒, 可供您開發和偵錯工具的自訂控制項和其相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-217">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="f4497-218">本逐步解說的其餘部分將著重于如何執行控制項和設計工具的功能詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f4497-218">The remainder of this walkthrough will concentrate on the details of implementing features of the control and the designer.</span></span>

## <a name="implementing-your-custom-control"></a><span data-ttu-id="f4497-219">執行您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-219">Implementing Your Custom Control</span></span>

<span data-ttu-id="f4497-220">`MarqueeControl` 是,而且有<xref:System.Windows.Forms.UserControl>一些自訂專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-220">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="f4497-221">它會公開兩個`Start`方法:, 這會啟動「天棚`Stop`」動畫, 而會停止動畫。</span><span class="sxs-lookup"><span data-stu-id="f4497-221">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="f4497-222">`Stop` `Start` `IMarqueeWidget` `StartMarquee`因為包含可實作為介面的子控制項, 並列舉每個子控制項並分別在每個子控制項上呼叫和`StopMarquee`方法 `MarqueeControl`該執行的。 `IMarqueeWidget`</span><span class="sxs-lookup"><span data-stu-id="f4497-222">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="f4497-223">`MarqueeBorder`和`MarqueeControl` <xref:System.Windows.Forms.Control.PerformLayout%2A> <xref:System.Windows.Forms.Control.OnLayout%2A>控制項的外觀取決於版面配置, 因此會覆寫方法, 並呼叫此類型的子控制項。 `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="f4497-223">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="f4497-224">這是`MarqueeControl`自訂的範圍。</span><span class="sxs-lookup"><span data-stu-id="f4497-224">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="f4497-225">執行時間功能是`MarqueeBorder`由和`MarqueeText`控制項所實, 而設計階段`MarqueeBorderDesigner`功能則是由和`MarqueeControlRootDesigner`類別來執行。</span><span class="sxs-lookup"><span data-stu-id="f4497-225">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="f4497-226">若要執行您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-226">To implement your custom control</span></span>

1. <span data-ttu-id="f4497-227">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="f4497-227">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-228">`Start`執行和`Stop`方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-228">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="f4497-229">覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-229">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a><span data-ttu-id="f4497-230">建立自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-230">Creating a Child Control for Your Custom Control</span></span>

<span data-ttu-id="f4497-231">會裝載兩種類型的子控制項`MarqueeBorder` : 控制項和`MarqueeText`控制項。 `MarqueeControl`</span><span class="sxs-lookup"><span data-stu-id="f4497-231">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="f4497-232">`MarqueeBorder`：此控制項會在其邊緣周圍繪製「光源」的框線。</span><span class="sxs-lookup"><span data-stu-id="f4497-232">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="f4497-233">燈光會依序閃爍, 因此它們看起來會在框線周圍移動。</span><span class="sxs-lookup"><span data-stu-id="f4497-233">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="f4497-234">以稱為`UpdatePeriod`的屬性控制燈閃爍的速度。</span><span class="sxs-lookup"><span data-stu-id="f4497-234">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="f4497-235">其他幾個自訂屬性會決定控制面板的其他層面。</span><span class="sxs-lookup"><span data-stu-id="f4497-235">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="f4497-236">有兩種方法`StartMarquee` ( `StopMarquee`稱為和) 會控制動畫啟動和停止的時間。</span><span class="sxs-lookup"><span data-stu-id="f4497-236">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="f4497-237">`MarqueeText`：此控制項會繪製閃爍的字串。</span><span class="sxs-lookup"><span data-stu-id="f4497-237">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="f4497-238">就像`UpdatePeriod`控制項一樣, 文字閃爍的速度是由屬性所控制。 `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="f4497-238">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="f4497-239">控制項也具有`StopMarquee`與`StartMarquee` 控制項`MarqueeBorder`共通的和方法。 `MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="f4497-239">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="f4497-240">在設計階段, `MarqueeControlRootDesigner`可讓您將這兩種控制項類型加入`MarqueeControl`任何組合中。</span><span class="sxs-lookup"><span data-stu-id="f4497-240">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="f4497-241">這兩個控制項的一般功能會分解成稱為`IMarqueeWidget`的介面。</span><span class="sxs-lookup"><span data-stu-id="f4497-241">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="f4497-242">這可讓`MarqueeControl`探索任何與天棚相關的子控制項, 並提供特殊的處理方式。</span><span class="sxs-lookup"><span data-stu-id="f4497-242">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="f4497-243">若要執行定期動畫功能, 您將會<xref:System.ComponentModel.BackgroundWorker>使用命名空間<xref:System.ComponentModel?displayProperty=nameWithType>中的物件。</span><span class="sxs-lookup"><span data-stu-id="f4497-243">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f4497-244">您可以使用<xref:System.Windows.Forms.Timer>物件, 但當有`IMarqueeWidget`許多物件存在時, 單一 UI 執行緒可能無法跟上動畫。</span><span class="sxs-lookup"><span data-stu-id="f4497-244">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="f4497-245">若要建立自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-245">To create a child control for your custom control</span></span>

1. <span data-ttu-id="f4497-246">將新的類別專案加入至`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-246">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-247">為新的來源檔案提供 "IMarqueeWidget" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="f4497-247">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="f4497-248">在程式**代碼編輯器**中開啟`class` `interface`原始程式檔,並將宣告`IMarqueeWidget`從變更為:</span><span class="sxs-lookup"><span data-stu-id="f4497-248">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="f4497-249">將下列程式碼新增至`IMarqueeWidget`介面, 以公開兩個方法, 以及可操作字幕動畫的屬性:</span><span class="sxs-lookup"><span data-stu-id="f4497-249">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="f4497-250">將新的**自訂控制項**專案加入`MarqueeControlLibrary`至專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-250">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-251">為新的來源檔案提供 "MarqueeText" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="f4497-251">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="f4497-252">將元件從 [工具箱] 拖曳至`MarqueeText`您的控制項。 <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="f4497-252">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="f4497-253">此元件可讓`MarqueeText`控制項以非同步方式更新其本身。</span><span class="sxs-lookup"><span data-stu-id="f4497-253">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="f4497-254">在屬性視窗<xref:System.ComponentModel.BackgroundWorker>中, 將元件的`WorkerReportsProgress`和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="f4497-254">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="f4497-255">這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件定期<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 並取消非同步更新。</span><span class="sxs-lookup"><span data-stu-id="f4497-255">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="f4497-256">如需詳細資訊, 請參閱[BackgroundWorker 元件](backgroundworker-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f4497-256">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="f4497-257">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeText`</span><span class="sxs-lookup"><span data-stu-id="f4497-257">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-258">在檔案的頂端, 匯入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-258">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="f4497-259">將的`MarqueeText`宣告變更為繼承自<xref:System.Windows.Forms.Label>和以執行`IMarqueeWidget`介面:</span><span class="sxs-lookup"><span data-stu-id="f4497-259">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="f4497-260">宣告對應至已公開屬性的執行個體變數, 並在此函式中將它們初始化。</span><span class="sxs-lookup"><span data-stu-id="f4497-260">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="f4497-261">欄位會決定是否要在`LightColor`屬性所指定的色彩中繪製文字。 `isLit`</span><span class="sxs-lookup"><span data-stu-id="f4497-261">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="f4497-262">實作 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="f4497-262">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="f4497-263">`StartMarquee` <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法會叫用元件的和方法, 以啟動和停止動畫。 <xref:System.ComponentModel.BackgroundWorker> `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="f4497-263">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="f4497-264"><xref:System.ComponentModel.CategoryAttribute.Category%2A> 和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性會套用至屬性,因此它會出現在稱為「天棚」之屬性視窗的自訂區段中。`UpdatePeriod`</span><span class="sxs-lookup"><span data-stu-id="f4497-264">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="f4497-265">執行屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="f4497-265">Implement the property accessors.</span></span> <span data-ttu-id="f4497-266">您會向用戶端公開兩個`LightColor`屬性`DarkColor`: 和。</span><span class="sxs-lookup"><span data-stu-id="f4497-266">You will expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="f4497-267"><xref:System.ComponentModel.CategoryAttribute.Category%2A> 和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性會套用至這些屬性, 因此屬性會出現在屬性視窗的自訂區段中, 稱為「天棚」。</span><span class="sxs-lookup"><span data-stu-id="f4497-267">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="f4497-268">執行<xref:System.ComponentModel.BackgroundWorker> 元件和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的處理常式。 <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="f4497-268">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="f4497-269">事件處理常式會在睡眠時`UpdatePeriod`進入指定的毫秒數, 然後<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 直到您的程式碼藉由<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>呼叫停止動畫為止。 <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="f4497-269">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="f4497-270"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式會將文字切換成淺與深的狀態, 以提供閃爍的外觀。</span><span class="sxs-lookup"><span data-stu-id="f4497-270">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="f4497-271">覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法以啟用動畫。</span><span class="sxs-lookup"><span data-stu-id="f4497-271">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="f4497-272">按 F6 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="f4497-272">Press F6 to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="f4497-273">建立 MarqueeBorder 子控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-273">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="f4497-274">`MarqueeBorder` 控制項`MarqueeText`比控制項稍微複雜一點。</span><span class="sxs-lookup"><span data-stu-id="f4497-274">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="f4497-275">其中包含更多屬性, 而<xref:System.Windows.Forms.Control.OnPaint%2A>方法中的動畫則比較複雜。</span><span class="sxs-lookup"><span data-stu-id="f4497-275">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="f4497-276">就原則而言, 這與`MarqueeText`控制項非常類似。</span><span class="sxs-lookup"><span data-stu-id="f4497-276">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="f4497-277">因為控制項可以有子控制項, 所以需要<xref:System.Windows.Forms.Control.Layout>留意事件。 `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="f4497-277">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="f4497-278">若要建立 MarqueeBorder 控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-278">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="f4497-279">將新的**自訂控制項**專案加入`MarqueeControlLibrary`至專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-279">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-280">為新的來源檔案提供 "MarqueeBorder" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="f4497-280">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="f4497-281">將元件從 [工具箱] 拖曳至`MarqueeBorder`您的控制項。 <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="f4497-281">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="f4497-282">此元件可讓`MarqueeBorder`控制項以非同步方式更新其本身。</span><span class="sxs-lookup"><span data-stu-id="f4497-282">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="f4497-283">在屬性視窗<xref:System.ComponentModel.BackgroundWorker>中, 將元件的`WorkerReportsProgress`和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="f4497-283">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="f4497-284">這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件定期<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 並取消非同步更新。</span><span class="sxs-lookup"><span data-stu-id="f4497-284">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="f4497-285">如需詳細資訊, 請參閱[BackgroundWorker 元件](backgroundworker-component.md)。</span><span class="sxs-lookup"><span data-stu-id="f4497-285">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="f4497-286">在 屬性視窗中, 按一下 事件 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f4497-286">In the Properties window, click the Events button.</span></span> <span data-ttu-id="f4497-287">附加和<xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="f4497-287">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="f4497-288">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="f4497-288">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-289">在檔案的頂端, 匯入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-289">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="f4497-290">將的`MarqueeBorder`宣告變更為繼承自<xref:System.Windows.Forms.Panel>和, 以執行`IMarqueeWidget`介面。</span><span class="sxs-lookup"><span data-stu-id="f4497-290">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="f4497-291">宣告兩個用於管理`MarqueeBorder`控制項狀態的列舉: `MarqueeSpinDirection`, 這會決定光源周圍「旋轉」的方向, 以及`MarqueeLightShape`決定光源的形狀 (方形或圓形)。</span><span class="sxs-lookup"><span data-stu-id="f4497-291">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="f4497-292">將這些宣告放在`MarqueeBorder`類別宣告之前。</span><span class="sxs-lookup"><span data-stu-id="f4497-292">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="f4497-293">宣告對應至已公開屬性的執行個體變數, 並在此函式中將它們初始化。</span><span class="sxs-lookup"><span data-stu-id="f4497-293">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="f4497-294">實作 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="f4497-294">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="f4497-295">`StartMarquee` <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法會叫用元件的和方法, 以啟動和停止動畫。 <xref:System.ComponentModel.BackgroundWorker> `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="f4497-295">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="f4497-296">因為控制項可以包含子控制項`StartMarquee` , 所以方法會列舉所有的子控制項, 並在所執行`IMarqueeWidget`的上呼叫。 `StartMarquee` `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="f4497-296">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="f4497-297">`StopMarquee`方法具有類似的執行方式。</span><span class="sxs-lookup"><span data-stu-id="f4497-297">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="f4497-298">執行屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="f4497-298">Implement the property accessors.</span></span> <span data-ttu-id="f4497-299">`MarqueeBorder`控制項有數個屬性可控制其外觀。</span><span class="sxs-lookup"><span data-stu-id="f4497-299">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="f4497-300">執行<xref:System.ComponentModel.BackgroundWorker> 元件和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的處理常式。 <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="f4497-300">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="f4497-301">事件處理常式會在睡眠時`UpdatePeriod`進入指定的毫秒數, 然後<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 直到您的程式碼藉由<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>呼叫停止動畫為止。 <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="f4497-301">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="f4497-302">事件處理常式會遞增「基底」光源的位置, 也就是判斷出另一個光源的淺色/深色狀態, 然後<xref:System.Windows.Forms.Control.Refresh%2A>呼叫方法, 讓控制項自行重新繪製。 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged></span><span class="sxs-lookup"><span data-stu-id="f4497-302">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="f4497-303">執行 helper 方法`IsLit`和`DrawLight`。</span><span class="sxs-lookup"><span data-stu-id="f4497-303">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="f4497-304">`IsLit`方法會決定指定位置的光線色彩。</span><span class="sxs-lookup"><span data-stu-id="f4497-304">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="f4497-305">「亮」的燈是以`LightColor`屬性所指定的色彩繪製, 而「深色」則是以`DarkColor`屬性所指定的色彩繪製。</span><span class="sxs-lookup"><span data-stu-id="f4497-305">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="f4497-306">`DrawLight`方法會使用適當的色彩、形狀和位置繪製一個光線。</span><span class="sxs-lookup"><span data-stu-id="f4497-306">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="f4497-307">覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>和方法。 <xref:System.Windows.Forms.Control.OnLayout%2A></span><span class="sxs-lookup"><span data-stu-id="f4497-307">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="f4497-308">方法會沿著`MarqueeBorder`控制項的邊緣繪製光源。 <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="f4497-308">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="f4497-309">因為方法取決於`MarqueeBorder`控制項的維度, 所以每當配置變更時, 您都必須呼叫它。 <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="f4497-309">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="f4497-310">若要達到此目的<xref:System.Windows.Forms.Control.OnLayout%2A> , 請<xref:System.Windows.Forms.Control.Refresh%2A>覆寫並呼叫。</span><span class="sxs-lookup"><span data-stu-id="f4497-310">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="f4497-311">建立自訂設計工具以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="f4497-311">Creating a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="f4497-312">`MarqueeControlRootDesigner`類別會提供根設計工具的實作為。</span><span class="sxs-lookup"><span data-stu-id="f4497-312">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="f4497-313">除了在上`MarqueeControl`運作的這個設計工具之外, 您還需要一個`MarqueeBorder`與控制項特別相關的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="f4497-313">In addition to this designer, which operates on the `MarqueeControl`, you will need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="f4497-314">這個設計工具會提供自訂的根設計工具內容中適用的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="f4497-314">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="f4497-315">具體而言, `MarqueeBorderDesigner`會「陰影」並篩選`MarqueeBorder`控制項上的特定屬性, 以變更其與設計環境的互動。</span><span class="sxs-lookup"><span data-stu-id="f4497-315">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="f4497-316">攔截元件屬性存取子的呼叫稱為「遮蔽」。</span><span class="sxs-lookup"><span data-stu-id="f4497-316">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="f4497-317">它可讓設計工具追蹤使用者所設定的值, 並選擇性地將該值傳遞至所設計的元件。</span><span class="sxs-lookup"><span data-stu-id="f4497-317">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="f4497-318">在此範例中, <xref:System.Windows.Forms.Control.Visible%2A>和<xref:System.Windows.Forms.Control.Enabled%2A>屬性`MarqueeBorderDesigner`會由遮蔽`MarqueeBorder` , 這可防止使用者在設計階段期間隱藏或停用控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-318">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="f4497-319">設計工具也可以加入和移除屬性。</span><span class="sxs-lookup"><span data-stu-id="f4497-319">Designers can also add and remove properties.</span></span> <span data-ttu-id="f4497-320">在此範例中, <xref:System.Windows.Forms.Control.Padding%2A>會在設計階段移除屬性, `MarqueeBorder`因為控制項會根據`LightSize`屬性所指定的光源大小, 以程式設計方式設定填補。</span><span class="sxs-lookup"><span data-stu-id="f4497-320">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="f4497-321">的基類`MarqueeBorderDesigner`是<xref:System.ComponentModel.Design.ComponentDesigner>, 其具有可在設計階段變更控制項所公開之屬性、屬性和事件的方法:</span><span class="sxs-lookup"><span data-stu-id="f4497-321">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="f4497-322">使用這些方法變更元件的公用介面時, 您必須遵循下列規則:</span><span class="sxs-lookup"><span data-stu-id="f4497-322">When changing the public interface of a component using these methods, you must follow these rules:</span></span>

- <span data-ttu-id="f4497-323">僅新增或移除方法中`PreFilter`的專案</span><span class="sxs-lookup"><span data-stu-id="f4497-323">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="f4497-324">只修改方法中的`PostFilter`現有專案</span><span class="sxs-lookup"><span data-stu-id="f4497-324">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="f4497-325">一律在`PreFilter`方法中先呼叫基底實作為</span><span class="sxs-lookup"><span data-stu-id="f4497-325">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="f4497-326">一律呼叫`PostFilter`方法中的最後一個基底執行</span><span class="sxs-lookup"><span data-stu-id="f4497-326">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="f4497-327">遵守這些規則可確保設計階段環境中的所有設計工具都能一致地看到所有設計的元件。</span><span class="sxs-lookup"><span data-stu-id="f4497-327">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="f4497-328"><xref:System.ComponentModel.Design.ComponentDesigner>類別提供用來管理陰影屬性值的字典, 讓您不需要建立特定的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="f4497-328">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="f4497-329">若要建立自訂設計工具以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="f4497-329">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="f4497-330">以滑鼠右鍵按一下 [**設計**] 資料夾, 並加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-330">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="f4497-331">將來源檔案的基底名稱指定為 "MarqueeBorderDesigner"。</span><span class="sxs-lookup"><span data-stu-id="f4497-331">Give the source file a base name of "MarqueeBorderDesigner."</span></span>

2. <span data-ttu-id="f4497-332">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeBorderDesigner`</span><span class="sxs-lookup"><span data-stu-id="f4497-332">Open the `MarqueeBorderDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-333">在檔案的頂端, 匯入下列命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-333">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="f4497-334">將的`MarqueeBorderDesigner`宣告變更為繼承自<xref:System.Windows.Forms.Design.ParentControlDesigner>。</span><span class="sxs-lookup"><span data-stu-id="f4497-334">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="f4497-335">因為控制項可以包含子控制項, `MarqueeBorderDesigner`所以會繼承<xref:System.Windows.Forms.Design.ParentControlDesigner>自, 以處理父子式互動。 `MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="f4497-335">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="f4497-336">覆寫的基底<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>執行。</span><span class="sxs-lookup"><span data-stu-id="f4497-336">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="f4497-337">實作 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="f4497-337">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="f4497-338">這些執行會遮蔽控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4497-338">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a><span data-ttu-id="f4497-339">處理元件變更</span><span class="sxs-lookup"><span data-stu-id="f4497-339">Handling Component Changes</span></span>
 <span data-ttu-id="f4497-340">類別會為您`MarqueeControl`的實例提供自訂的設計階段體驗。 `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="f4497-340">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="f4497-341">大部分的設計階段功能都是繼承自<xref:System.Windows.Forms.Design.DocumentDesigner>類別, 您的程式碼將會執行兩個特定的自訂: 處理元件變更, 以及加入設計工具動詞。</span><span class="sxs-lookup"><span data-stu-id="f4497-341">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class; your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

 <span data-ttu-id="f4497-342">當使用者設計其`MarqueeControl`實例時, 您的根設計工具會追蹤`MarqueeControl`和其子控制項的變更。</span><span class="sxs-lookup"><span data-stu-id="f4497-342">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="f4497-343">設計階段環境提供便利的服務, <xref:System.ComponentModel.Design.IComponentChangeService>可用於追蹤元件狀態的變更。</span><span class="sxs-lookup"><span data-stu-id="f4497-343">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

 <span data-ttu-id="f4497-344">您可以使用<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>方法來查詢環境, 以取得此服務的參考。</span><span class="sxs-lookup"><span data-stu-id="f4497-344">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="f4497-345">如果查詢成功, 您的設計工具可以附加<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>事件的處理常式, 並執行在設計階段維持一致狀態所需的任何工作。</span><span class="sxs-lookup"><span data-stu-id="f4497-345">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

 <span data-ttu-id="f4497-346">在`MarqueeControlRootDesigner`類別的案例中, 您將會在所<xref:System.Windows.Forms.Control.Refresh%2A>包含的`MarqueeControl`每`IMarqueeWidget`個物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-346">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="f4497-347">這會讓`IMarqueeWidget`物件在屬性 (如其父系的<xref:System.Windows.Forms.Control.Size%2A> ) 變更時, 適當地重新繪製本身。</span><span class="sxs-lookup"><span data-stu-id="f4497-347">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="f4497-348">若要處理元件變更</span><span class="sxs-lookup"><span data-stu-id="f4497-348">To handle component changes</span></span>

1. <span data-ttu-id="f4497-349">在程式**代碼編輯器**中開啟<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 原始程式檔,並覆寫方法。`MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="f4497-349">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="f4497-350">呼叫的基底實<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>作為, 並查詢<xref:System.ComponentModel.Design.IComponentChangeService>的。</span><span class="sxs-lookup"><span data-stu-id="f4497-350">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="f4497-351"><xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>執行事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f4497-351">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="f4497-352">測試傳送元件的類型, 如果它是`IMarqueeWidget`, 請呼叫其<xref:System.Windows.Forms.Control.Refresh%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-352">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="f4497-353">將設計工具動詞新增至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="f4497-353">Adding Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="f4497-354">設計工具動詞是連結至事件處理常式的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="f4497-354">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="f4497-355">設計工具動詞會在設計階段加入至元件的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="f4497-355">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="f4497-356">如需詳細資訊，請參閱 <xref:System.ComponentModel.Design.DesignerVerb>。</span><span class="sxs-lookup"><span data-stu-id="f4497-356">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="f4497-357">您會在設計工具中加入兩個設計工具動詞:**執行測試**並**停止測試**。</span><span class="sxs-lookup"><span data-stu-id="f4497-357">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="f4497-358">這些動詞可讓您`MarqueeControl`在設計階段時, 查看的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="f4497-358">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="f4497-359">這些動詞將會新增至`MarqueeControlRootDesigner`。</span><span class="sxs-lookup"><span data-stu-id="f4497-359">These verbs will be added to the `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="f4497-360">叫用**執行測試**時, 動詞事件處理常式會呼叫上`StartMarquee` `MarqueeControl`的方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-360">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="f4497-361">叫用**停止測試**時, 動詞事件處理常式會呼叫上`StopMarquee` `MarqueeControl`的方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-361">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="f4497-362">`StartMarquee`和`IMarqueeWidget` `IMarqueeWidget`方法的實作為在所包含的控制項上呼叫這些方法, 因此任何包含的控制項也會參與測試。 `StopMarquee`</span><span class="sxs-lookup"><span data-stu-id="f4497-362">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="f4497-363">將設計工具動詞新增至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="f4497-363">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="f4497-364">在類別中, 新增名為`OnVerbRunTest`和`OnVerbStopTest`的事件處理常式。 `MarqueeControlRootDesigner`</span><span class="sxs-lookup"><span data-stu-id="f4497-364">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="f4497-365">將這些事件處理常式連接至其對應的設計工具動詞。</span><span class="sxs-lookup"><span data-stu-id="f4497-365">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="f4497-366">`MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection>從其基類繼承。</span><span class="sxs-lookup"><span data-stu-id="f4497-366">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="f4497-367">您將建立兩個<xref:System.ComponentModel.Design.DesignerVerb>新的<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>物件, 並在方法中將它們加入此集合。</span><span class="sxs-lookup"><span data-stu-id="f4497-367">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a><span data-ttu-id="f4497-368">建立自訂 UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="f4497-368">Creating a Custom UITypeEditor</span></span>

<span data-ttu-id="f4497-369">當您為使用者建立自訂的設計階段體驗時, 通常需要建立與屬性視窗的自訂互動。</span><span class="sxs-lookup"><span data-stu-id="f4497-369">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="f4497-370">您可以藉由建立來完成<xref:System.Drawing.Design.UITypeEditor>這項工作。</span><span class="sxs-lookup"><span data-stu-id="f4497-370">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span> <span data-ttu-id="f4497-371">如需詳細資訊，請參閱[如何：建立 UI 類型編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="f4497-371">For more information, see [How to: Create a UI Type Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span></span>

<span data-ttu-id="f4497-372">`MarqueeBorder`控制項會在屬性視窗中公開數個屬性。</span><span class="sxs-lookup"><span data-stu-id="f4497-372">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="f4497-373">這些屬性`MarqueeSpinDirection` `MarqueeLightShape`的其中兩個是以列舉表示。</span><span class="sxs-lookup"><span data-stu-id="f4497-373">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="f4497-374">為了說明 UI 類型編輯器的用法, `MarqueeLightShape`屬性會有相關聯<xref:System.Drawing.Design.UITypeEditor>的類別。</span><span class="sxs-lookup"><span data-stu-id="f4497-374">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="f4497-375">若要建立自訂 UI 類型編輯器</span><span class="sxs-lookup"><span data-stu-id="f4497-375">To create a custom UI type editor</span></span>

1. <span data-ttu-id="f4497-376">在程式**代碼編輯器**中開啟原始程式檔。`MarqueeBorder`</span><span class="sxs-lookup"><span data-stu-id="f4497-376">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="f4497-377">在`MarqueeBorder`類別的定義中, 宣告衍生自<xref:System.Drawing.Design.UITypeEditor>的類別`LightShapeEditor` (稱為)。</span><span class="sxs-lookup"><span data-stu-id="f4497-377">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="f4497-378">宣告名<xref:System.Windows.Forms.Design.IWindowsFormsEditorService> `editorService`為的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="f4497-378">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="f4497-379">覆寫 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-379">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="f4497-380">這個執行<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>會傳回, 告訴設計環境如何`LightShapeEditor`顯示。</span><span class="sxs-lookup"><span data-stu-id="f4497-380">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="f4497-381">覆寫 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-381">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="f4497-382">此實作為查詢<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>物件的設計環境。</span><span class="sxs-lookup"><span data-stu-id="f4497-382">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="f4497-383">如果成功, 則會建立`LightShapeSelectionControl`。</span><span class="sxs-lookup"><span data-stu-id="f4497-383">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="f4497-384">會叫用`LightShapeEditor`方法來啟動 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f4497-384">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="f4497-385">這個調用的傳回值會傳回到設計環境。</span><span class="sxs-lookup"><span data-stu-id="f4497-385">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="f4497-386">建立自訂 UITypeEditor 的 View 控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-386">Creating a View Control for your Custom UITypeEditor</span></span>

1. <span data-ttu-id="f4497-387">屬性支援兩種類型的淺色圖形: `Square`和`Circle`。 `MarqueeLightShape`</span><span class="sxs-lookup"><span data-stu-id="f4497-387">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="f4497-388">您將建立僅用於在屬性視窗中以圖形方式顯示這些值的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-388">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="f4497-389">此自訂控制項將由您<xref:System.Drawing.Design.UITypeEditor>用來與屬性視窗互動。</span><span class="sxs-lookup"><span data-stu-id="f4497-389">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="f4497-390">若要建立自訂 UI 類型編輯器的 view 控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-390">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="f4497-391">將新<xref:System.Windows.Forms.UserControl>專案加入`MarqueeControlLibrary`至專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-391">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-392">為新的來源檔案提供 "LightShapeSelectionControl" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="f4497-392">Give the new source file a base name of "LightShapeSelectionControl."</span></span>

2. <span data-ttu-id="f4497-393">將兩<xref:System.Windows.Forms.Panel>個控制項從 [ `LightShapeSelectionControl`工具箱] 拖曳至。</span><span class="sxs-lookup"><span data-stu-id="f4497-393">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="f4497-394">將其`squarePanel`命名`circlePanel`為和。</span><span class="sxs-lookup"><span data-stu-id="f4497-394">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="f4497-395">並排排列它們。</span><span class="sxs-lookup"><span data-stu-id="f4497-395">Arrange them side by side.</span></span> <span data-ttu-id="f4497-396">將兩<xref:System.Windows.Forms.Control.Size%2A>個<xref:System.Windows.Forms.Panel>控制項的屬性設定為 (60、60)。</span><span class="sxs-lookup"><span data-stu-id="f4497-396">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to (60, 60).</span></span> <span data-ttu-id="f4497-397">將`squarePanel`控制項<xref:System.Windows.Forms.Control.Location%2A>的屬性設定為 (8, 10)。</span><span class="sxs-lookup"><span data-stu-id="f4497-397">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to (8, 10).</span></span> <span data-ttu-id="f4497-398">將`circlePanel`控制項<xref:System.Windows.Forms.Control.Location%2A>的屬性設定為 (80, 10)。</span><span class="sxs-lookup"><span data-stu-id="f4497-398">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to (80, 10).</span></span> <span data-ttu-id="f4497-399">最後, 將的<xref:System.Windows.Forms.Control.Size%2A>屬性`LightShapeSelectionControl`設定為 (150, 80)。</span><span class="sxs-lookup"><span data-stu-id="f4497-399">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to (150, 80).</span></span>

3. <span data-ttu-id="f4497-400">在程式**代碼編輯器**中開啟原始程式檔。`LightShapeSelectionControl`</span><span class="sxs-lookup"><span data-stu-id="f4497-400">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="f4497-401">在檔案的頂端, 匯入<xref:System.Windows.Forms.Design?displayProperty=nameWithType>命名空間:</span><span class="sxs-lookup"><span data-stu-id="f4497-401">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. <span data-ttu-id="f4497-402">為<xref:System.Windows.Forms.Control.Click>和控制項`circlePanel`執行事件處理常式。 `squarePanel`</span><span class="sxs-lookup"><span data-stu-id="f4497-402">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="f4497-403">這些方法<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>會叫用來結束<xref:System.Drawing.Design.UITypeEditor>自訂的編輯會話。</span><span class="sxs-lookup"><span data-stu-id="f4497-403">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. <span data-ttu-id="f4497-404">宣告名<xref:System.Windows.Forms.Design.IWindowsFormsEditorService> `editorService`為的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="f4497-404">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. <span data-ttu-id="f4497-405">宣告名`MarqueeLightShape` `lightShapeValue`為的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="f4497-405">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. <span data-ttu-id="f4497-406">在此`LightShapeSelectionControl`函數中, <xref:System.Windows.Forms.Control.Click>將事件處理常式附加`squarePanel` <xref:System.Windows.Forms.Control.Click>至`circlePanel`和控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="f4497-406">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="f4497-407">此外, 定義從設計環境將`MarqueeLightShape`值指派`lightShapeValue`給欄位的函式多載。</span><span class="sxs-lookup"><span data-stu-id="f4497-407">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. <span data-ttu-id="f4497-408">在方法中, 卸<xref:System.Windows.Forms.Control.Click>離事件處理常式。 <xref:System.ComponentModel.Component.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="f4497-408">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. <span data-ttu-id="f4497-409">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f4497-409">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="f4497-410">開啟 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl 檔案, 並移除<xref:System.ComponentModel.Component.Dispose%2A>方法的預設定義。</span><span class="sxs-lookup"><span data-stu-id="f4497-410">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

5. <span data-ttu-id="f4497-411">實作 `LightShape` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f4497-411">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <span data-ttu-id="f4497-412">覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f4497-412">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="f4497-413">此實行會繪製實心方形和圓形。</span><span class="sxs-lookup"><span data-stu-id="f4497-413">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="f4497-414">它也會反白顯示選取的值, 方法是在一個圖形周圍繪製框線。</span><span class="sxs-lookup"><span data-stu-id="f4497-414">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a><span data-ttu-id="f4497-415">在設計工具中測試您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="f4497-415">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="f4497-416">此時, 您可以建立`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-416">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f4497-417">藉由建立繼承自`MarqueeControl`類別並在表單上使用的控制項, 來測試您的執行。</span><span class="sxs-lookup"><span data-stu-id="f4497-417">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="f4497-418">若要建立自訂 MarqueeControl 實</span><span class="sxs-lookup"><span data-stu-id="f4497-418">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="f4497-419">在 Windows Form 設計工具中開啟 `DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="f4497-419">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="f4497-420">這會建立`DemoMarqueeControl`類型的實例, 並將它顯示在`MarqueeControlRootDesigner`類型的實例中。</span><span class="sxs-lookup"><span data-stu-id="f4497-420">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="f4497-421">在 [**工具箱**] 中, 開啟 [ **MarqueeControlLibrary 元件**] 索引標籤。您會看到可`MarqueeBorder`供`MarqueeText`選取的和控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-421">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="f4497-422">將`MarqueeBorder`控制項的實例拖曳`DemoMarqueeControl`到設計介面上。</span><span class="sxs-lookup"><span data-stu-id="f4497-422">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="f4497-423">將此`MarqueeBorder`控制項停駐于父控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-423">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="f4497-424">將`MarqueeText`控制項的實例拖曳`DemoMarqueeControl`到設計介面上。</span><span class="sxs-lookup"><span data-stu-id="f4497-424">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="f4497-425">建置方案。</span><span class="sxs-lookup"><span data-stu-id="f4497-425">Build the solution.</span></span>

6. <span data-ttu-id="f4497-426">以滑鼠右鍵按一下`DemoMarqueeControl`快捷方式功能表上的 [], 然後選取 [**執行測試**] 選項來啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="f4497-426">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="f4497-427">按一下 [**停止測試**] 以停止動畫。</span><span class="sxs-lookup"><span data-stu-id="f4497-427">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="f4497-428">在設計檢視中開啟 [Form1]。</span><span class="sxs-lookup"><span data-stu-id="f4497-428">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="f4497-429">將兩<xref:System.Windows.Forms.Button>個控制項放在表單上。</span><span class="sxs-lookup"><span data-stu-id="f4497-429">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="f4497-430">將它們`startButton`命名`stopButton`為和, 並<xref:System.Windows.Forms.Control.Text%2A>分別將屬性值變更為 [**開始**] 和 [**停止**]。</span><span class="sxs-lookup"><span data-stu-id="f4497-430">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="f4497-431">為<xref:System.Windows.Forms.Control.Click>這兩個<xref:System.Windows.Forms.Button>控制項執行事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f4497-431">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="f4497-432">在 [**工具箱**] 中, 開啟 [ **MarqueeControlTest 元件**] 索引標籤。您會看到可`DemoMarqueeControl`供選擇的專案。</span><span class="sxs-lookup"><span data-stu-id="f4497-432">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="f4497-433">將的`DemoMarqueeControl`實例拖曳至 [ **Form1** ] 設計介面上。</span><span class="sxs-lookup"><span data-stu-id="f4497-433">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="f4497-434">在事件處理常式中, 叫`Start`用`Stop`上`DemoMarqueeControl`的和方法。 <xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="f4497-434">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

```vb
Private Sub startButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Start()
End Sub 'startButton_Click

Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
Me.demoMarqueeControl1.Stop()
End Sub 'stopButton_Click
```

```csharp
private void startButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Start();
}

private void stopButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Stop();
}
```

1. <span data-ttu-id="f4497-435">`MarqueeControlTest`將專案設定為啟始專案, 並加以執行。</span><span class="sxs-lookup"><span data-stu-id="f4497-435">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="f4497-436">您會看到顯示您`DemoMarqueeControl`的表單。</span><span class="sxs-lookup"><span data-stu-id="f4497-436">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="f4497-437">按一下 [**啟動**] 按鈕以啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="f4497-437">Click the **Start** button to start the animation.</span></span> <span data-ttu-id="f4497-438">您應該會看到文字閃爍, 而光線周圍的燈會移動。</span><span class="sxs-lookup"><span data-stu-id="f4497-438">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f4497-439">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f4497-439">Next Steps</span></span>

<span data-ttu-id="f4497-440">`MarqueeControlLibrary`示範了簡單的自訂控制項和相關設計工具的執行。</span><span class="sxs-lookup"><span data-stu-id="f4497-440">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="f4497-441">您可以透過數種方式讓此範例更為複雜:</span><span class="sxs-lookup"><span data-stu-id="f4497-441">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="f4497-442">在設計工具中變更的`DemoMarqueeControl`屬性值。</span><span class="sxs-lookup"><span data-stu-id="f4497-442">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="f4497-443">新增更`MarqueBorder`多控制項, 並將它們固定在其父實例內, 以建立嵌套的效果。</span><span class="sxs-lookup"><span data-stu-id="f4497-443">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="f4497-444">針對`UpdatePeriod`和 light 相關的屬性試驗不同的設定。</span><span class="sxs-lookup"><span data-stu-id="f4497-444">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="f4497-445">撰寫您自己的`IMarqueeWidget`實作者。</span><span class="sxs-lookup"><span data-stu-id="f4497-445">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="f4497-446">例如, 您可以建立閃爍的「霓虹燈號」或具有多個影像的動畫符號。</span><span class="sxs-lookup"><span data-stu-id="f4497-446">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="f4497-447">進一步自訂設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="f4497-447">Further customize the design-time experience.</span></span> <span data-ttu-id="f4497-448">您可以嘗試遮蔽比<xref:System.Windows.Forms.Control.Enabled%2A>和<xref:System.Windows.Forms.Control.Visible%2A>更多的屬性, 也可以加入新的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4497-448">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="f4497-449">加入新的設計工具動詞來簡化一般工作, 例如停駐子控制項。</span><span class="sxs-lookup"><span data-stu-id="f4497-449">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="f4497-450">`MarqueeControl`授權。</span><span class="sxs-lookup"><span data-stu-id="f4497-450">License the `MarqueeControl`.</span></span> <span data-ttu-id="f4497-451">如需詳細資訊，請參閱[如何：授權元件和控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="f4497-451">For more information, see [How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span></span>

- <span data-ttu-id="f4497-452">控制控制項的序列化方式, 以及如何為其產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4497-452">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="f4497-453">如需詳細資訊, 請參閱[動態來來源程式代碼產生和編譯](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="f4497-453">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4497-454">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4497-454">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- <span data-ttu-id="f4497-455">[如何：建立會利用設計階段功能的 Windows Forms 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f4497-455">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>
- <span data-ttu-id="f4497-456">[擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f4497-456">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- <span data-ttu-id="f4497-457">[自訂設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f4497-457">[Custom Designers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span></span>
