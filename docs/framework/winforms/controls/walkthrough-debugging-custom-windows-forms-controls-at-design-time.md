---
title: "逐步解說：在設計階段偵錯自訂的 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fd38f6246d44bd24753d9c86a5b0b08819d3db7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="4f16e-102">逐步解說：在設計階段偵錯自訂的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-102">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="4f16e-103">當您建立自訂控制項時，您通常會發現它需要偵錯設計階段行為。</span><span class="sxs-lookup"><span data-stu-id="4f16e-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="4f16e-104">特別是如果您撰寫自訂的設計工具為您的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4f16e-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="4f16e-105">如需詳細資訊，請參閱[逐步解說： 建立 Windows Form 控制項，會利用的 Visual Studio 設計階段功能](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)。</span><span class="sxs-lookup"><span data-stu-id="4f16e-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
 <span data-ttu-id="4f16e-106">您可以偵錯使用 Visual Studio 中，您的自訂控制項，就像您會偵錯任何其他.NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="4f16e-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="4f16e-107">不同的是您要偵錯 Visual Studio 執行您的自訂控制項程式碼的個別執行個體</span><span class="sxs-lookup"><span data-stu-id="4f16e-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code</span></span>  
  
 <span data-ttu-id="4f16e-108">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="4f16e-108">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="4f16e-109">建立 Windows Form 專案以裝載您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-109">Creating a Windows Forms project to host your custom control</span></span>  
  
-   <span data-ttu-id="4f16e-110">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="4f16e-110">Creating a control library project</span></span>  
  
-   <span data-ttu-id="4f16e-111">將屬性加入至您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-111">Adding a property to your custom control</span></span>  
  
-   <span data-ttu-id="4f16e-112">將您的自訂控制項加入至主表單</span><span class="sxs-lookup"><span data-stu-id="4f16e-112">Adding your custom control to the host form</span></span>  
  
-   <span data-ttu-id="4f16e-113">設計階段偵錯的專案設定</span><span class="sxs-lookup"><span data-stu-id="4f16e-113">Setting up the project for design-time debugging</span></span>  
  
-   <span data-ttu-id="4f16e-114">在設計階段偵錯您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-114">Debugging your custom control at design time</span></span>  
  
 <span data-ttu-id="4f16e-115">當您完成時，您必須了解偵錯自訂控制項的設計階段行為的必要工作。</span><span class="sxs-lookup"><span data-stu-id="4f16e-115">When you are finished, you will have an understanding of the tasks necessary for debugging the design-time behavior of a custom control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f16e-116">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="4f16e-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4f16e-117">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="4f16e-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4f16e-118">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="4f16e-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="4f16e-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="4f16e-119">Creating the Project</span></span>  
 <span data-ttu-id="4f16e-120">第一個步驟是建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-120">The first step is to create the application project.</span></span> <span data-ttu-id="4f16e-121">您將使用此專案來建置裝載自訂控制項的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4f16e-121">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="4f16e-122">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="4f16e-122">To create the project</span></span>  
  
-   <span data-ttu-id="4f16e-123">建立 Windows 應用程式專案，稱為 「 DebuggingExample"。</span><span class="sxs-lookup"><span data-stu-id="4f16e-123">Create a Windows Application project called "DebuggingExample".</span></span> <span data-ttu-id="4f16e-124">如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。</span><span class="sxs-lookup"><span data-stu-id="4f16e-124">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="4f16e-125">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="4f16e-125">Creating a Control Library Project</span></span>  
 <span data-ttu-id="4f16e-126">下一個步驟是建立控制項程式庫專案並設定自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4f16e-126">The next step is to create the control library project and set up the custom control.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="4f16e-127">若要建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="4f16e-127">To create the control library project</span></span>  
  
1.  <span data-ttu-id="4f16e-128">新增**Windows 控制項程式庫**專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-128">Add a **Windows Control Library** project to the solution.</span></span>  
  
