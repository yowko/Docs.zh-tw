---
title: 逐步解說：在設計階段偵錯自訂 Windows Forms 控制項
ms.date: 03/30/2017
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 824d8a7de8e9e37899cb84d6cee9621f84a5bc65
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015690"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a><span data-ttu-id="38f4f-102">逐步解說：在設計階段時, Debug 自訂 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="38f4f-102">Walkthrough: Debug Custom Windows Forms Controls at Design Time</span></span>

<span data-ttu-id="38f4f-103">當您建立自訂控制項時, 您通常會發現有必要將它的設計階段行為進行調試。</span><span class="sxs-lookup"><span data-stu-id="38f4f-103">When you create a custom control, you will often find it necessary to debug its design-time behavior.</span></span> <span data-ttu-id="38f4f-104">如果您要撰寫自訂控制項的自訂設計工具, 更是如此。</span><span class="sxs-lookup"><span data-stu-id="38f4f-104">This is especially true if you are authoring a custom designer for your custom control.</span></span> <span data-ttu-id="38f4f-105">如需詳細資訊[, 請參閱逐步解說:建立 Windows Forms 控制項, 利用 Visual Studio 的設計階段功能](creating-a-wf-control-design-time-features.md)。</span><span class="sxs-lookup"><span data-stu-id="38f4f-105">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

<span data-ttu-id="38f4f-106">您可以使用 Visual Studio 來進行自訂控制項的偵錯工具, 就像處理任何其他 .NET Framework 類別一樣。</span><span class="sxs-lookup"><span data-stu-id="38f4f-106">You can debug your custom controls using Visual Studio, just as you would debug any other .NET Framework classes.</span></span> <span data-ttu-id="38f4f-107">差別在於, 您將會對執行自訂控制項程式碼的個別 Visual Studio 實例進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="38f4f-107">The difference is that you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="38f4f-108">建立專案</span><span class="sxs-lookup"><span data-stu-id="38f4f-108">Create the project</span></span>

<span data-ttu-id="38f4f-109">第一個步驟是建立應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-109">The first step is to create the application project.</span></span> <span data-ttu-id="38f4f-110">您將使用此專案來建立裝載自訂控制項的應用程式。</span><span class="sxs-lookup"><span data-stu-id="38f4f-110">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="38f4f-111">在 Visual Studio 中, 建立 Windows 應用程式專案, 並將其命名為**DebuggingExample**。</span><span class="sxs-lookup"><span data-stu-id="38f4f-111">In Visual Studio, create a Windows Application project, and name it **DebuggingExample**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="38f4f-112">建立控制項程式庫專案</span><span class="sxs-lookup"><span data-stu-id="38f4f-112">Create the control library project</span></span>

1. <span data-ttu-id="38f4f-113">將**Windows 控制項程式庫**專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-113">Add a **Windows Control Library** project to the solution.</span></span>

2. <span data-ttu-id="38f4f-114">將新的**UserControl**專案新增至 DebugControlLibrary 專案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-114">Add a new **UserControl** item to the DebugControlLibrary project.</span></span> <span data-ttu-id="38f4f-115">將它命名為**DebugControl**。</span><span class="sxs-lookup"><span data-stu-id="38f4f-115">Name it **DebugControl**.</span></span>

3. <span data-ttu-id="38f4f-116">在**方案總管**中, 藉由刪除基底名稱為 UserControl1 的程式碼檔案, 刪除專案的預設控制項。</span><span class="sxs-lookup"><span data-stu-id="38f4f-116">In **Solution Explorer**, delete the project's default control by deleting the code file with a base name of UserControl1.</span></span>

4. <span data-ttu-id="38f4f-117">建置方案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-117">Build the solution.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="38f4f-118">檢查點</span><span class="sxs-lookup"><span data-stu-id="38f4f-118">Checkpoint</span></span>

<span data-ttu-id="38f4f-119">此時, 您將能夠在 [**工具箱**] 中看到您的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="38f4f-119">At this point, you will be able to see your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="38f4f-120">若要檢查您的進度, 請尋找名為 [ **DebugControlLibrary 元件**] 的新索引標籤, 然後按一下以選取它。</span><span class="sxs-lookup"><span data-stu-id="38f4f-120">To check your progress, find the new tab called **DebugControlLibrary Components** and click to select it.</span></span> <span data-ttu-id="38f4f-121">開啟時, 您會看到您的控制項列為**DebugControl** , 旁邊有預設圖示。</span><span class="sxs-lookup"><span data-stu-id="38f4f-121">When it opens, you will see your control listed as **DebugControl** with the default icon beside it.</span></span>

