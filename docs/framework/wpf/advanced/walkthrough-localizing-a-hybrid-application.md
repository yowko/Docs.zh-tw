---
title: 逐步解說：當地語系化混合應用程式
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111110"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="21fc8-102">逐步解說：當地語系化混合應用程式</span><span class="sxs-lookup"><span data-stu-id="21fc8-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="21fc8-103">本演練將介紹如何當地語系化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]基於 Windows 表單的混合應用程式中的元素。</span><span class="sxs-lookup"><span data-stu-id="21fc8-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a Windows Forms-based hybrid application.</span></span>

<span data-ttu-id="21fc8-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="21fc8-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="21fc8-105">創建 Windows 表單主項目目。</span><span class="sxs-lookup"><span data-stu-id="21fc8-105">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="21fc8-106">新增可當地語系化的內容。</span><span class="sxs-lookup"><span data-stu-id="21fc8-106">Adding localizable content.</span></span>

- <span data-ttu-id="21fc8-107">啟用當地語系化。</span><span class="sxs-lookup"><span data-stu-id="21fc8-107">Enabling localization.</span></span>

- <span data-ttu-id="21fc8-108">指派資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="21fc8-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="21fc8-109">使用 LocBaml 工具產生附屬組件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="21fc8-110">有關本演練中說明的任務的完整代碼清單，請參閱[當地語系化混合應用程式示例](https://go.microsoft.com/fwlink/?LinkID=160015)。</span><span class="sxs-lookup"><span data-stu-id="21fc8-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="21fc8-111">完成之後，就會有當地語系化的混合應用程式。</span><span class="sxs-lookup"><span data-stu-id="21fc8-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21fc8-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="21fc8-112">Prerequisites</span></span>

