---
title: 建立利用 Visual Studio 設計階段功能的控制項
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744072"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="1f251-102">逐步解說：建立利用設計階段功能的控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-102">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="1f251-103">您可以撰寫相關聯的自訂設計工具來增強自訂控制項的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="1f251-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="1f251-104">本文說明如何建立自訂控制項的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-104">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="1f251-105">您將會執行 `MarqueeControl` 型別，以及稱為 `MarqueeControlRootDesigner`的相關聯設計工具類別。</span><span class="sxs-lookup"><span data-stu-id="1f251-105">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="1f251-106">`MarqueeControl` 類型會使用動畫燈和閃爍文字，來執行類似劇院天棚的顯示。</span><span class="sxs-lookup"><span data-stu-id="1f251-106">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="1f251-107">此控制項的設計工具會與設計環境互動，以提供自訂的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="1f251-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="1f251-108">在自訂設計工具中，您可以使用動畫光線組合自訂的 `MarqueeControl` 實，並以許多組合來進行閃爍的文字。</span><span class="sxs-lookup"><span data-stu-id="1f251-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="1f251-109">您可以在表單上使用群組控制項，就像任何其他 Windows Forms 控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="1f251-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="1f251-110">當您完成本逐步解說時，您的自訂控制項看起來會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="1f251-110">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![應用程式會顯示文字和 [開始] 和 [停止] 按鈕的提示。](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="1f251-112">如需完整的程式代碼清單，請參閱[如何：建立利用設計階段功能的 Windows Forms 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="1f251-112">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f251-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="1f251-113">Prerequisites</span></span>

<span data-ttu-id="1f251-114">為了完成此逐步解說，您需要 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1f251-114">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="1f251-115">建立專案</span><span class="sxs-lookup"><span data-stu-id="1f251-115">Create the project</span></span>

<span data-ttu-id="1f251-116">第一個步驟是建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-116">The first step is to create the application project.</span></span> <span data-ttu-id="1f251-117">您將使用此專案來建立裝載自訂控制項的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f251-117">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="1f251-118">在 Visual Studio 中，建立新的 Windows Forms 應用程式專案，並將其命名為**MarqueeControlTest**。</span><span class="sxs-lookup"><span data-stu-id="1f251-118">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="1f251-119">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="1f251-119">Create the control library project</span></span>

1. <span data-ttu-id="1f251-120">將 Windows Forms 控制項程式庫專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="1f251-120">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="1f251-121">將專案命名為**MarqueeControlLibrary**。</span><span class="sxs-lookup"><span data-stu-id="1f251-121">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="1f251-122">使用**方案總管**，根據您選擇的語言刪除名為 "UserControl1.cs" 或 "UserControl1" 的來源檔案，以刪除專案的預設控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-122">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="1f251-123">將新的 <xref:System.Windows.Forms.UserControl> 專案加入至 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-123">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="1f251-124">為新的來源檔案提供**MarqueeControl**的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-124">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="1f251-125">使用**方案總管**，在 `MarqueeControlLibrary` 專案中建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1f251-125">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="1f251-126">以滑鼠右鍵按一下 [**設計**] 資料夾，並加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="1f251-126">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="1f251-127">將它命名為**MarqueeControlRootDesigner**。</span><span class="sxs-lookup"><span data-stu-id="1f251-127">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="1f251-128">您必須使用來自 system.servicemodel 元件的類型，因此請將此參考新增至 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-128">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="1f251-129">參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="1f251-129">Reference the Custom Control Project</span></span>

<span data-ttu-id="1f251-130">您將使用 `MarqueeControlTest` 專案來測試自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-130">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="1f251-131">當您將專案參考加入至 `MarqueeControlLibrary` 元件時，測試專案將會察覺自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-131">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="1f251-132">在 `MarqueeControlTest` 專案中，將專案參考加入至 `MarqueeControlLibrary` 元件。</span><span class="sxs-lookup"><span data-stu-id="1f251-132">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="1f251-133">請務必使用 [**加入參考**] 對話方塊中的 [**專案**] 索引標籤，而不是直接參考 `MarqueeControlLibrary` 元件。</span><span class="sxs-lookup"><span data-stu-id="1f251-133">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="1f251-134">定義自訂控制項及其自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="1f251-134">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="1f251-135">您的自訂控制項會從 <xref:System.Windows.Forms.UserControl> 類別衍生。</span><span class="sxs-lookup"><span data-stu-id="1f251-135">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="1f251-136">這可讓您的控制項包含其他控制項，並讓您的控制項有很多的預設功能。</span><span class="sxs-lookup"><span data-stu-id="1f251-136">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="1f251-137">您的自訂控制項將會有相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-137">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="1f251-138">這可讓您建立專為您的自訂控制項量身打造的獨特設計經驗。</span><span class="sxs-lookup"><span data-stu-id="1f251-138">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="1f251-139">您可以使用 <xref:System.ComponentModel.DesignerAttribute> 類別，讓控制項與設計工具產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1f251-139">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="1f251-140">因為您正在開發自訂控制項的整個設計階段行為，所以自訂設計工具會執行 <xref:System.ComponentModel.Design.IRootDesigner> 介面。</span><span class="sxs-lookup"><span data-stu-id="1f251-140">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="1f251-141">若要定義自訂控制項和其自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="1f251-141">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="1f251-142">在程式**代碼編輯器**中開啟 `MarqueeControl` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-142">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-143">在檔案的頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-143">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="1f251-144">將 <xref:System.ComponentModel.DesignerAttribute> 新增至 `MarqueeControl` 類別宣告。</span><span class="sxs-lookup"><span data-stu-id="1f251-144">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="1f251-145">這會使自訂控制項與其設計工具產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1f251-145">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="1f251-146">在程式**代碼編輯器**中開啟 `MarqueeControlRootDesigner` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-146">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-147">在檔案的頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-147">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="1f251-148">將 `MarqueeControlRootDesigner` 的宣告變更為繼承自 <xref:System.Windows.Forms.Design.DocumentDesigner> 類別。</span><span class="sxs-lookup"><span data-stu-id="1f251-148">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="1f251-149">套用 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 以指定設計工具與 [**工具箱**] 的互動。</span><span class="sxs-lookup"><span data-stu-id="1f251-149">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1f251-150">`MarqueeControlRootDesigner` 類別的定義已包含在名為 MarqueeControlLibrary 的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1f251-150">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="1f251-151">這個宣告會將設計工具放在保留給設計相關類型的特殊命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1f251-151">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="1f251-152">定義 `MarqueeControlRootDesigner` 類別的「構造函式」。</span><span class="sxs-lookup"><span data-stu-id="1f251-152">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="1f251-153">在函式主體中插入 <xref:System.Diagnostics.Trace.WriteLine%2A> 語句。</span><span class="sxs-lookup"><span data-stu-id="1f251-153">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="1f251-154">這將有助於進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-154">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="1f251-155">建立自訂控制項的實例</span><span class="sxs-lookup"><span data-stu-id="1f251-155">Create an instance of your custom control</span></span>