## <a name="add-a-property-to-your-custom-control"></a><span data-ttu-id="38f4f-122">將屬性新增至您的自訂控制項</span><span class="sxs-lookup"><span data-stu-id="38f4f-122">Add a property to your custom control</span></span>

<span data-ttu-id="38f4f-123">為了示範您自訂控制項的程式碼在設計階段執行, 您會在執行屬性的程式碼中加入屬性並設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="38f4f-123">To demonstrate that your custom control's code is running at design-time, you will add a property and set a breakpoint in the code that implements the property.</span></span>

1. <span data-ttu-id="38f4f-124">在程式**代碼編輯器**中開啟**DebugControl** 。</span><span class="sxs-lookup"><span data-stu-id="38f4f-124">Open **DebugControl** in the **Code Editor**.</span></span> <span data-ttu-id="38f4f-125">將下列程式碼新增至類別定義:</span><span class="sxs-lookup"><span data-stu-id="38f4f-125">Add the following code to the class definition:</span></span>

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

2. <span data-ttu-id="38f4f-126">建置方案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-126">Build the solution.</span></span>

## <a name="add-your-custom-control-to-the-host-form"></a><span data-ttu-id="38f4f-127">將自訂控制項新增至主機表單</span><span class="sxs-lookup"><span data-stu-id="38f4f-127">Add your custom control to the host form</span></span>

<span data-ttu-id="38f4f-128">若要對自訂控制項的設計階段行為進行偵錯工具, 您要將自訂控制項類別的實例放在主表單上。</span><span class="sxs-lookup"><span data-stu-id="38f4f-128">To debug the design-time behavior of your custom control, you will place an instance of the custom control class on a host form.</span></span>

1. <span data-ttu-id="38f4f-129">在 "DebuggingExample" 專案中, 開啟  **Windows Form 設計工具**中的 Form1。</span><span class="sxs-lookup"><span data-stu-id="38f4f-129">In the "DebuggingExample" project, open Form1 in the **Windows Forms Designer**.</span></span>

2. <span data-ttu-id="38f4f-130">在 [**工具箱**] 中, 開啟 [ **DebugControlLibrary 元件**] 索引標籤, 並將**DebugControl**實例拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="38f4f-130">In the **Toolbox**, open the **DebugControlLibrary Components** tab and drag a **DebugControl** instance onto the form.</span></span>

3. <span data-ttu-id="38f4f-131">在 [**屬性**] 視窗中尋找自訂屬性。`DemoString`</span><span class="sxs-lookup"><span data-stu-id="38f4f-131">Find the `DemoString` custom property in the **Properties** window.</span></span> <span data-ttu-id="38f4f-132">請注意, 您可以變更它的值, 就像任何其他屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="38f4f-132">Note that you can change its value as you would any other property.</span></span> <span data-ttu-id="38f4f-133">另請注意, 當`DemoString`您選取屬性時, 屬性的描述字串會顯示在 [**屬性**] 視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="38f4f-133">Also note that when the `DemoString` property is selected, the property's description string appears at the bottom of the **Properties** window.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="38f4f-134">設定專案以進行設計階段的偵錯工具</span><span class="sxs-lookup"><span data-stu-id="38f4f-134">Set up the project for design-time debugging</span></span>

<span data-ttu-id="38f4f-135">若要在自訂控制項的設計階段行為中進行偵錯工具, 您將會對執行自訂控制項程式碼的個別 Visual Studio 實例進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="38f4f-135">To debug your custom control's design-time behavior, you will debug a separate instance of Visual Studio that is running your custom control's code.</span></span>

