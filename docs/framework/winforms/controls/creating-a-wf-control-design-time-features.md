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
ms.openlocfilehash: 9f290629e50d7d791119298059277ba73d8e73eb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211208"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a><span data-ttu-id="8bfbe-102">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-102">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>

<span data-ttu-id="8bfbe-103">撰寫相關聯的自訂設計工具，可以增強自訂控制項的設計階段體驗。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="8bfbe-104">此逐步解說將說明如何建立自訂控制項的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-104">This walkthrough illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="8bfbe-105">您將實作`MarqueeControl`型別和相關聯的設計工具類別，稱為`MarqueeControlRootDesigner`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-105">You will implement a `MarqueeControl` type and an associated designer class, called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="8bfbe-106">`MarqueeControl`類型實作類似劇場跑馬燈，與動畫的燈號閃爍的文字顯示。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-106">The `MarqueeControl` type implements a display similar to a theater marquee, with animated lights and flashing text.</span></span>

<span data-ttu-id="8bfbe-107">此控制項的設計工具互動設計環境來提供自訂的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="8bfbe-108">使用自訂的設計工具中，您可以組合自訂`MarqueeControl`與動畫的燈號閃爍的文字，多種組合的實作。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="8bfbe-109">您可以使用像是任何其他的 Windows Form 控制項在表單上控制項組合。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="8bfbe-110">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-110">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="8bfbe-111">建立專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-111">Creating the Project</span></span>

- <span data-ttu-id="8bfbe-112">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-112">Creating a Control Library Project</span></span>

- <span data-ttu-id="8bfbe-113">參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-113">Referencing the Custom Control Project</span></span>

- <span data-ttu-id="8bfbe-114">定義自訂控制項和其自訂的設計工具</span><span class="sxs-lookup"><span data-stu-id="8bfbe-114">Defining a Custom Control and Its Custom Designer</span></span>

- <span data-ttu-id="8bfbe-115">建立您的自訂控制項的執行個體</span><span class="sxs-lookup"><span data-stu-id="8bfbe-115">Creating an Instance of Your Custom Control</span></span>

- <span data-ttu-id="8bfbe-116">設定設計階段偵錯的專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-116">Setting Up the Project for Design-Time Debugging</span></span>

- <span data-ttu-id="8bfbe-117">實作您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-117">Implementing Your Custom Control</span></span>

- <span data-ttu-id="8bfbe-118">建立您的自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-118">Creating a Child Control for Your Custom Control</span></span>

- <span data-ttu-id="8bfbe-119">建立 MarqueeBorder 子控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-119">Create the MarqueeBorder Child Control</span></span>

- <span data-ttu-id="8bfbe-120">建立自訂的設計工具，以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="8bfbe-120">Creating a Custom Designer to Shadow and Filter Properties</span></span>

- <span data-ttu-id="8bfbe-121">處理元件的變更</span><span class="sxs-lookup"><span data-stu-id="8bfbe-121">Handling Component Changes</span></span>

- <span data-ttu-id="8bfbe-122">將設計工具動詞命令加入至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="8bfbe-122">Adding Designer Verbs to your Custom Designer</span></span>

- <span data-ttu-id="8bfbe-123">建立自訂的 UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="8bfbe-123">Creating a Custom UITypeEditor</span></span>

- <span data-ttu-id="8bfbe-124">在設計工具中測試您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-124">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="8bfbe-125">當您完成時，您的自訂控制項看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-125">When you are finished, your custom control will look something like the following:</span></span>

<span data-ttu-id="8bfbe-126">![可能的 marqueecontrol 可能排列](./media/demomarqueecontrol.gif "DemoMarqueeControl")</span><span class="sxs-lookup"><span data-stu-id="8bfbe-126">![A possible MarqueeControl arrangement](./media/demomarqueecontrol.gif "DemoMarqueeControl")</span></span>