1. <span data-ttu-id="1f251-156">將新的 <xref:System.Windows.Forms.UserControl> 專案加入至 `MarqueeControlTest` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-156">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="1f251-157">為新的來源檔案提供**DemoMarqueeControl**的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-157">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="1f251-158">在程式**代碼編輯器**中開啟 `DemoMarqueeControl` 檔案。</span><span class="sxs-lookup"><span data-stu-id="1f251-158">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-159">在檔案的頂端，匯入 `MarqueeControlLibrary` 命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-159">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="1f251-160">將 `DemoMarqueeControl` 的宣告變更為繼承自 `MarqueeControl` 類別。</span><span class="sxs-lookup"><span data-stu-id="1f251-160">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="1f251-161">建置專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-161">Build the project.</span></span>

5. <span data-ttu-id="1f251-162">在 Windows Form 設計工具中開啟 Form1。</span><span class="sxs-lookup"><span data-stu-id="1f251-162">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="1f251-163">在 [**工具箱**] 中尋找 [ **MarqueeControlTest 元件**] 索引標籤，並加以開啟。</span><span class="sxs-lookup"><span data-stu-id="1f251-163">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="1f251-164">將 `DemoMarqueeControl` 從 **工具箱** 拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="1f251-164">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="1f251-165">建置專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-165">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="1f251-166">設定專案以進行設計階段的偵錯工具</span><span class="sxs-lookup"><span data-stu-id="1f251-166">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="1f251-167">當您開發自訂的設計階段體驗時，必須先將控制項和元件進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-167">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="1f251-168">有一種簡單的方式可設定您的專案，以允許在設計階段進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-168">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="1f251-169">如需詳細資訊，請參閱[逐步解說：在設計階段進行自訂 Windows Forms 控制項的調試](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)程式。</span><span class="sxs-lookup"><span data-stu-id="1f251-169">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="1f251-170">以滑鼠右鍵按一下 [`MarqueeControlLibrary`] 專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="1f251-170">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="1f251-171">在 [ **MarqueeControlLibrary 屬性頁**] 對話方塊中，選取 [ **Debug** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="1f251-171">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="1f251-172">在 [**起始動作**] 區段中，選取 [**啟動外部程式**]。</span><span class="sxs-lookup"><span data-stu-id="1f251-172">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="1f251-173">您將會 Visual Studio 的個別實例進行偵錯工具，因此，請按一下省略號（![[Visual Studio](./media/visual-studio-ellipsis-button.png)）] 按鈕屬性視窗中的省略號按鈕（...），以流覽 Visual Studio IDE。</span><span class="sxs-lookup"><span data-stu-id="1f251-173">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="1f251-174">可執行檔的名稱為 devenv，如果您安裝到預設位置，其路徑為 *% ProgramFiles （x86）% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*。</span><span class="sxs-lookup"><span data-stu-id="1f251-174">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="1f251-175">選取 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1f251-175">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="1f251-176">以滑鼠右鍵按一下 [MarqueeControlLibrary] 專案，然後選取 [**設定為啟始專案**]，以啟用此調試設定。</span><span class="sxs-lookup"><span data-stu-id="1f251-176">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="1f251-177">檢查點</span><span class="sxs-lookup"><span data-stu-id="1f251-177">Checkpoint</span></span>