1. <span data-ttu-id="38f4f-136">以滑鼠右鍵按一下 **方案總管**中的  **DebugControlLibrary**  專案, 然後選取 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="38f4f-136">Right-click on the **DebugControlLibrary** project in the **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="38f4f-137">在 [ **DebugControlLibrary** ] 屬性工作表中, 選取 [ **Debug** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="38f4f-137">In the **DebugControlLibrary** property sheet, select the **Debug** tab.</span></span>

     <span data-ttu-id="38f4f-138">在 [**起始動作**] 區段中, 選取 [**啟動外部程式**]。</span><span class="sxs-lookup"><span data-stu-id="38f4f-138">In the **Start Action** section, select **Start external program**.</span></span> <span data-ttu-id="38f4f-139">您將會 Visual Studio 的個別實例進行偵錯工具, 因此請按一下省略號![([Visual Studio](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕 (...)] 按鈕, 以流覽 Visual Studio 的 IDE。</span><span class="sxs-lookup"><span data-stu-id="38f4f-139">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="38f4f-140">可執行檔的名稱為**devenv**, 如果您安裝到預設位置, 其路徑為 *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\ \<edition > \Common7\IDE*。</span><span class="sxs-lookup"><span data-stu-id="38f4f-140">The name of the executable file is **devenv.exe**, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE*.</span></span>

3. <span data-ttu-id="38f4f-141">選取 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="38f4f-141">Select **OK** to close the dialog box.</span></span>

4. <span data-ttu-id="38f4f-142">以滑鼠右鍵按一下 [ **DebugControlLibrary** ] 專案, 然後選取 [**設定為啟始專案**], 以啟用此調試設定。</span><span class="sxs-lookup"><span data-stu-id="38f4f-142">Right-click the **DebugControlLibrary** project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="debug-your-custom-control-at-design-time"></a><span data-ttu-id="38f4f-143">在設計階段時, 對自訂控制項進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="38f4f-143">Debug your custom control at design time</span></span>

<span data-ttu-id="38f4f-144">現在您已準備好在設計模式中執行自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="38f4f-144">Now you are ready to debug your custom control as it runs in design mode.</span></span> <span data-ttu-id="38f4f-145">當您啟動調試階段時, 將會建立 Visual Studio 的新實例, 而您會使用它來載入 "DebuggingExample" 方案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-145">When you start the debugging session, a new instance of Visual Studio will be created, and you will use it to load the "DebuggingExample" solution.</span></span> <span data-ttu-id="38f4f-146">當您在**表單設計**工具中開啟 Form1 時, 將會建立自訂控制項的實例, 而且會開始執行。</span><span class="sxs-lookup"><span data-stu-id="38f4f-146">When you open Form1 in the **Forms Designer**, an instance of your custom control will be created and will start running.</span></span>

1. <span data-ttu-id="38f4f-147">在程式**代碼編輯器**中開啟**DebugControl**原始程式檔, 並將中斷點放`Set`在`DemoString`屬性的存取子上。</span><span class="sxs-lookup"><span data-stu-id="38f4f-147">Open the **DebugControl** source file in the **Code Editor** and place a breakpoint on the `Set` accessor of the `DemoString` property.</span></span>

2. <span data-ttu-id="38f4f-148">按**F5**啟動「調試」會話。</span><span class="sxs-lookup"><span data-stu-id="38f4f-148">Press **F5** to start the debugging session.</span></span> <span data-ttu-id="38f4f-149">建立 Visual Studio 的新實例。</span><span class="sxs-lookup"><span data-stu-id="38f4f-149">A new instance of Visual Studio is created.</span></span> <span data-ttu-id="38f4f-150">您可以透過兩種方式來區別實例:</span><span class="sxs-lookup"><span data-stu-id="38f4f-150">You can distinguish between the instances in two ways:</span></span>

    - <span data-ttu-id="38f4f-151">偵錯工具實例的標題列中有執行的單字</span><span class="sxs-lookup"><span data-stu-id="38f4f-151">The debugging instance has the word **Running** in its title bar</span></span>

    - <span data-ttu-id="38f4f-152">偵錯工具實例在其**調試**程式工具列上的 [**啟動**] 按鈕已停用</span><span class="sxs-lookup"><span data-stu-id="38f4f-152">The debugging instance has the **Start** button on its **Debug** toolbar disabled</span></span>

   <span data-ttu-id="38f4f-153">您的中斷點是在偵錯工具實例中設定。</span><span class="sxs-lookup"><span data-stu-id="38f4f-153">Your breakpoint is set in the debugging instance.</span></span>

3. <span data-ttu-id="38f4f-154">在 Visual Studio 的新實例中, 開啟 "DebuggingExample" 解決方案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-154">In the new instance of Visual Studio, open the "DebuggingExample" solution.</span></span> <span data-ttu-id="38f4f-155">您可以從 [檔案] 功能表選取 [**最近使用**的專案], 輕鬆地找到解決方案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-155">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="38f4f-156">"DebuggingExample" 方案檔會列為最近使用的檔案。</span><span class="sxs-lookup"><span data-stu-id="38f4f-156">The "DebuggingExample.sln" solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="38f4f-157">在**表單設計**工具中開啟 Form1, 然後選取 [ **DebugControl** ] 控制項。</span><span class="sxs-lookup"><span data-stu-id="38f4f-157">Open Form1 in the **Forms Designer** and select the **DebugControl** control.</span></span>

5. <span data-ttu-id="38f4f-158">變更 `DemoString` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="38f4f-158">Change the value of the `DemoString` property.</span></span> <span data-ttu-id="38f4f-159">當您認可變更時, Visual Studio 的偵錯工具實例會取得焦點, 而執行則會在您的中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="38f4f-159">When you commit the change, the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="38f4f-160">您可以單一步驟逐步執行屬性存取子, 就如同您對任何其他程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="38f4f-160">You can single-step through the property accessor just as your would any other code.</span></span>

6. <span data-ttu-id="38f4f-161">若要停止調試, 請結束 Visual Studio 的主控實例, 或在調試實例中選取 [**停止調試**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="38f4f-161">To stop debugging, exit the hosted instance of Visual Studio or select the **Stop Debugging** button in the debugging instance.</span></span>

## <a name="next-steps"></a><span data-ttu-id="38f4f-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="38f4f-162">Next steps</span></span>

<span data-ttu-id="38f4f-163">現在您可以在設計階段進行自訂控制項的偵錯工具, 展開控制項與 Visual Studio IDE 的互動有許多可能性。</span><span class="sxs-lookup"><span data-stu-id="38f4f-163">Now that you can debug your custom controls at design time, there are many possibilities for expanding your control's interaction with the Visual Studio IDE.</span></span>

- <span data-ttu-id="38f4f-164">您可以使用<xref:System.ComponentModel.Component>類別<xref:System.ComponentModel.Component.DesignMode%2A>的屬性來撰寫只會在設計階段執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="38f4f-164">You can use the <xref:System.ComponentModel.Component.DesignMode%2A> property of the <xref:System.ComponentModel.Component> class to write code that will only execute at design time.</span></span> <span data-ttu-id="38f4f-165">如需詳細資訊，請參閱 <xref:System.ComponentModel.Component.DesignMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="38f4f-165">For details, see <xref:System.ComponentModel.Component.DesignMode%2A>.</span></span>

- <span data-ttu-id="38f4f-166">您可以將數個屬性套用至控制項的屬性, 以操作自訂控制項與設計工具的互動。</span><span class="sxs-lookup"><span data-stu-id="38f4f-166">There are several attributes you can apply to your control's properties to manipulate your custom control's interaction with the designer.</span></span> <span data-ttu-id="38f4f-167">您可以在<xref:System.ComponentModel?displayProperty=nameWithType>命名空間中找到這些屬性。</span><span class="sxs-lookup"><span data-stu-id="38f4f-167">You can find these attributes in the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="38f4f-168">您可以撰寫自訂控制項的自訂設計工具。</span><span class="sxs-lookup"><span data-stu-id="38f4f-168">You can write a custom designer for your custom control.</span></span> <span data-ttu-id="38f4f-169">這可讓您使用 Visual Studio 所公開的可擴充設計工具基礎結構, 完全掌控設計經驗。</span><span class="sxs-lookup"><span data-stu-id="38f4f-169">This gives you complete control over the design experience using the extensible designer infrastructure exposed by Visual Studio.</span></span> <span data-ttu-id="38f4f-170">如需詳細資訊[, 請參閱逐步解說:建立 Windows Forms 控制項, 利用 Visual Studio 的設計階段功能](creating-a-wf-control-design-time-features.md)。</span><span class="sxs-lookup"><span data-stu-id="38f4f-170">For details, see [Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38f4f-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38f4f-171">See also</span></span>

- [<span data-ttu-id="38f4f-172">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="38f4f-172">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)