2.  <span data-ttu-id="4f16e-129">加入新**UserControl** DebugControlLibrary 專案項目。</span><span class="sxs-lookup"><span data-stu-id="4f16e-129">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="4f16e-130">如需詳細資訊，請參閱[NIB： 如何： 加入新的專案項目](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。</span><span class="sxs-lookup"><span data-stu-id="4f16e-130">For details, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/en-us/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="4f16e-131">提供新的來源檔案的"DebugControl 「 基底名稱。</span><span class="sxs-lookup"><span data-stu-id="4f16e-131">Give the new source file a base name of "DebugControl".</span></span>  
  
3.  <span data-ttu-id="4f16e-132">使用**方案總管 中**，刪除專案的預設控制項的基底名稱與程式碼檔案中刪除 「`UserControl1`"。</span><span class="sxs-lookup"><span data-stu-id="4f16e-132">Using the **Solution Explorer**, delete the project's default control by deleting the code file with a base name of "`UserControl1`".</span></span> <span data-ttu-id="4f16e-133">如需詳細資訊，請參閱[NIB： 如何： 移除、 刪除和排除的項目](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。</span><span class="sxs-lookup"><span data-stu-id="4f16e-133">For details, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
4.  <span data-ttu-id="4f16e-134">建置方案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-134">Build the solution.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="4f16e-135">檢查點</span><span class="sxs-lookup"><span data-stu-id="4f16e-135">Checkpoint</span></span>  
 <span data-ttu-id="4f16e-136">此時，您將能夠看到您的自訂控制項中**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="4f16e-136">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>  
  
#### <a name="to-check-your-progress"></a><span data-ttu-id="4f16e-137">若要檢查您的進度</span><span class="sxs-lookup"><span data-stu-id="4f16e-137">To check your progress</span></span>  
  
-   <span data-ttu-id="4f16e-138">尋找新 索引標籤，並呼叫**DebugControlLibrary 元件**按一下來選取它。</span><span class="sxs-lookup"><span data-stu-id="4f16e-138">Find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="4f16e-139">當它開啟時，您會看到列為控制項**DebugControl**與它旁邊的預設圖示。</span><span class="sxs-lookup"><span data-stu-id="4f16e-139">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>  
  
## <a name="adding-a-property-to-your-custom-control"></a><span data-ttu-id="4f16e-140">將屬性加入至您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-140">Adding a Property to Your Custom Control</span></span>  
 <span data-ttu-id="4f16e-141">為了示範自訂控制項的程式碼在設計階段執行，您會加入屬性，以及實作屬性的程式碼中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="4f16e-141">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>  
  
#### <a name="to-add-a-property-to-your-custom-control"></a><span data-ttu-id="4f16e-142">若要將屬性加入自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-142">To add a property to your custom control</span></span>  
  
1.  <span data-ttu-id="4f16e-143">開啟**DebugControl**中**程式碼編輯器**。</span><span class="sxs-lookup"><span data-stu-id="4f16e-143">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="4f16e-144">將下列程式碼加入至類別定義：</span><span class="sxs-lookup"><span data-stu-id="4f16e-144">Add the following code to the class definition:</span></span>  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="4f16e-145">建置方案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-145">Build the solution.</span></span>  
  
## <a name="adding-your-custom-control-to-the-host-form"></a><span data-ttu-id="4f16e-146">將您的自訂控制項加入至主表單</span><span class="sxs-lookup"><span data-stu-id="4f16e-146">Adding Your Custom Control to the Host Form</span></span>  
 <span data-ttu-id="4f16e-147">若要偵錯您的自訂控制項的設計階段行為，您將自訂控制項類別的執行個體置於主表單。</span><span class="sxs-lookup"><span data-stu-id="4f16e-147">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a><span data-ttu-id="4f16e-148">若要將自訂控制項加入至主表單</span><span class="sxs-lookup"><span data-stu-id="4f16e-148">To add your custom control to the host form</span></span>  
  
1.  <span data-ttu-id="4f16e-149">在 「 DebuggingExample 」 專案中，開啟 Form1 中的**Windows Form 設計工具**。</span><span class="sxs-lookup"><span data-stu-id="4f16e-149">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>  
  
2.  <span data-ttu-id="4f16e-150">在**工具箱**，開啟**DebugControlLibrary 元件**索引標籤，將**DebugControl**拖曳至表單的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f16e-150">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>  
  
3.  <span data-ttu-id="4f16e-151">尋找`DemoString`中的自訂屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="4f16e-151">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="4f16e-152">請注意，您就可以變更其值，如同任何其他內容。</span><span class="sxs-lookup"><span data-stu-id="4f16e-152">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="4f16e-153">也請注意，當`DemoString`屬性，屬性的描述字串會出現在底部**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="4f16e-153">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="4f16e-154">設計階段偵錯的專案設定</span><span class="sxs-lookup"><span data-stu-id="4f16e-154">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="4f16e-155">若要偵錯自訂控制項的設計階段行為，您要偵錯 Visual Studio 執行您的自訂控制項程式碼的個別執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f16e-155">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="4f16e-156">若要設定的設計階段偵錯專案</span><span class="sxs-lookup"><span data-stu-id="4f16e-156">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="4f16e-157">以滑鼠右鍵按一下**DebugControlLibrary**專案中**方案總管 中**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4f16e-157">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4f16e-158">在**DebugControlLibrary**屬性工作表，選取**偵錯** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4f16e-158">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>  
  
     <span data-ttu-id="4f16e-159">在**起始動作**區段中，選取**啟動外部程式**。</span><span class="sxs-lookup"><span data-stu-id="4f16e-159">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="4f16e-160">您將無法偵錯 Visual Studio 中，個別執行個體，按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來瀏覽 Visual Studio IDE。</span><span class="sxs-lookup"><span data-stu-id="4f16e-160">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="4f16e-161">可執行檔的名稱是**devenv.exe**，且如果您安裝到預設位置，其路徑為 %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe。</span><span class="sxs-lookup"><span data-stu-id="4f16e-161">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
3.  <span data-ttu-id="4f16e-162">按一下 [確定]  關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4f16e-162">Click **OK** to close the dialog box.</span></span>  
  
4.  <span data-ttu-id="4f16e-163">以滑鼠右鍵按一下**DebugControlLibrary**專案，然後選取**設定為啟始專案**來啟用這個偵錯組態。</span><span class="sxs-lookup"><span data-stu-id="4f16e-163">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>  
  
## <a name="debugging-your-custom-control-at-design-time"></a><span data-ttu-id="4f16e-164">在設計階段偵錯您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-164">Debugging Your Custom Control at Design Time</span></span>  
 <span data-ttu-id="4f16e-165">現在您已準備好要在設計模式中執行時，偵錯自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4f16e-165">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="4f16e-166">當您啟動偵錯工作階段時，將建立的 Visual Studio 的新執行個體，以及您將使用它來載入 「 DebuggingExample 」 方案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-166">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="4f16e-167">當您開啟中的 Form1 **Form 設計工具**，將會建立您的自訂控制項的執行個體，而且會開始執行。</span><span class="sxs-lookup"><span data-stu-id="4f16e-167">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a><span data-ttu-id="4f16e-168">若要在設計階段偵錯您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-168">To debug your custom control at design time</span></span>  
  
1.  <span data-ttu-id="4f16e-169">開啟**DebugControl**原始程式檔中的**程式碼編輯器**，並將中斷點放在`Set`的存取子`DemoString`屬性。</span><span class="sxs-lookup"><span data-stu-id="4f16e-169">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>  
  
2.  <span data-ttu-id="4f16e-170">按 f5 鍵啟動偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="4f16e-170">Press F5 to start the debugging session.</span></span> <span data-ttu-id="4f16e-171">請注意，要建立的 Visual Studio 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="4f16e-171">Note that a new instance of Visual Studio is created.</span></span> <span data-ttu-id="4f16e-172">您可以區分兩種方式中的執行個體：</span><span class="sxs-lookup"><span data-stu-id="4f16e-172">You can distinguish between the instances in two ways:</span></span>  
  
    -   <span data-ttu-id="4f16e-173">偵錯的執行個體都有這個字**執行**標題列中</span><span class="sxs-lookup"><span data-stu-id="4f16e-173">The debugging instance has the word **Running** in its title bar</span></span>  
  
    -   <span data-ttu-id="4f16e-174">偵錯的執行個體**啟動**按鈕上其**偵錯**工具列停用</span><span class="sxs-lookup"><span data-stu-id="4f16e-174">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>  
  
     <span data-ttu-id="4f16e-175">偵錯的執行個體是設定您的中斷點。</span><span class="sxs-lookup"><span data-stu-id="4f16e-175">Your breakpoint is set in the debugging instance.</span></span>  
  
3.  <span data-ttu-id="4f16e-176">在 Visual Studio 的新執行個體，開啟 「 DebuggingExample 」 方案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-176">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="4f16e-177">您可以輕鬆地找到所選取的方案**最近使用的專案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="4f16e-177">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="4f16e-178">會列出 「 DebuggingExample.sln 」 方案檔，如此最近使用過的檔案。</span><span class="sxs-lookup"><span data-stu-id="4f16e-178">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="4f16e-179">開啟 Form1 中的**Form 設計工具**選取**DebugControl**控制項。</span><span class="sxs-lookup"><span data-stu-id="4f16e-179">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>  
  
5.  <span data-ttu-id="4f16e-180">值變更`DemoString`屬性。</span><span class="sxs-lookup"><span data-stu-id="4f16e-180">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="4f16e-181">請注意，當您認可變更時，Visual Studio 偵錯執行個體取得焦點，執行會在您的中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="4f16e-181">Note that when you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="4f16e-182">您可以逐步執行屬性存取子只做為您將任何其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="4f16e-182">You can single-step through the property accessor just as your would any other code.</span></span>  
  
6.  <span data-ttu-id="4f16e-183">當您完成您的偵錯工作階段，您可以結束解除裝載 Visual Studio 執行個體，或按一下**停止偵錯**偵錯的執行個體中的按鈕。</span><span class="sxs-lookup"><span data-stu-id="4f16e-183">When you are finished with your debugging session, you can exit by dismissing the hosted instance of Visual Studio or by clicking the **Stop Debugging** button in the debugging instance.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4f16e-184">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4f16e-184">Next Steps</span></span>  
 <span data-ttu-id="4f16e-185">現在，您可以在設計階段偵錯您的自訂控制項，有許多可能性擴充控制項的 Visual Studio IDE 的互動。</span><span class="sxs-lookup"><span data-stu-id="4f16e-185">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>  
  
-   <span data-ttu-id="4f16e-186">您可以使用<xref:System.ComponentModel.Component.DesignMode%2A>屬性<xref:System.ComponentModel.Component>類別撰寫程式碼，只會在設計階段執行。</span><span class="sxs-lookup"><span data-stu-id="4f16e-186">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="4f16e-187">如需詳細資訊，請參閱 <xref:System.ComponentModel.Component.DesignMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="4f16e-187">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>  
  
-   <span data-ttu-id="4f16e-188">有幾個屬性可以套用至控制項的屬性，以操作設計工具的自訂控制項的互動。</span><span class="sxs-lookup"><span data-stu-id="4f16e-188">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="4f16e-189">您可以找到這些屬性在<xref:System.ComponentModel?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="4f16e-189">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>  
  
-   <span data-ttu-id="4f16e-190">您可以撰寫自訂的設計工具為您的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4f16e-190">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="4f16e-191">這可讓您使用 Visual Studio 所公開的可擴充設計工具基礎結構的設計經驗的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="4f16e-191">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="4f16e-192">如需詳細資訊，請參閱[逐步解說： 建立 Windows Form 控制項，會利用的 Visual Studio 設計階段功能](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)。</span><span class="sxs-lookup"><span data-stu-id="4f16e-192">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f16e-193">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f16e-193">See Also</span></span>  
 [<span data-ttu-id="4f16e-194">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="4f16e-194">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [<span data-ttu-id="4f16e-195">如何： 存取設計階段服務</span><span class="sxs-lookup"><span data-stu-id="4f16e-195">How to: Access Design-Time Services</span></span>](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [<span data-ttu-id="4f16e-196">如何： 存取 Windows Form 中的設計階段支援</span><span class="sxs-lookup"><span data-stu-id="4f16e-196">How to: Access Design-Time Support in Windows Forms</span></span>](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