<span data-ttu-id="21fc8-113">您需要下列元件才能完成這個逐步解說：</span><span class="sxs-lookup"><span data-stu-id="21fc8-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="21fc8-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="21fc8-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="21fc8-115">建立 Windows Forms 主專案</span><span class="sxs-lookup"><span data-stu-id="21fc8-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="21fc8-116">第一步是創建 Windows 表單應用程式專案，並添加包含[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要當地語系化的內容的元素。</span><span class="sxs-lookup"><span data-stu-id="21fc8-116">The first step is to create the Windows Forms application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="21fc8-117">建立主專案</span><span class="sxs-lookup"><span data-stu-id="21fc8-117">To create the host project</span></span>

1. <span data-ttu-id="21fc8-118">創建名為`LocalizingWpfInWf`**的 WPF 應用**專案。</span><span class="sxs-lookup"><span data-stu-id="21fc8-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="21fc8-119">（**檔** > **新專案** > **Project** > **Classic Desktop** > **WPF Application\*\*\*\*Visual Basic\*\*\*\*Visual C#** 視覺化C#或視覺化基本經典桌面WPF應用程式）。 > </span><span class="sxs-lookup"><span data-stu-id="21fc8-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="21fc8-120">向專案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>添加調用`SimpleControl`的元素。</span><span class="sxs-lookup"><span data-stu-id="21fc8-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="21fc8-121">使用<xref:System.Windows.Forms.Integration.ElementHost>控制項在表單上`SimpleControl`放置元素。</span><span class="sxs-lookup"><span data-stu-id="21fc8-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="21fc8-122">有關詳細資訊，請參閱[演練：在 Windows 表單中託管 3D WPF 複合控制項](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="21fc8-122">For more information, see [Walkthrough: Hosting a 3D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="21fc8-123">新增可當地語系化的內容</span><span class="sxs-lookup"><span data-stu-id="21fc8-123">Adding Localizable Content</span></span>

<span data-ttu-id="21fc8-124">接下來，您將添加 Windows 表單標籤控制項，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]並將元素的內容設置為可當地語系化字串。</span><span class="sxs-lookup"><span data-stu-id="21fc8-124">Next, you will add a Windows Forms label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="21fc8-125">新增可當地語系化的內容</span><span class="sxs-lookup"><span data-stu-id="21fc8-125">To add localizable content</span></span>

1. <span data-ttu-id="21fc8-126">在**解決方案資源管理器中**，按兩下**SimpleControl.xaml**以在 WPF 設計器中打開它。</span><span class="sxs-lookup"><span data-stu-id="21fc8-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="21fc8-127">使用以下代碼設置<xref:System.Windows.Controls.Button>控制項的內容。</span><span class="sxs-lookup"><span data-stu-id="21fc8-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="21fc8-128">在**解決方案資源管理器中**，按兩下**Form1**以在 Windows 表單設計器中打開它。</span><span class="sxs-lookup"><span data-stu-id="21fc8-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="21fc8-129">打開**工具箱**並按兩下**標籤**以向表單添加標籤控制項。</span><span class="sxs-lookup"><span data-stu-id="21fc8-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="21fc8-130">將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值設定為 `"Hello"`。</span><span class="sxs-lookup"><span data-stu-id="21fc8-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="21fc8-131">按**F5**生成並運行應用程式。</span><span class="sxs-lookup"><span data-stu-id="21fc8-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="21fc8-132">元素`SimpleControl`和標籤控制項都顯示文本 **"你好"。**</span><span class="sxs-lookup"><span data-stu-id="21fc8-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="21fc8-133">啟用當地語系化</span><span class="sxs-lookup"><span data-stu-id="21fc8-133">Enabling Localization</span></span>

<span data-ttu-id="21fc8-134">Windows Forms 設計工具提供在附屬組件中啟用當地語系化的設定。</span><span class="sxs-lookup"><span data-stu-id="21fc8-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="21fc8-135">啟用當地語系化</span><span class="sxs-lookup"><span data-stu-id="21fc8-135">To enable localization</span></span>

1. <span data-ttu-id="21fc8-136">在**解決方案資源管理器**中，按兩下**Form1.cs**在 Windows 表單設計器中打開它。</span><span class="sxs-lookup"><span data-stu-id="21fc8-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="21fc8-137">在 **"屬性"** 視窗中，將表單的**可當地語系化**屬性的值設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="21fc8-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="21fc8-138">在 **"屬性"** 視窗中，將**語言**屬性的值設置為**西班牙文（西班牙）。**</span><span class="sxs-lookup"><span data-stu-id="21fc8-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="21fc8-139">在 [Windows Forms 設計工具] 中，選取 Label 控制項。</span><span class="sxs-lookup"><span data-stu-id="21fc8-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="21fc8-140">在 **"屬性"** 視窗中，將<xref:System.Windows.Forms.Control.Text%2A>屬性的值設置為`"Hola"`。</span><span class="sxs-lookup"><span data-stu-id="21fc8-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="21fc8-141">名為 Form1.es-ES.resx 的新資源檔會新增至專案。</span><span class="sxs-lookup"><span data-stu-id="21fc8-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="21fc8-142">在**解決方案資源管理器**中，按右鍵**Form1.cs**並按一下 **"查看代碼**"以在代碼編輯器中打開它。</span><span class="sxs-lookup"><span data-stu-id="21fc8-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="21fc8-143">將以下代碼複製到建構函式`Form1`中，在調用 之前到`InitializeComponent`。</span><span class="sxs-lookup"><span data-stu-id="21fc8-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="21fc8-144">在**解決方案資源管理器中**，按右鍵 **"當地語系化 WpfinWf"，** 然後按一下 **"卸載專案**"。</span><span class="sxs-lookup"><span data-stu-id="21fc8-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="21fc8-145">專案名稱標記為 **（不可用）。**</span><span class="sxs-lookup"><span data-stu-id="21fc8-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="21fc8-146">按右鍵 **"當地語系化 WpfinWf**"，然後按一下 **"編輯當地語系化 WpfinWf.csproj**"。</span><span class="sxs-lookup"><span data-stu-id="21fc8-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="21fc8-147">隨即在程式碼編輯器中開啟專案檔。</span><span class="sxs-lookup"><span data-stu-id="21fc8-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="21fc8-148">將以下行複製到專案檔案中的第`PropertyGroup`一行。</span><span class="sxs-lookup"><span data-stu-id="21fc8-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="21fc8-149">儲存並關閉專案檔。</span><span class="sxs-lookup"><span data-stu-id="21fc8-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="21fc8-150">在**解決方案資源管理器中**，按右鍵 **"當地語系化 WpfinWf"，** 然後按一下 **"重新載入專案**"。</span><span class="sxs-lookup"><span data-stu-id="21fc8-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="21fc8-151">指派資源識別碼</span><span class="sxs-lookup"><span data-stu-id="21fc8-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="21fc8-152">您可以使用資源識別碼，將可當地語系化的內容對應至資源組件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="21fc8-153">當您指定`updateuid`選項時，MsBuild.exe 應用程式會自動分配資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="21fc8-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="21fc8-154">指派資源識別碼</span><span class="sxs-lookup"><span data-stu-id="21fc8-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="21fc8-155">從"開始"功能表中，打開視覺化工作室的開發人員命令提示。</span><span class="sxs-lookup"><span data-stu-id="21fc8-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="21fc8-156">使用下列命令，將資源識別碼指派給可當地語系化的內容。</span><span class="sxs-lookup"><span data-stu-id="21fc8-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="21fc8-157">在**解決方案資源管理器中**，按兩下**SimpleControl.xaml**以在代碼編輯器中打開它。</span><span class="sxs-lookup"><span data-stu-id="21fc8-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="21fc8-158">您將看到該`msbuild`命令已將`Uid`該屬性添加到所有元素。</span><span class="sxs-lookup"><span data-stu-id="21fc8-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="21fc8-159">這有助於透過資源識別碼指派進行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="21fc8-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="21fc8-160">按 **F6** 以建立方案。</span><span class="sxs-lookup"><span data-stu-id="21fc8-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="21fc8-161">使用 LocBaml 產生附屬組件</span><span class="sxs-lookup"><span data-stu-id="21fc8-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="21fc8-162">當地語系化的內容存儲在僅資源附屬*程式集*中。</span><span class="sxs-lookup"><span data-stu-id="21fc8-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="21fc8-163">使用命令列工具 LocBaml.exe 為您的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容生成當地語系化程式集。</span><span class="sxs-lookup"><span data-stu-id="21fc8-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="21fc8-164">產生附屬組件</span><span class="sxs-lookup"><span data-stu-id="21fc8-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="21fc8-165">將 LocBaml.exe 複製至專案的 obj\Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21fc8-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="21fc8-166">有關詳細資訊，請參閱[當地語系化應用程式](how-to-localize-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="21fc8-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="21fc8-167">在 [命令提示字元] 視窗中，使用下列命令來將資源字串擷取至暫存檔。</span><span class="sxs-lookup"><span data-stu-id="21fc8-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="21fc8-168">使用 Visual Studio 或其他文字編輯器打開 temp.csv 檔。</span><span class="sxs-lookup"><span data-stu-id="21fc8-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="21fc8-169">將字串`"Hello"`替換為其西班牙文翻譯 。 `"Hola"`</span><span class="sxs-lookup"><span data-stu-id="21fc8-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="21fc8-170">儲存 temp.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="21fc8-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="21fc8-171">使用下列命令來產生已當地語系化的資源檔。</span><span class="sxs-lookup"><span data-stu-id="21fc8-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="21fc8-172">LocalizingWpfInWf.g.es-ES.resources 檔案會在 obj\Debug 資料夾中建立。</span><span class="sxs-lookup"><span data-stu-id="21fc8-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="21fc8-173">使用下列命令來建置已當地語系化的附屬組件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="21fc8-174">LocalizingWpfInWf.resources.dll 檔案會在 obj\Debug 資料夾中建立。</span><span class="sxs-lookup"><span data-stu-id="21fc8-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="21fc8-175">將 LocalizingWpfInWf.resources.dll 檔案複製至專案的 bin\Debug\es-ES 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21fc8-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="21fc8-176">取代現有檔案。</span><span class="sxs-lookup"><span data-stu-id="21fc8-176">Replace the existing file.</span></span>

8. <span data-ttu-id="21fc8-177">執行 LocalizingWpfInWf.exe，其位於專案的 bin\Debug 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="21fc8-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="21fc8-178">請不要重建應用程式，否則將會覆寫附屬組件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="21fc8-179">應用程式會顯示當地語系化字串，而不是英文字串。</span><span class="sxs-lookup"><span data-stu-id="21fc8-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="21fc8-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21fc8-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="21fc8-181">將應用程式當地語系化</span><span class="sxs-lookup"><span data-stu-id="21fc8-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="21fc8-182">[逐步解說：將 Windows Forms 當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="21fc8-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="21fc8-183">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="21fc8-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