<span data-ttu-id="8bfbe-127">如需完整的程式碼清單，請參閱[How to:建立採用設計階段功能的 Windows Form 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-127">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

> [!NOTE]
> <span data-ttu-id="8bfbe-128">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-128">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8bfbe-129">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-129">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8bfbe-130">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-130">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bfbe-131">必要條件</span><span class="sxs-lookup"><span data-stu-id="8bfbe-131">Prerequisites</span></span>

<span data-ttu-id="8bfbe-132">若要完成此逐步解說中，您必須使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-132">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="8bfbe-133">建立專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-133">Creating the Project</span></span>

<span data-ttu-id="8bfbe-134">第一個步驟是建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-134">The first step is to create the application project.</span></span> <span data-ttu-id="8bfbe-135">您將使用此專案來建置應用程式裝載自訂的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-135">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="8bfbe-136">開啟 Visual Studio 並建立名為"MarqueeControlTest 」 的 Windows Forms 應用程式專案 (**檔案** > **新增** > **專案** > **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**).</span><span class="sxs-lookup"><span data-stu-id="8bfbe-136">Open Visual Studio and create a Windows Forms Application project called "MarqueeControlTest" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="creating-a-control-library-project"></a><span data-ttu-id="8bfbe-137">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-137">Creating a Control Library Project</span></span>

<span data-ttu-id="8bfbe-138">下一個步驟是建立控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-138">The next step is to create the control library project.</span></span> <span data-ttu-id="8bfbe-139">您將建立新的自訂控制項和其對應的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-139">You will create a new custom control and its corresponding custom designer.</span></span>

### <a name="to-create-the-control-library-project"></a><span data-ttu-id="8bfbe-140">若要建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-140">To create the control library project</span></span>

1. <span data-ttu-id="8bfbe-141">將 Windows Form 控制項程式庫專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-141">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="8bfbe-142">將專案命名為"MarqueeControlLibrary。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-142">Name the project "MarqueeControlLibrary."</span></span>

2. <span data-ttu-id="8bfbe-143">使用**方案總管 中**，藉由刪除原始程式檔，視您選擇的語言而定，名為"UserControl1.cs 」 或 「 UserControl1.vb"，刪除專案的預設控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-143">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span> <span data-ttu-id="8bfbe-144">如需詳細資訊，請參閱[如何：移除，請刪除，並排除項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-144">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="8bfbe-145">加入新<xref:System.Windows.Forms.UserControl>項目`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-145">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-146">提供新的原始程式檔的基底名稱的"Marqueecontrol 可能"。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-146">Give the new source file a base name of "MarqueeControl."</span></span>

4. <span data-ttu-id="8bfbe-147">使用**方案總管**，建立新的資料夾中`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-147">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-148">如需詳細資訊，請參閱[如何：加入新的專案項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-148">For more information, see [How to: Add New Project Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100)).</span></span> <span data-ttu-id="8bfbe-149">將新資料夾命名為 「 設計 」。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-149">Name the new folder "Design."</span></span>

5. <span data-ttu-id="8bfbe-150">以滑鼠右鍵按一下**設計**資料夾，並加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-150">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="8bfbe-151">提供的原始程式檔的基底名稱的"MarqueeControlRootDesigner。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-151">Give the source file a base name of "MarqueeControlRootDesigner."</span></span>

6. <span data-ttu-id="8bfbe-152">您必須使用從 System.Design 組件的類型，因此將新增此參考以`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-152">You will need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8bfbe-153">若要使用 System.Design 組件，您的專案必須為目標.NET Framework 中，而非.NET Framework Client Profile 的完整的版本。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-153">To use the System.Design assembly, your project must target the full version of the .NET Framework, not the .NET Framework Client Profile.</span></span> <span data-ttu-id="8bfbe-154">若要變更目標 framework，請參閱[How to:以一個 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-154">To change the target framework, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

## <a name="referencing-the-custom-control-project"></a><span data-ttu-id="8bfbe-155">參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-155">Referencing the Custom Control Project</span></span>

<span data-ttu-id="8bfbe-156">您將使用`MarqueeControlTest`專案來測試自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-156">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="8bfbe-157">當您新增的專案參考時，測試專案將會察覺自訂控制項的`MarqueeControlLibrary`組件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-157">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

### <a name="to-reference-the-custom-control-project"></a><span data-ttu-id="8bfbe-158">若要參考自訂控制項專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-158">To reference the custom control project</span></span>

- <span data-ttu-id="8bfbe-159">在 `MarqueeControlTest`專案中，加入的專案參考`MarqueeControlLibrary`組件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-159">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="8bfbe-160">請務必使用**專案**索引標籤中**加入參考**對話方塊中，而不是參考`MarqueeControlLibrary`直接的組件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-160">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="defining-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="8bfbe-161">定義自訂控制項和其自訂的設計工具</span><span class="sxs-lookup"><span data-stu-id="8bfbe-161">Defining a Custom Control and Its Custom Designer</span></span>
 <span data-ttu-id="8bfbe-162">您的自訂控制項將衍生自<xref:System.Windows.Forms.UserControl>類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-162">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="8bfbe-163">這可讓您的控制項，以包含其他控制項，以及它能讓您控制大量的預設功能。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-163">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

 <span data-ttu-id="8bfbe-164">您的自訂控制項，會有相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-164">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="8bfbe-165">這可讓您建立專為您的自訂控制項的獨特設計經驗。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-165">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

 <span data-ttu-id="8bfbe-166">您關聯控制項設計工具使用<xref:System.ComponentModel.DesignerAttribute>類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-166">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="8bfbe-167">因為您正在開發您的自訂控制項的整個設計階段行為，將實作自訂設計工具<xref:System.ComponentModel.Design.IRootDesigner>介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-167">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="8bfbe-168">若要定義自訂控制項和其自訂的設計工具</span><span class="sxs-lookup"><span data-stu-id="8bfbe-168">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="8bfbe-169">開啟`MarqueeControl`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-169">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-170">在檔案頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-170">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="8bfbe-171">新增<xref:System.ComponentModel.DesignerAttribute>至`MarqueeControl`類別宣告。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-171">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="8bfbe-172">這將自訂控制項與它的設計工具產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-172">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="8bfbe-173">開啟`MarqueeControlRootDesigner`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-173">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-174">在檔案頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-174">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="8bfbe-175">變更的宣告`MarqueeControlRootDesigner`繼承自<xref:System.Windows.Forms.Design.DocumentDesigner>類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-175">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="8bfbe-176">適用於<xref:System.ComponentModel.ToolboxItemFilterAttribute>來指定與設計工具的互動**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-176">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

     <span data-ttu-id="8bfbe-177">**附註**的定義`MarqueeControlRootDesigner`類別已經括在命名空間中稱為 「 MarqueeControlLibrary.Design。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-177">**Note** The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called "MarqueeControlLibrary.Design."</span></span> <span data-ttu-id="8bfbe-178">這個宣告會放在特殊的命名空間保留供設計相關的型別設計工具。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-178">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="8bfbe-179">定義的建構函式`MarqueeControlRootDesigner`類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-179">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="8bfbe-180">插入<xref:System.Diagnostics.Trace.WriteLine%2A>建構函式主體中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-180">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="8bfbe-181">這會是適用於偵錯之用。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-181">This will be useful for debugging purposes.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a><span data-ttu-id="8bfbe-182">建立您的自訂控制項的執行個體</span><span class="sxs-lookup"><span data-stu-id="8bfbe-182">Creating an Instance of Your Custom Control</span></span>
 <span data-ttu-id="8bfbe-183">若要觀察您的控制項的自訂設計階段行為，您將放置在表單上控制項的執行個體`MarqueeControlTest`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-183">To observe the custom design-time behavior of your control, you will place an instance of your control on the form in `MarqueeControlTest` project.</span></span>

### <a name="to-create-an-instance-of-your-custom-control"></a><span data-ttu-id="8bfbe-184">若要建立您的自訂控制項的執行個體</span><span class="sxs-lookup"><span data-stu-id="8bfbe-184">To create an instance of your custom control</span></span>

1. <span data-ttu-id="8bfbe-185">加入新<xref:System.Windows.Forms.UserControl>項目`MarqueeControlTest`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-185">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="8bfbe-186">提供新的原始程式檔的基底名稱的"DemoMarqueeControl。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-186">Give the new source file a base name of "DemoMarqueeControl."</span></span>

2. <span data-ttu-id="8bfbe-187">開啟`DemoMarqueeControl`檔案中**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-187">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-188">在檔案頂端，匯入`MarqueeControlLibrary`命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-188">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. <span data-ttu-id="8bfbe-189">變更的宣告`DemoMarqueeControl`繼承自`MarqueeControl`類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-189">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

2. <span data-ttu-id="8bfbe-190">建置專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-190">Build the project.</span></span>

3. <span data-ttu-id="8bfbe-191">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-191">Open `Form1` in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="8bfbe-192">尋找**MarqueeControlTest 元件**索引標籤中**工具箱**並將它開啟。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-192">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="8bfbe-193">拖曳`DemoMarqueeControl`從**工具箱**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-193">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

5. <span data-ttu-id="8bfbe-194">建置專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-194">Build the project.</span></span>

## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="8bfbe-195">設定設計階段偵錯的專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-195">Setting Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="8bfbe-196">當您開發自訂的設計階段經驗時，它必須偵錯您的控制項和元件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-196">When you are developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="8bfbe-197">沒有簡單的方式來設定您的專案，才能在設計階段偵錯。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-197">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="8bfbe-198">如需詳細資訊，請參閱[逐步解說：在設計階段偵錯自訂的 Windows Form 控制項](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-198">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="8bfbe-199">若要設定設計階段偵錯的專案</span><span class="sxs-lookup"><span data-stu-id="8bfbe-199">To set up the project for design-time debugging</span></span>

1. <span data-ttu-id="8bfbe-200">以滑鼠右鍵按一下`MarqueeControlLibrary`專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-200">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="8bfbe-201">在 「 MarqueeControlLibrary 屬性頁面 」 的對話方塊中，選取**偵錯**頁面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-201">In the "MarqueeControlLibrary Property Pages" dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="8bfbe-202">在 **起始動作**區段中，選取**起始外部程式**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-202">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="8bfbe-203">您將會讓偵錯個別的執行個體的 Visual Studio 中，按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來瀏覽 Visual Studio IDE。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-203">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="8bfbe-204">可執行檔的名稱是 devenv.exe，且如果您安裝的預設位置，其路徑為 %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-204">The name of the executable file is devenv.exe, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>

4. <span data-ttu-id="8bfbe-205">按一下 [確定] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-205">Click OK to close the dialog box.</span></span>

5. <span data-ttu-id="8bfbe-206">以滑鼠右鍵按一下`MarqueeControlLibrary`專案，然後選取"設定為啟始專案 」 來啟用這個偵錯組態。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-206">Right-click the `MarqueeControlLibrary` project and select "Set as StartUp Project" to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="8bfbe-207">檢查點</span><span class="sxs-lookup"><span data-stu-id="8bfbe-207">Checkpoint</span></span>

<span data-ttu-id="8bfbe-208">您現在已準備好偵錯您的自訂控制項的設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-208">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="8bfbe-209">一旦您決定偵錯環境已正確設定時，您將測試的自訂控制項和自訂的設計工具之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-209">Once you have determined that the debugging environment is set up correctly, you will test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="8bfbe-210">若要測試的偵錯環境和設計工具關聯</span><span class="sxs-lookup"><span data-stu-id="8bfbe-210">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="8bfbe-211">開啟`MarqueeControlRootDesigner`中的原始程式檔**程式碼編輯器**並將中斷點放在<xref:System.Diagnostics.Trace.WriteLine%2A>陳述式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-211">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="8bfbe-212">按下 f5 鍵啟動偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-212">Press F5 to start the debugging session.</span></span> <span data-ttu-id="8bfbe-213">請注意，已建立 Visual Studio 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-213">Note that a new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="8bfbe-214">在 Visual Studio 的新執行個體，開啟 「 MarqueeControlTest 」 方案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-214">In the new instance of Visual Studio, open the "MarqueeControlTest" solution.</span></span> <span data-ttu-id="8bfbe-215">您可以選取，以輕鬆地尋找方案**最近使用的專案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-215">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="8bfbe-216">會列出 「 MarqueeControlTest.sln"方案檔，因為最近使用過的檔案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-216">The "MarqueeControlTest.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="8bfbe-217">開啟`DemoMarqueeControl`設計工具中。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-217">Open the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="8bfbe-218">請注意，Visual Studio 偵錯執行個體取得焦點於中斷點停止執行。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-218">Note that the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="8bfbe-219">按 f5 鍵繼續偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-219">Press F5 to continue the debugging session.</span></span>

<span data-ttu-id="8bfbe-220">到目前為止，所有項目都可供您開發及偵錯您的自訂控制項和其相關聯的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-220">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="8bfbe-221">本逐步解說的其餘部分將著重於實作的控制項和設計工具功能的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-221">The remainder of this walkthrough will concentrate on the details of implementing features of the control and the designer.</span></span>

## <a name="implementing-your-custom-control"></a><span data-ttu-id="8bfbe-222">實作您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-222">Implementing Your Custom Control</span></span>

<span data-ttu-id="8bfbe-223">`MarqueeControl`是<xref:System.Windows.Forms.UserControl>加上一些自訂。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-223">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="8bfbe-224">它會公開兩種方法： `Start`，這會啟動跑馬燈動畫和`Stop`，這樣會停止動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-224">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="8bfbe-225">因為`MarqueeControl`包含子控制項，可實作`IMarqueeWidget`介面，`Start`並`Stop`列舉每一個子控制項和呼叫`StartMarquee`和`StopMarquee`方法，分別在每個子控制項實作`IMarqueeWidget`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-225">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="8bfbe-226">外觀`MarqueeBorder`並`MarqueeText`視版面配置控制項，而讓`MarqueeControl`覆寫<xref:System.Windows.Forms.Control.OnLayout%2A>方法，呼叫<xref:System.Windows.Forms.Control.PerformLayout%2A>上此類型的子控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-226">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="8bfbe-227">這是程度`MarqueeControl`自訂項目。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-227">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="8bfbe-228">執行階段功能由實作`MarqueeBorder`並`MarqueeText`控制項和設計階段功能由`MarqueeBorderDesigner`和`MarqueeControlRootDesigner`類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-228">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="8bfbe-229">若要實作自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-229">To implement your custom control</span></span>

1. <span data-ttu-id="8bfbe-230">開啟`MarqueeControl`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-230">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-231">實作`Start`和`Stop`方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-231">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="8bfbe-232">覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-232">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a><span data-ttu-id="8bfbe-233">建立您的自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-233">Creating a Child Control for Your Custom Control</span></span>

<span data-ttu-id="8bfbe-234">`MarqueeControl`將裝載之子控制項的兩種類型：`MarqueeBorder`控制項和`MarqueeText`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-234">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="8bfbe-235">`MarqueeBorder`：此控制項會繪製"號誌"其邊緣的框線。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-235">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="8bfbe-236">燈號閃爍在順序中，讓它們呈現為框線周圍移動。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-236">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="8bfbe-237">由呼叫屬性控制的燈號閃爍的速度`UpdatePeriod`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-237">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="8bfbe-238">其他幾個自訂屬性決定控制項的外觀的其他層面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-238">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="8bfbe-239">兩種方法，稱為`StartMarquee`和`StopMarquee`，控制動畫何時啟動和停止。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-239">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="8bfbe-240">`MarqueeText`：此控制項會繪製閃爍的字串。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-240">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="8bfbe-241">像是`MarqueeBorder`控制項，由控制文字的閃爍速度`UpdatePeriod`屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-241">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="8bfbe-242">`MarqueeText`控制項也有`StartMarquee`並`StopMarquee`方法與`MarqueeBorder`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-242">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="8bfbe-243">在設計階段`MarqueeControlRootDesigner`使得這些兩個控制項型別新增至`MarqueeControl`的任意組合。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-243">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="8bfbe-244">常見的兩個控制項的功能會納入介面呼叫`IMarqueeWidget`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-244">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="8bfbe-245">這可讓`MarqueeControl`探索任何跑馬燈相關的子控制項，並提供他們特殊的處理方式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-245">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="8bfbe-246">若要實作定期動畫的功能，您將使用<xref:System.ComponentModel.BackgroundWorker>物件從<xref:System.ComponentModel?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-246">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8bfbe-247">您可以使用<xref:System.Windows.Forms.Timer>物件，但是在許多`IMarqueeWidget`物件存在，單一 UI 執行緒可能無法跟上動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-247">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="8bfbe-248">若要建立您的自訂控制項的子控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-248">To create a child control for your custom control</span></span>

1. <span data-ttu-id="8bfbe-249">若要加入新的類別`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-249">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-250">提供新的原始程式檔的基底名稱的"IMarqueeWidget。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-250">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="8bfbe-251">開啟`IMarqueeWidget`中的原始程式檔**程式碼編輯器**並將變更從宣告`class`到`interface`:</span><span class="sxs-lookup"><span data-stu-id="8bfbe-251">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="8bfbe-252">將下列程式碼加入`IMarqueeWidget`介面來公開兩個方法和操作跑馬燈動畫的屬性：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-252">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="8bfbe-253">加入新**自訂控制項**項目`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-253">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-254">提供新的原始程式檔的基底名稱的"MarqueeText。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-254">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="8bfbe-255">拖曳<xref:System.ComponentModel.BackgroundWorker>元件從**工具箱**拖曳至您`MarqueeText`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-255">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="8bfbe-256">此元件可讓`MarqueeText`來以非同步方式更新自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-256">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="8bfbe-257">在 [屬性] 視窗中，設定<xref:System.ComponentModel.BackgroundWorker>元件的`WorkerReportsProgress`並<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性，以`true`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-257">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="8bfbe-258">這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件會定期引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件以及取消非同步的更新。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-258">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="8bfbe-259">如需詳細資訊，請參閱 < [BackgroundWorker 元件](backgroundworker-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-259">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="8bfbe-260">開啟`MarqueeText`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-260">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-261">在檔案頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-261">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="8bfbe-262">變更的宣告`MarqueeText`繼承自<xref:System.Windows.Forms.Label>實作和`IMarqueeWidget`介面：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-262">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="8bfbe-263">宣告對應至公開的屬性中，執行個體變數，並將它們初始化建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-263">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="8bfbe-264">`isLit`欄位可讓您決定是否要在所指定的色彩繪製文字`LightColor`屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-264">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="8bfbe-265">實作 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-265">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="8bfbe-266">`StartMarquee`並`StopMarquee`方法叫用<xref:System.ComponentModel.BackgroundWorker>元件<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法啟動或停止動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-266">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="8bfbe-267"><xref:System.ComponentModel.CategoryAttribute.Category%2A>並<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性套用至`UpdatePeriod`屬性使其出現在自訂區段的 [屬性] 視窗稱為 「 跑馬燈。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-267">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="8bfbe-268">實作屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-268">Implement the property accessors.</span></span> <span data-ttu-id="8bfbe-269">您將會公開 （expose) 給用戶端的兩個屬性：`LightColor`和`DarkColor`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-269">You will expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="8bfbe-270"><xref:System.ComponentModel.CategoryAttribute.Category%2A>和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性套用至這些屬性，因此屬性會出現在自訂區段的 [屬性] 視窗稱為 「 跑馬燈。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-270">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="8bfbe-271">實作的處理常式<xref:System.ComponentModel.BackgroundWorker>元件的<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-271">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="8bfbe-272"><xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式會休息所指定的毫秒數`UpdatePeriod`然後引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，直到您的程式碼會藉由呼叫停止動畫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-272">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="8bfbe-273"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式切換其淺色與深色的閃爍的狀態之間的文字。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-273">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="8bfbe-274">覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，讓動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-274">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="8bfbe-275">按 F6 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-275">Press F6 to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="8bfbe-276">建立 MarqueeBorder 子控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-276">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="8bfbe-277">`MarqueeBorder`控制項是稍微複雜一點，比`MarqueeText`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-277">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="8bfbe-278">它有更多屬性和中的動畫<xref:System.Windows.Forms.Control.OnPaint%2A>方法會更為複雜。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-278">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="8bfbe-279">基本上，它是非常類似`MarqueeText`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-279">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="8bfbe-280">因為`MarqueeBorder`控制項可以具有子控制項，它必須要注意的<xref:System.Windows.Forms.Control.Layout>事件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-280">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="8bfbe-281">若要建立 MarqueeBorder 控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-281">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="8bfbe-282">加入新**自訂控制項**項目`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-282">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-283">提供新的原始程式檔的基底名稱的"MarqueeBorder。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-283">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="8bfbe-284">拖曳<xref:System.ComponentModel.BackgroundWorker>元件從**工具箱**拖曳至您`MarqueeBorder`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-284">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="8bfbe-285">此元件可讓`MarqueeBorder`來以非同步方式更新自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-285">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="8bfbe-286">在 [屬性] 視窗中，設定<xref:System.ComponentModel.BackgroundWorker>元件的`WorkerReportsProgress`並<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性，以`true`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-286">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="8bfbe-287">這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件會定期引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件以及取消非同步的更新。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-287">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="8bfbe-288">如需詳細資訊，請參閱 < [BackgroundWorker 元件](backgroundworker-component.md)。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-288">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="8bfbe-289">在 [屬性] 視窗中，按一下 [事件] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-289">In the Properties window, click the Events button.</span></span> <span data-ttu-id="8bfbe-290">附加的處理常式<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-290">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="8bfbe-291">開啟`MarqueeBorder`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-291">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-292">在檔案頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-292">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="8bfbe-293">變更的宣告`MarqueeBorder`繼承自<xref:System.Windows.Forms.Panel>實作和`IMarqueeWidget`介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-293">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="8bfbe-294">宣告來管理兩個列舉`MarqueeBorder`控制項的狀態： `MarqueeSpinDirection`，以決定在其中燈號"旋轉"邊框，方向和`MarqueeLightShape`，以決定 圖形的燈號 （正方形或循環）。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-294">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="8bfbe-295">將這些宣告之前`MarqueeBorder`類別宣告。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-295">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="8bfbe-296">宣告對應至公開的屬性中，執行個體變數，並將它們初始化建構函式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-296">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="8bfbe-297">實作 `IMarqueeWidget` 介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-297">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="8bfbe-298">`StartMarquee`並`StopMarquee`方法叫用<xref:System.ComponentModel.BackgroundWorker>元件<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法啟動或停止動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-298">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="8bfbe-299">因為`MarqueeBorder`控制項可以包含子控制項`StartMarquee`方法會列舉所有的子控制項和呼叫`StartMarquee`那些實作`IMarqueeWidget`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-299">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="8bfbe-300">`StopMarquee`方法有類似的實作。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-300">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="8bfbe-301">實作屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-301">Implement the property accessors.</span></span> <span data-ttu-id="8bfbe-302">`MarqueeBorder`控制項有數個屬性來控制其外觀。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-302">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="8bfbe-303">實作的處理常式<xref:System.ComponentModel.BackgroundWorker>元件的<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-303">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="8bfbe-304"><xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式會休息所指定的毫秒數`UpdatePeriod`然後引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，直到您的程式碼會藉由呼叫停止動畫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-304">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="8bfbe-305"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式會遞增的 「 基底 」 的光線，從中淡/濃狀態的其他燈號決定，並呼叫位置<xref:System.Windows.Forms.Control.Refresh%2A>方法，讓重新繪製它自己的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-305">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="8bfbe-306">實作 helper 方法，`IsLit`和`DrawLight`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-306">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="8bfbe-307">`IsLit`方法決定的指定位置的燈號色彩。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-307">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="8bfbe-308">「 引發 」 的燈號以所指定的色彩繪製`LightColor`屬性，和 「 暗色調 」 中所指定的色彩繪製`DarkColor`屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-308">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="8bfbe-309">`DrawLight`方法繪製的光線，使用適當的色彩、 形狀和位置。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-309">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="8bfbe-310">覆寫<xref:System.Windows.Forms.Control.OnLayout%2A>和<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-310">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="8bfbe-311"><xref:System.Windows.Forms.Control.OnPaint%2A>方法會繪製的邊緣的燈號`MarqueeBorder`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-311">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="8bfbe-312">因為<xref:System.Windows.Forms.Control.OnPaint%2A>方法而定的尺寸`MarqueeBorder`控制項，您需要每次配置變更時呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-312">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="8bfbe-313">若要這麼做，請覆寫<xref:System.Windows.Forms.Control.OnLayout%2A>並呼叫<xref:System.Windows.Forms.Control.Refresh%2A>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-313">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="8bfbe-314">建立自訂的設計工具，以遮蔽和篩選屬性</span><span class="sxs-lookup"><span data-stu-id="8bfbe-314">Creating a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="8bfbe-315">`MarqueeControlRootDesigner`類別提供之根目錄設計工具的實作。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-315">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="8bfbe-316">這個設計工具中，除了作`MarqueeControl`，您必須特別相關聯的自訂設計工具`MarqueeBorder`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-316">In addition to this designer, which operates on the `MarqueeControl`, you will need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="8bfbe-317">這個設計工具提供自訂的根目錄設計工具的內容中適當的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-317">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="8bfbe-318">具體而言，`MarqueeBorderDesigner`將 「 遮蔽 」，並篩選出某些屬性`MarqueeBorder`控制項，變更與設計環境互動。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-318">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="8bfbe-319">攔截呼叫元件的屬性存取子就是所謂 「 遮蔽 」。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-319">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="8bfbe-320">它可讓設計工具可以追蹤使用者所設定的值，並選擇性地將該值傳遞至所設計的元件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-320">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="8bfbe-321">針對此範例中，<xref:System.Windows.Forms.Control.Visible%2A>及<xref:System.Windows.Forms.Control.Enabled%2A>屬性會被遮蔽`MarqueeBorderDesigner`，這可防止進行使用者`MarqueeBorder`不可見還是在設計階段期間停用的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-321">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="8bfbe-322">設計工具也可以加入或移除屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-322">Designers can also add and remove properties.</span></span> <span data-ttu-id="8bfbe-323">此範例中，如<xref:System.Windows.Forms.Control.Padding%2A>屬性將會移除在設計階段，因為`MarqueeBorder`控制項以程式設計方式設定的燈號所指定大小所根據的邊框間距`LightSize`屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-323">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="8bfbe-324">基底類別`MarqueeBorderDesigner`是<xref:System.ComponentModel.Design.ComponentDesigner>，其中包含可以變更屬性、 屬性和事件在設計階段控制項所公開的方法：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-324">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="8bfbe-325">變更時使用這些方法的元件的公用介面，您必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-325">When changing the public interface of a component using these methods, you must follow these rules:</span></span>

- <span data-ttu-id="8bfbe-326">新增或移除項目中的`PreFilter`只方法</span><span class="sxs-lookup"><span data-stu-id="8bfbe-326">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="8bfbe-327">修改現有的項目中`PostFilter`只方法</span><span class="sxs-lookup"><span data-stu-id="8bfbe-327">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="8bfbe-328">務必第一次呼叫基底實作`PreFilter`方法</span><span class="sxs-lookup"><span data-stu-id="8bfbe-328">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="8bfbe-329">一律上次呼叫基底實作`PostFilter`方法</span><span class="sxs-lookup"><span data-stu-id="8bfbe-329">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="8bfbe-330">遵守這些規則可確保所有的設計工具在設計階段環境中有一致的檢視所設計的所有元件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-330">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="8bfbe-331"><xref:System.ComponentModel.Design.ComponentDesigner>類別提供的字典來管理已遮蔽的屬性值這減輕您需要建立特定的執行個體變數。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-331">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="8bfbe-332">若要建立自訂的設計工具，以遮蔽和篩選的屬性</span><span class="sxs-lookup"><span data-stu-id="8bfbe-332">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="8bfbe-333">以滑鼠右鍵按一下**設計**資料夾，並加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-333">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="8bfbe-334">提供的原始程式檔的基底名稱的"MarqueeBorderDesigner。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-334">Give the source file a base name of "MarqueeBorderDesigner."</span></span>

2. <span data-ttu-id="8bfbe-335">開啟`MarqueeBorderDesigner`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-335">Open the `MarqueeBorderDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-336">在檔案頂端，匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-336">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="8bfbe-337">變更的宣告`MarqueeBorderDesigner`繼承自<xref:System.Windows.Forms.Design.ParentControlDesigner>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-337">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="8bfbe-338">因為`MarqueeBorder`控制項可以包含子控制項`MarqueeBorderDesigner`繼承自<xref:System.Windows.Forms.Design.ParentControlDesigner>，處理父子式互動。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-338">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="8bfbe-339">覆寫的基底實作<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-339">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="8bfbe-340">實作 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-340">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="8bfbe-341">這些實作陰影控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-341">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a><span data-ttu-id="8bfbe-342">處理元件的變更</span><span class="sxs-lookup"><span data-stu-id="8bfbe-342">Handling Component Changes</span></span>
 <span data-ttu-id="8bfbe-343">`MarqueeControlRootDesigner`類別提供的自訂設計階段體驗您`MarqueeControl`執行個體。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-343">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="8bfbe-344">大部分的設計階段功能繼承自<xref:System.Windows.Forms.Design.DocumentDesigner>類別; 您的程式碼將會實作兩個特定的自訂： 處理元件的變更，並加入設計工具動詞命令。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-344">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class; your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

 <span data-ttu-id="8bfbe-345">為使用者設計其`MarqueeControl`執行個體，您的根設計工具會追蹤對`MarqueeControl`及其子控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-345">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="8bfbe-346">設計階段環境提供便利的服務， <xref:System.ComponentModel.Design.IComponentChangeService>、 追蹤變更為元件的狀態。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-346">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

 <span data-ttu-id="8bfbe-347">您藉由查詢的環境中取得這項服務的參考<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-347">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="8bfbe-348">如果查詢成功，您的設計工具可以附加的處理常式<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>事件，並執行任何工作都必須在設計階段中維持一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-348">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

 <span data-ttu-id="8bfbe-349">若是`MarqueeControlRootDesigner`類別，您會呼叫<xref:System.Windows.Forms.Control.Refresh%2A>方法在每個`IMarqueeWidget`物件所包含的`MarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-349">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="8bfbe-350">這會導致`IMarqueeWidget`物件來重繪本身適當屬性，例如其父代時<xref:System.Windows.Forms.Control.Size%2A>會變更。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-350">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="8bfbe-351">若要處理元件的變更</span><span class="sxs-lookup"><span data-stu-id="8bfbe-351">To handle component changes</span></span>

1. <span data-ttu-id="8bfbe-352">開啟`MarqueeControlRootDesigner`中的原始程式檔**程式碼編輯器**，並覆寫<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-352">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="8bfbe-353">呼叫的基底實作<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>並查詢<xref:System.ComponentModel.Design.IComponentChangeService>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-353">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="8bfbe-354">實作<xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-354">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="8bfbe-355">測試傳送的元件型別，而且如果它是`IMarqueeWidget`，呼叫其<xref:System.Windows.Forms.Control.Refresh%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-355">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="8bfbe-356">將設計工具動詞命令加入至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="8bfbe-356">Adding Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="8bfbe-357">設計工具動詞命令是連結至事件處理常式的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-357">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="8bfbe-358">在設計階段，設計工具動詞命令會新增至元件之捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-358">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="8bfbe-359">如需詳細資訊，請參閱 <xref:System.ComponentModel.Design.DesignerVerb>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-359">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="8bfbe-360">您會在設計工具中加入兩個設計工具動詞命令：**執行測試**並**停止測試**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-360">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="8bfbe-361">這些動詞命令可讓您檢視的執行階段行為`MarqueeControl`在設計階段。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-361">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="8bfbe-362">這些動詞命令會加入至`MarqueeControlRootDesigner`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-362">These verbs will be added to the `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="8bfbe-363">當**執行測試**會叫用，動詞命令的事件處理常式會呼叫`StartMarquee`方法`MarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-363">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="8bfbe-364">當**停止測試**會叫用，動詞命令的事件處理常式會呼叫`StopMarquee`方法`MarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-364">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="8bfbe-365">實作`StartMarquee`並`StopMarquee`方法會呼叫這些方法上包含的控制項，可實作`IMarqueeWidget`，因此任何包含`IMarqueeWidget`控制項也會參與測試。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-365">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="8bfbe-366">若要將設計工具動詞命令加入至您的自訂設計工具</span><span class="sxs-lookup"><span data-stu-id="8bfbe-366">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="8bfbe-367">在 `MarqueeControlRootDesigner`類別中，新增名為事件處理常式`OnVerbRunTest`和`OnVerbStopTest`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-367">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="8bfbe-368">連線至其對應的設計工具動詞命令的這些事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-368">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="8bfbe-369">`MarqueeControlRootDesigner` 繼承<xref:System.ComponentModel.Design.DesignerVerbCollection>從其基底類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-369">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="8bfbe-370">您將建立兩個新<xref:System.ComponentModel.Design.DesignerVerb>物件，並將它們新增至這個集合中<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-370">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a><span data-ttu-id="8bfbe-371">建立自訂的 UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="8bfbe-371">Creating a Custom UITypeEditor</span></span>

<span data-ttu-id="8bfbe-372">當您建立使用者的自訂設計階段經驗時，它通常會建立自訂的互動，使用 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-372">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="8bfbe-373">您可以完成這藉由建立<xref:System.Drawing.Design.UITypeEditor>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-373">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span> <span data-ttu-id="8bfbe-374">如需詳細資訊，請參閱[如何：建立 UI 類型編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-374">For more information, see [How to: Create a UI Type Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120)).</span></span>

<span data-ttu-id="8bfbe-375">`MarqueeBorder`控制項會公開在 [屬性] 視窗中的數個屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-375">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="8bfbe-376">這些屬性，其中兩個`MarqueeSpinDirection`和`MarqueeLightShape`都由列舉型別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-376">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="8bfbe-377">為了說明 UI 類型編輯器，使用`MarqueeLightShape`屬性會有相關聯<xref:System.Drawing.Design.UITypeEditor>類別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-377">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="8bfbe-378">若要建立自訂的 UI 類型編輯器</span><span class="sxs-lookup"><span data-stu-id="8bfbe-378">To create a custom UI type editor</span></span>

1. <span data-ttu-id="8bfbe-379">開啟`MarqueeBorder`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-379">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="8bfbe-380">定義中的`MarqueeBorder`類別中，宣告類別，稱為`LightShapeEditor`衍生自<xref:System.Drawing.Design.UITypeEditor>。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-380">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="8bfbe-381">宣告<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>名的執行個體變數`editorService`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-381">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="8bfbe-382">覆寫 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-382">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="8bfbe-383">這個實作會傳回<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>，告知如何顯示在設計環境`LightShapeEditor`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-383">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="8bfbe-384">覆寫 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-384">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="8bfbe-385">這項實作查詢的設計環境<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>物件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-385">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="8bfbe-386">如果成功，它會建立`LightShapeSelectionControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-386">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="8bfbe-387"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>方法會叫用來啟動`LightShapeEditor`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-387">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="8bfbe-388">這個引動過程的傳回值會傳回用於設計環境。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-388">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="8bfbe-389">建立自訂的 UITypeEditor 檢視控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-389">Creating a View Control for your Custom UITypeEditor</span></span>

1. <span data-ttu-id="8bfbe-390">`MarqueeLightShape`屬性支援兩種類型的淺的圖形：`Square`和`Circle`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-390">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="8bfbe-391">您將建立用來專門用來以圖形方式顯示在 [屬性] 視窗中的這些值的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-391">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="8bfbe-392">此自訂控制項將由您<xref:System.Drawing.Design.UITypeEditor>與 [屬性] 視窗進行互動。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-392">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="8bfbe-393">若要建立的檢視控制項程式自訂的 ui 類型編輯器</span><span class="sxs-lookup"><span data-stu-id="8bfbe-393">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="8bfbe-394">加入新<xref:System.Windows.Forms.UserControl>項目`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-394">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-395">提供新的原始程式檔的基底名稱的"LightShapeSelectionControl。 」</span><span class="sxs-lookup"><span data-stu-id="8bfbe-395">Give the new source file a base name of "LightShapeSelectionControl."</span></span>

2. <span data-ttu-id="8bfbe-396">將兩個<xref:System.Windows.Forms.Panel>控制項從**工具箱**拖曳至`LightShapeSelectionControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-396">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="8bfbe-397">它們的名稱`squarePanel`和`circlePanel`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-397">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="8bfbe-398">將它們並排排列。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-398">Arrange them side by side.</span></span> <span data-ttu-id="8bfbe-399">設定<xref:System.Windows.Forms.Control.Size%2A>屬性兩者的<xref:System.Windows.Forms.Panel>控制項 （60，60）。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-399">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to (60, 60).</span></span> <span data-ttu-id="8bfbe-400">設定<xref:System.Windows.Forms.Control.Location%2A>屬性`squarePanel`控制項 （8，10）。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-400">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to (8, 10).</span></span> <span data-ttu-id="8bfbe-401">設定<xref:System.Windows.Forms.Control.Location%2A>屬性`circlePanel`控制權傳輸至 80 (10）。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-401">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to (80, 10).</span></span> <span data-ttu-id="8bfbe-402">最後，設定<xref:System.Windows.Forms.Control.Size%2A>屬性`LightShapeSelectionControl`到 150 (80）。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-402">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to (150, 80).</span></span>

3. <span data-ttu-id="8bfbe-403">開啟`LightShapeSelectionControl`中的原始程式檔**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-403">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="8bfbe-404">在檔案頂端，匯入<xref:System.Windows.Forms.Design?displayProperty=nameWithType>命名空間：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-404">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. <span data-ttu-id="8bfbe-405">實作<xref:System.Windows.Forms.Control.Click>事件處理常式`squarePanel`和`circlePanel`控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-405">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="8bfbe-406">這些方法叫用<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>來結束自訂<xref:System.Drawing.Design.UITypeEditor>編輯工作階段。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-406">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. <span data-ttu-id="8bfbe-407">宣告<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>名的執行個體變數`editorService`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-407">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. <span data-ttu-id="8bfbe-408">宣告`MarqueeLightShape`名的執行個體變數`lightShapeValue`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-408">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. <span data-ttu-id="8bfbe-409">在`LightShapeSelectionControl`建構函式，附加<xref:System.Windows.Forms.Control.Click>事件處理常式`squarePanel`並`circlePanel`控制項的<xref:System.Windows.Forms.Control.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-409">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="8bfbe-410">此外，定義指派的建構函式多載`MarqueeLightShape`值從設計環境來`lightShapeValue`欄位。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-410">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. <span data-ttu-id="8bfbe-411">在 <xref:System.ComponentModel.Component.Dispose%2A>方法中，卸離<xref:System.Windows.Forms.Control.Click>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-411">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. <span data-ttu-id="8bfbe-412">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-412">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="8bfbe-413">開啟 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl.Designer.vb 檔案，並移除的預設定義<xref:System.ComponentModel.Component.Dispose%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-413">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

5. <span data-ttu-id="8bfbe-414">實作 `LightShape` 屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-414">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. <span data-ttu-id="8bfbe-415">覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-415">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="8bfbe-416">這個實作會繪製實心的方形和圓形。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-416">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="8bfbe-417">它也會繪製框線一個形狀或其他反白選取的值。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-417">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a><span data-ttu-id="8bfbe-418">在設計工具中測試您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8bfbe-418">Testing your Custom Control in the Designer</span></span>

<span data-ttu-id="8bfbe-419">此時，您可以建置`MarqueeControlLibrary`專案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-419">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="8bfbe-420">測試您的實作，藉由建立繼承自控制項`MarqueeControl`類別和表單上使用它。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-420">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="8bfbe-421">若要建立自訂的 marqueecontrol 可能實作</span><span class="sxs-lookup"><span data-stu-id="8bfbe-421">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="8bfbe-422">在 Windows Form 設計工具中開啟 `DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-422">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="8bfbe-423">這會建立的執行個體`DemoMarqueeControl`輸入，並顯示它的執行個體中`MarqueeControlRootDesigner`型別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-423">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="8bfbe-424">在 [**工具箱**，開啟**MarqueeControlLibrary 元件**] 索引標籤。您會看到`MarqueeBorder`和`MarqueeText`可讓您選取的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-424">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="8bfbe-425">拖曳的一個執行個體`MarqueeBorder`控制項拖曳至`DemoMarqueeControl`設計介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-425">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="8bfbe-426">停駐此`MarqueeBorder`至父控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-426">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="8bfbe-427">拖曳的一個執行個體`MarqueeText`控制項拖曳至`DemoMarqueeControl`設計介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-427">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="8bfbe-428">建置方案。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-428">Build the solution.</span></span>

6. <span data-ttu-id="8bfbe-429">以滑鼠右鍵按一下`DemoMarqueeControl`並從快顯功能表選取**執行的測試**選項來啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-429">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="8bfbe-430">按一下 **停止測試**停止動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-430">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="8bfbe-431">在設計檢視中開啟 [Form1]。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-431">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="8bfbe-432">將兩個<xref:System.Windows.Forms.Button>表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-432">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="8bfbe-433">它們的名稱`startButton`和`stopButton`，並將變更<xref:System.Windows.Forms.Control.Text%2A>屬性值來**開始**並**停止**分別。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-433">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="8bfbe-434">實作<xref:System.Windows.Forms.Control.Click>兩個事件處理常式<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-434">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="8bfbe-435">在 [**工具箱**，開啟**MarqueeControlTest 元件**] 索引標籤。您會看到`DemoMarqueeControl`可讓您選取。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-435">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="8bfbe-436">拖曳的一個執行個體`DemoMarqueeControl`拖曳至**Form1**設計介面。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-436">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="8bfbe-437">在 <xref:System.Windows.Forms.Control.Click>事件處理常式，叫用`Start`並`Stop`上的方法`DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-437">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

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

1. <span data-ttu-id="8bfbe-438">設定`MarqueeControlTest`專案為啟始專案，然後執行它。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-438">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="8bfbe-439">您會看到表單顯示您`DemoMarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-439">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="8bfbe-440">按一下 **啟動**按鈕以啟動動畫。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-440">Click the **Start** button to start the animation.</span></span> <span data-ttu-id="8bfbe-441">您應該會看到閃爍的文字和框線周圍移動光線。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-441">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8bfbe-442">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8bfbe-442">Next Steps</span></span>

<span data-ttu-id="8bfbe-443">`MarqueeControlLibrary`示範自訂控制項和相關聯的設計工具的簡單實作。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-443">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="8bfbe-444">您可以在此範例更複雜數種方式：</span><span class="sxs-lookup"><span data-stu-id="8bfbe-444">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="8bfbe-445">變更的屬性值`DemoMarqueeControl`設計工具中。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-445">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="8bfbe-446">新增更多`MarqueBorder`控制，並將它們固定到其父執行個體，以建立巢狀的效果內。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-446">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="8bfbe-447">嘗試使用不同的設定，如`UpdatePeriod`和 light 相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-447">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="8bfbe-448">撰寫您自己的實作`IMarqueeWidget`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-448">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="8bfbe-449">您可以比方說，建立閃爍 「 neon 登 」 或動畫的正負號與多個映像。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-449">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="8bfbe-450">進一步自訂設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-450">Further customize the design-time experience.</span></span> <span data-ttu-id="8bfbe-451">您可以嘗試遮蔽其他屬性，但是<xref:System.Windows.Forms.Control.Enabled%2A>和<xref:System.Windows.Forms.Control.Visible%2A>，然後加入新的屬性。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-451">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="8bfbe-452">加入新的設計工具動詞命令，以簡化常見工作，像是停駐子控制項。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-452">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="8bfbe-453">授權`MarqueeControl`。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-453">License the `MarqueeControl`.</span></span> <span data-ttu-id="8bfbe-454">如需詳細資訊，請參閱[如何：授權元件和控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-454">For more information, see [How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120)).</span></span>

- <span data-ttu-id="8bfbe-455">控制如何序列化您的控制項，並為其產生程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-455">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="8bfbe-456">如需詳細資訊，請參閱 <<c0> [ 動態原始程式碼的產生和編譯](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="8bfbe-456">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8bfbe-457">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bfbe-457">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- <span data-ttu-id="8bfbe-458">[如何：建立採用設計階段功能的 Windows Form 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8bfbe-458">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>
- <span data-ttu-id="8bfbe-459">[擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8bfbe-459">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- <span data-ttu-id="8bfbe-460">[自訂設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8bfbe-460">[Custom Designers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))</span></span>