<span data-ttu-id="1f251-178">您現在已準備好要開始進行自訂控制項的設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="1f251-178">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="1f251-179">一旦確定已正確設定偵錯工具環境，就會測試自訂控制項和自訂設計工具之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="1f251-179">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="1f251-180">測試調試環境和設計工具關聯</span><span class="sxs-lookup"><span data-stu-id="1f251-180">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="1f251-181">在程式**代碼編輯器**中開啟 MarqueeControlRootDesigner 原始程式檔，並將中斷點放在 <xref:System.Diagnostics.Trace.WriteLine%2A> 語句上。</span><span class="sxs-lookup"><span data-stu-id="1f251-181">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="1f251-182">按**F5**啟動「調試」會話。</span><span class="sxs-lookup"><span data-stu-id="1f251-182">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="1f251-183">建立 Visual Studio 的新實例。</span><span class="sxs-lookup"><span data-stu-id="1f251-183">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="1f251-184">在 Visual Studio 的新實例中，開啟 MarqueeControlTest 方案。</span><span class="sxs-lookup"><span data-stu-id="1f251-184">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="1f251-185">您可以從 [檔案] 功能表選取 [**最近使用的專案** **]，輕鬆**地找到解決方案。</span><span class="sxs-lookup"><span data-stu-id="1f251-185">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="1f251-186">MarqueeControlTest 的方案檔會列為最近使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="1f251-186">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="1f251-187">在設計工具中開啟 `DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="1f251-187">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="1f251-188">Visual Studio 的偵錯工具實例會取得焦點，而執行則會在您的中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="1f251-188">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="1f251-189">按**F5**繼續執行調試會話。</span><span class="sxs-lookup"><span data-stu-id="1f251-189">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="1f251-190">此時，所有專案都已準備就緒，可供您開發和偵錯工具的自訂控制項和其相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-190">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="1f251-191">本文的其餘部分將著重于實作為控制項和設計工具功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1f251-191">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="1f251-192">執行自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-192">Implement the Custom Control</span></span>

<span data-ttu-id="1f251-193">`MarqueeControl` 是一個 <xref:System.Windows.Forms.UserControl>，而且有一些自訂。</span><span class="sxs-lookup"><span data-stu-id="1f251-193">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="1f251-194">它會公開兩個方法： `Start`，這會啟動「天棚」動畫，並 `Stop`，這會停止動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-194">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="1f251-195">由於 `MarqueeControl` 包含實 `IMarqueeWidget` 介面的子控制項，因此 `Start` 和 `Stop` 列舉每個子控制項，並分別在每個執行 `StartMarquee` 的子控制項上呼叫 `StopMarquee` 和 `IMarqueeWidget`方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-195">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="1f251-196">`MarqueeBorder` 和 `MarqueeText` 控制項的外觀取決於版面配置，因此 `MarqueeControl` 會覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法，並在此類型的子控制項上呼叫 <xref:System.Windows.Forms.Control.PerformLayout%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f251-196">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="1f251-197">這是 `MarqueeControl` 自訂的範圍。</span><span class="sxs-lookup"><span data-stu-id="1f251-197">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="1f251-198">執行時間功能是由 `MarqueeBorder` 和 `MarqueeText` 控制項所實，而設計階段功能則是由 `MarqueeBorderDesigner` 和 `MarqueeControlRootDesigner` 類別來執行。</span><span class="sxs-lookup"><span data-stu-id="1f251-198">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="1f251-199">若要執行您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-199">To implement your custom control</span></span>

1. <span data-ttu-id="1f251-200">在程式**代碼編輯器**中開啟 `MarqueeControl` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-200">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-201">執行 `Start` 和 `Stop` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-201">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="1f251-202">覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-202">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="1f251-203">建立自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-203">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="1f251-204">`MarqueeControl` 將裝載兩種類型的子控制項： `MarqueeBorder` 控制項和 `MarqueeText` 控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-204">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="1f251-205">`MarqueeBorder`：此控制項會在其邊緣周圍繪製「光源」的框線。</span><span class="sxs-lookup"><span data-stu-id="1f251-205">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="1f251-206">燈光會依序閃爍，因此它們看起來會在框線周圍移動。</span><span class="sxs-lookup"><span data-stu-id="1f251-206">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="1f251-207">燈閃爍的速度，是由稱為 `UpdatePeriod`的屬性所控制。</span><span class="sxs-lookup"><span data-stu-id="1f251-207">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="1f251-208">其他幾個自訂屬性會決定控制面板的其他層面。</span><span class="sxs-lookup"><span data-stu-id="1f251-208">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="1f251-209">兩個稱為 `StartMarquee` 和 `StopMarquee`的方法，會控制動畫啟動和停止的時間。</span><span class="sxs-lookup"><span data-stu-id="1f251-209">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="1f251-210">`MarqueeText`：此控制項會繪製閃爍的字串。</span><span class="sxs-lookup"><span data-stu-id="1f251-210">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="1f251-211">就像 `MarqueeBorder` 控制項一樣，文字閃爍的速度是由 `UpdatePeriod` 屬性所控制。</span><span class="sxs-lookup"><span data-stu-id="1f251-211">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="1f251-212">`MarqueeText` 控制項也具有 `MarqueeBorder` 控制項共同的 `StartMarquee` 和 `StopMarquee` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-212">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="1f251-213">在設計階段，`MarqueeControlRootDesigner` 可讓您將這兩種控制項類型新增至任何組合中的 `MarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="1f251-213">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="1f251-214">這兩個控制項的一般功能會分解成稱為 `IMarqueeWidget`的介面。</span><span class="sxs-lookup"><span data-stu-id="1f251-214">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="1f251-215">這可讓 `MarqueeControl` 探索任何與天棚相關的子控制項，並提供特殊的處理方式。</span><span class="sxs-lookup"><span data-stu-id="1f251-215">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="1f251-216">若要執行定期動畫功能，您將使用來自 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間的 <xref:System.ComponentModel.BackgroundWorker> 物件。</span><span class="sxs-lookup"><span data-stu-id="1f251-216">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1f251-217">您可以使用 <xref:System.Windows.Forms.Timer> 物件，但當有許多 `IMarqueeWidget` 物件存在時，單一 UI 執行緒可能無法跟上動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-217">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="1f251-218">若要建立自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-218">To create a child control for your custom control</span></span>

1. <span data-ttu-id="1f251-219">將新的類別專案加入至 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-219">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="1f251-220">為新的來源檔案提供 "IMarqueeWidget" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-220">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="1f251-221">在程式**代碼編輯器**中開啟 `IMarqueeWidget` 原始程式檔，並將宣告從 `class` 變更為 `interface`：</span><span class="sxs-lookup"><span data-stu-id="1f251-221">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="1f251-222">將下列程式碼新增至 `IMarqueeWidget` 介面，以公開兩個方法，以及可操作字幕動畫的屬性：</span><span class="sxs-lookup"><span data-stu-id="1f251-222">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="1f251-223">將新的**自訂控制項**專案加入至 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-223">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="1f251-224">為新的來源檔案提供 "MarqueeText" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-224">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="1f251-225">將 [<xref:System.ComponentModel.BackgroundWorker>] 元件從 [**工具箱**] 拖曳至您的 `MarqueeText` 控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-225">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="1f251-226">此元件可讓 `MarqueeText` 控制項以非同步方式更新其本身。</span><span class="sxs-lookup"><span data-stu-id="1f251-226">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="1f251-227">在 [**屬性**] 視窗中，將 <xref:System.ComponentModel.BackgroundWorker> 元件的 `WorkerReportsProgress` 和 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> 屬性設定為 [ **true**]。</span><span class="sxs-lookup"><span data-stu-id="1f251-227">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="1f251-228">這些設定可讓 <xref:System.ComponentModel.BackgroundWorker> 元件定期引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，並取消非同步更新。</span><span class="sxs-lookup"><span data-stu-id="1f251-228">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="1f251-229">如需詳細資訊，請參閱[BackgroundWorker 元件](backgroundworker-component.md)。</span><span class="sxs-lookup"><span data-stu-id="1f251-229">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="1f251-230">在程式**代碼編輯器**中開啟 `MarqueeText` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-230">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-231">在檔案的頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-231">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="1f251-232">將 `MarqueeText` 的宣告變更為繼承自 <xref:System.Windows.Forms.Label> 並執行 `IMarqueeWidget` 介面：</span><span class="sxs-lookup"><span data-stu-id="1f251-232">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="1f251-233">宣告對應至已公開屬性的執行個體變數，並在此函式中將它們初始化。</span><span class="sxs-lookup"><span data-stu-id="1f251-233">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="1f251-234">[`isLit`] 欄位會決定是否要以 [`LightColor`] 屬性所指定的色彩繪製文字。</span><span class="sxs-lookup"><span data-stu-id="1f251-234">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="1f251-235">實作 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="1f251-235">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="1f251-236">`StartMarquee` 和 `StopMarquee` 方法會叫用 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法來啟動和停止動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-236">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="1f251-237"><xref:System.ComponentModel.CategoryAttribute.Category%2A> 和 <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 屬性會套用至 `UpdatePeriod` 屬性，使其出現在名為「天棚」之屬性視窗的自訂區段中。</span><span class="sxs-lookup"><span data-stu-id="1f251-237">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="1f251-238">執行屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="1f251-238">Implement the property accessors.</span></span> <span data-ttu-id="1f251-239">您會向用戶端公開兩個屬性： `LightColor` 和 `DarkColor`。</span><span class="sxs-lookup"><span data-stu-id="1f251-239">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="1f251-240"><xref:System.ComponentModel.CategoryAttribute.Category%2A> 和 <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 屬性會套用至這些屬性，因此屬性會出現在名為「天棚」之屬性視窗的自訂區段中。</span><span class="sxs-lookup"><span data-stu-id="1f251-240">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="1f251-241">執行 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-241">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="1f251-242"><xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式會睡眠，`UpdatePeriod` 所指定的毫秒數，然後引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，直到您的程式碼藉由呼叫 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>來停止動畫為止。</span><span class="sxs-lookup"><span data-stu-id="1f251-242">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="1f251-243"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件處理常式會將文字切換成淺與深的狀態，以提供閃爍的外觀。</span><span class="sxs-lookup"><span data-stu-id="1f251-243">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="1f251-244">覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法以啟用動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-244">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="1f251-245">按 **F6** 以建立方案。</span><span class="sxs-lookup"><span data-stu-id="1f251-245">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="1f251-246">建立 MarqueeBorder 子控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-246">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="1f251-247">`MarqueeBorder` 控制項比 `MarqueeText` 控制項稍微複雜一點。</span><span class="sxs-lookup"><span data-stu-id="1f251-247">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="1f251-248">其中包含更多屬性，而 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法中的動畫則比較複雜。</span><span class="sxs-lookup"><span data-stu-id="1f251-248">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="1f251-249">原則上，它與 `MarqueeText` 控制項非常類似。</span><span class="sxs-lookup"><span data-stu-id="1f251-249">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="1f251-250">因為 `MarqueeBorder` 控制項可以有子控制項，所以必須留意 <xref:System.Windows.Forms.Control.Layout> 的事件。</span><span class="sxs-lookup"><span data-stu-id="1f251-250">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="1f251-251">若要建立 MarqueeBorder 控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-251">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="1f251-252">將新的**自訂控制項**專案加入至 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-252">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="1f251-253">為新的來源檔案提供 "MarqueeBorder" 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-253">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="1f251-254">將 [<xref:System.ComponentModel.BackgroundWorker>] 元件從 [**工具箱**] 拖曳至您的 `MarqueeBorder` 控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-254">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="1f251-255">此元件可讓 `MarqueeBorder` 控制項以非同步方式更新其本身。</span><span class="sxs-lookup"><span data-stu-id="1f251-255">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="1f251-256">在 [**屬性**] 視窗中，將 <xref:System.ComponentModel.BackgroundWorker> 元件的 `WorkerReportsProgress` 和 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> 屬性設定為 [ **true**]。</span><span class="sxs-lookup"><span data-stu-id="1f251-256">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="1f251-257">這些設定可讓 <xref:System.ComponentModel.BackgroundWorker> 元件定期引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，並取消非同步更新。</span><span class="sxs-lookup"><span data-stu-id="1f251-257">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="1f251-258">如需詳細資訊，請參閱[BackgroundWorker 元件](backgroundworker-component.md)。</span><span class="sxs-lookup"><span data-stu-id="1f251-258">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="1f251-259">在 [**屬性**] 視窗中，選取 [**事件**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f251-259">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="1f251-260">附加 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-260">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="1f251-261">在程式**代碼編輯器**中開啟 `MarqueeBorder` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-261">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-262">在檔案的頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-262">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="1f251-263">將 `MarqueeBorder` 的宣告變更為繼承自 <xref:System.Windows.Forms.Panel> 並執行 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="1f251-263">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="1f251-264">宣告兩個列舉來管理 `MarqueeBorder` 控制項的狀態： [`MarqueeSpinDirection`]，這會決定光線圍繞框線的方向，以及 [`MarqueeLightShape`]，以決定光源的形狀（方形或圓形）。</span><span class="sxs-lookup"><span data-stu-id="1f251-264">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="1f251-265">將這些宣告放在 `MarqueeBorder` 類別宣告之前。</span><span class="sxs-lookup"><span data-stu-id="1f251-265">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="1f251-266">宣告對應至已公開屬性的執行個體變數，並在此函式中將它們初始化。</span><span class="sxs-lookup"><span data-stu-id="1f251-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="1f251-267">實作 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="1f251-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="1f251-268">`StartMarquee` 和 `StopMarquee` 方法會叫用 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法來啟動和停止動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="1f251-269">因為 `MarqueeBorder` 控制項可以包含子控制項，所以 `StartMarquee` 方法會列舉所有子控制項，並在執行 `IMarqueeWidget`的節點上呼叫 `StartMarquee`。</span><span class="sxs-lookup"><span data-stu-id="1f251-269">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="1f251-270">`StopMarquee` 方法有類似的執行方式。</span><span class="sxs-lookup"><span data-stu-id="1f251-270">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="1f251-271">執行屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="1f251-271">Implement the property accessors.</span></span> <span data-ttu-id="1f251-272">`MarqueeBorder` 控制項有數個屬性可控制其外觀。</span><span class="sxs-lookup"><span data-stu-id="1f251-272">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="1f251-273">執行 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="1f251-274"><xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式會睡眠，`UpdatePeriod` 所指定的毫秒數，然後引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，直到您的程式碼藉由呼叫 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>來停止動畫為止。</span><span class="sxs-lookup"><span data-stu-id="1f251-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="1f251-275"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件處理常式會遞增「基底」光源的位置，也就是判斷出另一個光源的淺色/深色狀態，然後呼叫 <xref:System.Windows.Forms.Control.Refresh%2A> 方法，讓控制項自行重新繪製。</span><span class="sxs-lookup"><span data-stu-id="1f251-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="1f251-276">執行 helper 方法，`IsLit` 和 `DrawLight`。</span><span class="sxs-lookup"><span data-stu-id="1f251-276">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="1f251-277">`IsLit` 方法會決定指定位置的光線色彩。</span><span class="sxs-lookup"><span data-stu-id="1f251-277">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="1f251-278">「亮」的燈是以 [`LightColor`] 屬性所指定的色彩繪製，而那些「深色」則以 `DarkColor` 屬性所指定的色彩繪製。</span><span class="sxs-lookup"><span data-stu-id="1f251-278">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="1f251-279">`DrawLight` 方法會使用適當的色彩、形狀和位置繪製一個光線。</span><span class="sxs-lookup"><span data-stu-id="1f251-279">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="1f251-280">覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 和 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-280">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="1f251-281"><xref:System.Windows.Forms.Control.OnPaint%2A> 方法會沿著 `MarqueeBorder` 控制項的邊緣繪製光源。</span><span class="sxs-lookup"><span data-stu-id="1f251-281">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="1f251-282">由於 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法取決於 `MarqueeBorder` 控制項的維度，因此每當配置變更時，您都必須呼叫它。</span><span class="sxs-lookup"><span data-stu-id="1f251-282">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="1f251-283">若要達到此目的，請覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 並呼叫 <xref:System.Windows.Forms.Control.Refresh%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f251-283">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="1f251-284">建立自訂設計工具以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="1f251-284">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="1f251-285">`MarqueeControlRootDesigner` 類別提供根設計工具的執行。</span><span class="sxs-lookup"><span data-stu-id="1f251-285">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="1f251-286">除了在 `MarqueeControl`上操作的這個設計工具之外，您還需要一個與 `MarqueeBorder` 控制項特別相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="1f251-286">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="1f251-287">這個設計工具會提供自訂的根設計工具內容中適用的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="1f251-287">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="1f251-288">具體而言，`MarqueeBorderDesigner` 將「陰影」並篩選 `MarqueeBorder` 控制項上的特定屬性，並變更其與設計環境的互動。</span><span class="sxs-lookup"><span data-stu-id="1f251-288">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="1f251-289">攔截元件屬性存取子的呼叫稱為「遮蔽」。</span><span class="sxs-lookup"><span data-stu-id="1f251-289">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="1f251-290">它可讓設計工具追蹤使用者所設定的值，並選擇性地將該值傳遞至所設計的元件。</span><span class="sxs-lookup"><span data-stu-id="1f251-290">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="1f251-291">在此範例中，<xref:System.Windows.Forms.Control.Visible%2A> 和 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性會由 `MarqueeBorderDesigner`加上陰影，這可防止使用者在設計階段期間隱藏或停用 `MarqueeBorder` 控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-291">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="1f251-292">設計工具也可以加入和移除屬性。</span><span class="sxs-lookup"><span data-stu-id="1f251-292">Designers can also add and remove properties.</span></span> <span data-ttu-id="1f251-293">在此範例中，會在設計階段移除 <xref:System.Windows.Forms.Control.Padding%2A> 屬性，因為 `MarqueeBorder` 控制項會根據 `LightSize` 屬性所指定的光源大小，以程式設計方式設定填補。</span><span class="sxs-lookup"><span data-stu-id="1f251-293">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="1f251-294">`MarqueeBorderDesigner` 的基類 <xref:System.ComponentModel.Design.ComponentDesigner>，其具有可在設計階段變更控制項所公開之屬性、屬性和事件的方法：</span><span class="sxs-lookup"><span data-stu-id="1f251-294">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="1f251-295">使用這些方法變更元件的公用介面時，請遵循下列規則：</span><span class="sxs-lookup"><span data-stu-id="1f251-295">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="1f251-296">僅新增或移除 `PreFilter` 方法中的專案</span><span class="sxs-lookup"><span data-stu-id="1f251-296">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="1f251-297">僅修改 `PostFilter` 方法中的現有專案</span><span class="sxs-lookup"><span data-stu-id="1f251-297">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="1f251-298">一律先在 `PreFilter` 方法中呼叫基底實作為</span><span class="sxs-lookup"><span data-stu-id="1f251-298">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="1f251-299">一律在 `PostFilter` 方法中的最後呼叫基底執行</span><span class="sxs-lookup"><span data-stu-id="1f251-299">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="1f251-300">遵守這些規則可確保設計階段環境中的所有設計工具都能一致地看到所有設計的元件。</span><span class="sxs-lookup"><span data-stu-id="1f251-300">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="1f251-301"><xref:System.ComponentModel.Design.ComponentDesigner> 類別提供用來管理陰影屬性值的字典，讓您不需要建立特定的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="1f251-301">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="1f251-302">若要建立自訂設計工具以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="1f251-302">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="1f251-303">以滑鼠右鍵按一下 [**設計**] 資料夾，並加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="1f251-303">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="1f251-304">為來源檔案提供**MarqueeBorderDesigner**的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-304">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="1f251-305">在程式**代碼編輯器**中開啟 MarqueeBorderDesigner 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-305">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-306">在檔案的頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-306">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="1f251-307">將 `MarqueeBorderDesigner` 的宣告變更為繼承自 <xref:System.Windows.Forms.Design.ParentControlDesigner>。</span><span class="sxs-lookup"><span data-stu-id="1f251-307">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="1f251-308">由於 `MarqueeBorder` 控制項可以包含子控制項，`MarqueeBorderDesigner` 繼承自 <xref:System.Windows.Forms.Design.ParentControlDesigner>，這會處理父子式互動。</span><span class="sxs-lookup"><span data-stu-id="1f251-308">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="1f251-309">覆寫 <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>的基底執行。</span><span class="sxs-lookup"><span data-stu-id="1f251-309">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="1f251-310">實作 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1f251-310">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="1f251-311">這些執行會遮蔽控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="1f251-311">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="1f251-312">處理元件變更</span><span class="sxs-lookup"><span data-stu-id="1f251-312">Handle Component Changes</span></span>

<span data-ttu-id="1f251-313">`MarqueeControlRootDesigner` 類別為您的 `MarqueeControl` 實例提供自訂的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="1f251-313">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="1f251-314">大部分的設計階段功能都是從 <xref:System.Windows.Forms.Design.DocumentDesigner> 類別繼承而來。</span><span class="sxs-lookup"><span data-stu-id="1f251-314">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="1f251-315">您的程式碼將會執行兩個特定的自訂：處理元件變更，以及新增設計工具動詞。</span><span class="sxs-lookup"><span data-stu-id="1f251-315">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="1f251-316">當使用者設計其 `MarqueeControl` 實例時，您的根設計工具會追蹤 `MarqueeControl` 及其子控制項的變更。</span><span class="sxs-lookup"><span data-stu-id="1f251-316">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="1f251-317">設計階段環境提供便利的服務，<xref:System.ComponentModel.Design.IComponentChangeService>，以追蹤元件狀態的變更。</span><span class="sxs-lookup"><span data-stu-id="1f251-317">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="1f251-318">您可以使用 <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> 方法來查詢環境，以取得此服務的參考。</span><span class="sxs-lookup"><span data-stu-id="1f251-318">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="1f251-319">如果查詢成功，您的設計工具可以附加 <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> 事件的處理常式，並執行在設計階段維持一致狀態所需的任何工作。</span><span class="sxs-lookup"><span data-stu-id="1f251-319">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="1f251-320">在 `MarqueeControlRootDesigner` 類別的情況下，您會在 `MarqueeControl`所包含的每個 `IMarqueeWidget` 物件上呼叫 <xref:System.Windows.Forms.Control.Refresh%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-320">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="1f251-321">這會在屬性（如其父系的 <xref:System.Windows.Forms.Control.Size%2A> 變更）時，讓 `IMarqueeWidget` 物件適當地重新繪製本身。</span><span class="sxs-lookup"><span data-stu-id="1f251-321">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="1f251-322">若要處理元件變更</span><span class="sxs-lookup"><span data-stu-id="1f251-322">To handle component changes</span></span>

1. <span data-ttu-id="1f251-323">在程式**代碼編輯器**中開啟 `MarqueeControlRootDesigner` 原始程式檔，並覆寫 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-323">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="1f251-324">呼叫 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 的基底實作為，並查詢 <xref:System.ComponentModel.Design.IComponentChangeService>。</span><span class="sxs-lookup"><span data-stu-id="1f251-324">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="1f251-325">執行 <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-325">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="1f251-326">測試傳送元件的類型，如果它是 `IMarqueeWidget`，請呼叫它的 <xref:System.Windows.Forms.Control.Refresh%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-326">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="1f251-327">將設計工具動詞新增至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="1f251-327">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="1f251-328">設計工具動詞命令是連結至事件處理常式的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="1f251-328">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="1f251-329">設計工具動詞會在設計階段加入至元件的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="1f251-329">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="1f251-330">如需詳細資訊，請參閱 <xref:System.ComponentModel.Design.DesignerVerb>。</span><span class="sxs-lookup"><span data-stu-id="1f251-330">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="1f251-331">您會在設計工具中加入兩個設計工具動詞：**執行測試**和**停止測試**。</span><span class="sxs-lookup"><span data-stu-id="1f251-331">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="1f251-332">這些動詞可讓您在設計階段查看 `MarqueeControl` 的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="1f251-332">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="1f251-333">這些動詞將會新增至 `MarqueeControlRootDesigner`。</span><span class="sxs-lookup"><span data-stu-id="1f251-333">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="1f251-334">叫用**執行測試**時，動詞事件處理常式會在 `MarqueeControl`上呼叫 `StartMarquee` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-334">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="1f251-335">叫用**停止測試**時，動詞事件處理常式會在 `MarqueeControl`上呼叫 `StopMarquee` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-335">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="1f251-336">`StartMarquee` 和 `StopMarquee` 方法的執行會在執行 `IMarqueeWidget`的包含控制項上呼叫這些方法，因此任何包含的 `IMarqueeWidget` 控制項也會參與測試。</span><span class="sxs-lookup"><span data-stu-id="1f251-336">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="1f251-337">將設計工具動詞新增至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="1f251-337">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="1f251-338">在 `MarqueeControlRootDesigner` 類別中，新增名為 `OnVerbRunTest` 和 `OnVerbStopTest`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-338">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="1f251-339">將這些事件處理常式連接至其對應的設計工具動詞。</span><span class="sxs-lookup"><span data-stu-id="1f251-339">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="1f251-340">`MarqueeControlRootDesigner` 繼承其基類的 <xref:System.ComponentModel.Design.DesignerVerbCollection>。</span><span class="sxs-lookup"><span data-stu-id="1f251-340">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="1f251-341">您將建立兩個新的 <xref:System.ComponentModel.Design.DesignerVerb> 物件，並在 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 方法中將它們加入此集合。</span><span class="sxs-lookup"><span data-stu-id="1f251-341">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="1f251-342">建立自訂 UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="1f251-342">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="1f251-343">當您為使用者建立自訂的設計階段體驗時，通常需要建立與屬性視窗的自訂互動。</span><span class="sxs-lookup"><span data-stu-id="1f251-343">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="1f251-344">您可以藉由建立 <xref:System.Drawing.Design.UITypeEditor>來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="1f251-344">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="1f251-345">`MarqueeBorder` 控制項會在屬性視窗中公開數個屬性。</span><span class="sxs-lookup"><span data-stu-id="1f251-345">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="1f251-346">`MarqueeSpinDirection` 和 `MarqueeLightShape` 的其中兩個屬性是以列舉表示。</span><span class="sxs-lookup"><span data-stu-id="1f251-346">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="1f251-347">為了說明 UI 類型編輯器的用法，`MarqueeLightShape` 屬性會有相關聯的 <xref:System.Drawing.Design.UITypeEditor> 類別。</span><span class="sxs-lookup"><span data-stu-id="1f251-347">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="1f251-348">若要建立自訂 UI 類型編輯器</span><span class="sxs-lookup"><span data-stu-id="1f251-348">To create a custom UI type editor</span></span>

1. <span data-ttu-id="1f251-349">在程式**代碼編輯器**中開啟 `MarqueeBorder` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-349">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="1f251-350">在 `MarqueeBorder` 類別的定義中，宣告一個衍生自 <xref:System.Drawing.Design.UITypeEditor>的類別，稱為 `LightShapeEditor`。</span><span class="sxs-lookup"><span data-stu-id="1f251-350">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="1f251-351">宣告稱為 `editorService`的 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="1f251-351">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="1f251-352">覆寫 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-352">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="1f251-353">這個實作為傳回 <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>，告訴設計環境如何顯示 `LightShapeEditor`。</span><span class="sxs-lookup"><span data-stu-id="1f251-353">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="1f251-354">覆寫 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-354">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="1f251-355">此實作為查詢 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 物件的設計環境。</span><span class="sxs-lookup"><span data-stu-id="1f251-355">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="1f251-356">如果成功，則會建立 `LightShapeSelectionControl`。</span><span class="sxs-lookup"><span data-stu-id="1f251-356">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="1f251-357">會叫用 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> 方法來啟動 `LightShapeEditor`。</span><span class="sxs-lookup"><span data-stu-id="1f251-357">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="1f251-358">這個調用的傳回值會傳回到設計環境。</span><span class="sxs-lookup"><span data-stu-id="1f251-358">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="1f251-359">建立自訂 UITypeEditor 的 View 控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-359">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="1f251-360">`MarqueeLightShape` 屬性支援兩種類型的淺色圖形： `Square` 和 `Circle`。</span><span class="sxs-lookup"><span data-stu-id="1f251-360">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="1f251-361">您將建立僅用於在屬性視窗中以圖形方式顯示這些值的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-361">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="1f251-362">此自訂控制項將由您的 <xref:System.Drawing.Design.UITypeEditor> 用來與屬性視窗互動。</span><span class="sxs-lookup"><span data-stu-id="1f251-362">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="1f251-363">若要建立自訂 UI 類型編輯器的 view 控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-363">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="1f251-364">將新的 <xref:System.Windows.Forms.UserControl> 專案加入至 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-364">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="1f251-365">為新的來源檔案提供**LightShapeSelectionControl**的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="1f251-365">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="1f251-366">將兩個 <xref:System.Windows.Forms.Panel> 控制項從 [**工具箱**] 拖曳至 [`LightShapeSelectionControl`]。</span><span class="sxs-lookup"><span data-stu-id="1f251-366">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="1f251-367">將它們命名為 `squarePanel` 和 `circlePanel`。</span><span class="sxs-lookup"><span data-stu-id="1f251-367">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="1f251-368">並排排列它們。</span><span class="sxs-lookup"><span data-stu-id="1f251-368">Arrange them side by side.</span></span> <span data-ttu-id="1f251-369">將兩個 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.Size%2A> 屬性設定為 **（60、60）** 。</span><span class="sxs-lookup"><span data-stu-id="1f251-369">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="1f251-370">將 `squarePanel` 控制項的 <xref:System.Windows.Forms.Control.Location%2A> 屬性設定為 **（8，10）** 。</span><span class="sxs-lookup"><span data-stu-id="1f251-370">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="1f251-371">將 `circlePanel` 控制項的 <xref:System.Windows.Forms.Control.Location%2A> 屬性設定為 **（80，10）** 。</span><span class="sxs-lookup"><span data-stu-id="1f251-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="1f251-372">最後，將 `LightShapeSelectionControl` 的 <xref:System.Windows.Forms.Control.Size%2A> 屬性設定為 **（150，80）** 。</span><span class="sxs-lookup"><span data-stu-id="1f251-372">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="1f251-373">在程式**代碼編輯器**中開啟 `LightShapeSelectionControl` 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="1f251-373">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="1f251-374">在檔案的頂端，匯入 <xref:System.Windows.Forms.Design?displayProperty=nameWithType> 命名空間：</span><span class="sxs-lookup"><span data-stu-id="1f251-374">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="1f251-375">執行 `squarePanel` 和 `circlePanel` 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-375">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="1f251-376">這些方法會叫用 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> 來結束自訂 <xref:System.Drawing.Design.UITypeEditor> 編輯會話。</span><span class="sxs-lookup"><span data-stu-id="1f251-376">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="1f251-377">宣告稱為 `editorService`的 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="1f251-377">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="1f251-378">宣告稱為 `lightShapeValue`的 `MarqueeLightShape` 執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="1f251-378">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="1f251-379">在 `LightShapeSelectionControl` 的函式中，將 <xref:System.Windows.Forms.Control.Click> 事件處理常式附加至 `squarePanel` 和 `circlePanel` 控制項的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="1f251-379">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="1f251-380">此外，定義將 `MarqueeLightShape` 值從設計環境指派至 `lightShapeValue` 欄位的函式多載。</span><span class="sxs-lookup"><span data-stu-id="1f251-380">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="1f251-381">在 <xref:System.ComponentModel.Component.Dispose%2A> 方法中，卸離 <xref:System.Windows.Forms.Control.Click> 的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-381">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="1f251-382">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f251-382">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="1f251-383">開啟 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl 檔案，並移除 <xref:System.ComponentModel.Component.Dispose%2A> 方法的預設定義。</span><span class="sxs-lookup"><span data-stu-id="1f251-383">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="1f251-384">實作 `LightShape` 屬性。</span><span class="sxs-lookup"><span data-stu-id="1f251-384">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="1f251-385">覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-385">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="1f251-386">此實行會繪製實心方形和圓形。</span><span class="sxs-lookup"><span data-stu-id="1f251-386">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="1f251-387">它也會反白顯示選取的值，方法是在一個圖形周圍繪製框線。</span><span class="sxs-lookup"><span data-stu-id="1f251-387">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="1f251-388">在設計工具中測試您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="1f251-388">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="1f251-389">此時，您可以建立 `MarqueeControlLibrary` 專案。</span><span class="sxs-lookup"><span data-stu-id="1f251-389">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="1f251-390">藉由建立繼承自 `MarqueeControl` 類別並在表單上使用的控制項，來測試您的執行。</span><span class="sxs-lookup"><span data-stu-id="1f251-390">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="1f251-391">若要建立自訂 MarqueeControl 實</span><span class="sxs-lookup"><span data-stu-id="1f251-391">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="1f251-392">在 Windows Form 設計工具中開啟 `DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="1f251-392">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="1f251-393">這會建立 `DemoMarqueeControl` 類型的實例，並將它顯示在 `MarqueeControlRootDesigner` 類型的實例中。</span><span class="sxs-lookup"><span data-stu-id="1f251-393">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="1f251-394">在 [**工具箱**] 中，開啟 [ **MarqueeControlLibrary 元件**] 索引標籤。您會看到可供選取的 [`MarqueeBorder`] 和 [`MarqueeText`] 控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-394">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="1f251-395">將 `MarqueeBorder` 控制項的實例拖曳至 `DemoMarqueeControl` 設計介面上。</span><span class="sxs-lookup"><span data-stu-id="1f251-395">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="1f251-396">將此 `MarqueeBorder` 控制項停駐在父控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-396">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="1f251-397">將 `MarqueeText` 控制項的實例拖曳至 `DemoMarqueeControl` 設計介面上。</span><span class="sxs-lookup"><span data-stu-id="1f251-397">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="1f251-398">建置方案。</span><span class="sxs-lookup"><span data-stu-id="1f251-398">Build the solution.</span></span>

6. <span data-ttu-id="1f251-399">以滑鼠右鍵按一下 `DemoMarqueeControl`，然後從快捷方式功能表選取 [**執行測試**] 選項來啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-399">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="1f251-400">按一下 [**停止測試**] 以停止動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-400">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="1f251-401">在設計檢視中開啟 [Form1]。</span><span class="sxs-lookup"><span data-stu-id="1f251-401">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="1f251-402">將兩個 <xref:System.Windows.Forms.Button> 控制項放在表單上。</span><span class="sxs-lookup"><span data-stu-id="1f251-402">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="1f251-403">將它們命名為 `startButton` 和 `stopButton`，並分別將 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更為 [**開始**] 和 [**停止**]。</span><span class="sxs-lookup"><span data-stu-id="1f251-403">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="1f251-404">為這兩個 <xref:System.Windows.Forms.Button> 控制項同時執行 <xref:System.Windows.Forms.Control.Click> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f251-404">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="1f251-405">在 [**工具箱**] 中，開啟 [ **MarqueeControlTest 元件**] 索引標籤。您會看到可供選取的 `DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="1f251-405">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="1f251-406">將 `DemoMarqueeControl` 的實例拖曳至 [ **Form1** ] 設計介面上。</span><span class="sxs-lookup"><span data-stu-id="1f251-406">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="1f251-407">在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，叫用 `DemoMarqueeControl`上的 `Start` 和 `Stop` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f251-407">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

13. <span data-ttu-id="1f251-408">將 `MarqueeControlTest` 專案設定為啟始專案，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="1f251-408">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="1f251-409">您會看到顯示您 `DemoMarqueeControl`的表單。</span><span class="sxs-lookup"><span data-stu-id="1f251-409">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="1f251-410">選取 [**啟動**] 按鈕以啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="1f251-410">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="1f251-411">您應該會看到文字閃爍，而光線周圍的燈會移動。</span><span class="sxs-lookup"><span data-stu-id="1f251-411">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f251-412">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1f251-412">Next steps</span></span>

<span data-ttu-id="1f251-413">`MarqueeControlLibrary` 示範自訂控制項和相關設計工具的簡單執行。</span><span class="sxs-lookup"><span data-stu-id="1f251-413">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="1f251-414">您可以透過數種方式讓此範例更為複雜：</span><span class="sxs-lookup"><span data-stu-id="1f251-414">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="1f251-415">在設計工具中變更 `DemoMarqueeControl` 的屬性值。</span><span class="sxs-lookup"><span data-stu-id="1f251-415">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="1f251-416">新增更多 `MarqueBorder` 控制項，並將它們固定在其父實例內，以建立嵌套的效果。</span><span class="sxs-lookup"><span data-stu-id="1f251-416">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="1f251-417">使用 `UpdatePeriod` 和光源相關屬性的不同設定進行實驗。</span><span class="sxs-lookup"><span data-stu-id="1f251-417">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="1f251-418">撰寫您自己的 `IMarqueeWidget`的實施。</span><span class="sxs-lookup"><span data-stu-id="1f251-418">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="1f251-419">例如，您可以建立閃爍的「霓虹燈號」或具有多個影像的動畫符號。</span><span class="sxs-lookup"><span data-stu-id="1f251-419">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="1f251-420">進一步自訂設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="1f251-420">Further customize the design-time experience.</span></span> <span data-ttu-id="1f251-421">您可以嘗試遮蔽比 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A>更多的屬性，也可以加入新的屬性。</span><span class="sxs-lookup"><span data-stu-id="1f251-421">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="1f251-422">加入新的設計工具動詞來簡化一般工作，例如停駐子控制項。</span><span class="sxs-lookup"><span data-stu-id="1f251-422">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="1f251-423">授權 `MarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="1f251-423">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="1f251-424">控制控制項的序列化方式，以及如何為其產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f251-424">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="1f251-425">如需詳細資訊，請參閱[動態來來源程式代碼產生和編譯](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="1f251-425">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f251-426">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f251-426">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
