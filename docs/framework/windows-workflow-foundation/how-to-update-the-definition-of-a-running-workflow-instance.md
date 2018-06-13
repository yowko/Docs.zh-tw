---
title: HOW TO：更新執行中工作流程執行個體的定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: 6492b08b45cf9e7767a14233c6aeb0dd648a3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520298"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="d7a08-102">HOW TO：更新執行中工作流程執行個體的定義</span><span class="sxs-lookup"><span data-stu-id="d7a08-102">How to: Update the Definition of a Running Workflow Instance</span></span>
<span data-ttu-id="d7a08-103">動態更新提供的機制可讓工作流程應用程式開發人員更新持續性工作流程執行個體的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="d7a08-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="d7a08-104">必要的變更可以是實作錯誤修復、新要求，或是適應突如其來的變化。</span><span class="sxs-lookup"><span data-stu-id="d7a08-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="d7a08-105">此教學課程中的步驟示範如何使用動態更新來修改保存的執行個體`v1`數字猜測工作流程來比對中引進的新功能[How to： 主機的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="d7a08-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7a08-106">若要下載完整的版或觀看影片逐步解說的教學課程，請參閱[Windows Workflow Foundation (WF45)-入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="d7a08-107">本主題內容</span><span class="sxs-lookup"><span data-stu-id="d7a08-107">In this topic</span></span>  
  
-   [<span data-ttu-id="d7a08-108">若要建立 CreateUpdateMaps 專案</span><span class="sxs-lookup"><span data-stu-id="d7a08-108">To create the CreateUpdateMaps project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [<span data-ttu-id="d7a08-109">更新 StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="d7a08-109">To update StateMachineNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [<span data-ttu-id="d7a08-110">更新 FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="d7a08-110">To update FlowchartNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [<span data-ttu-id="d7a08-111">更新 SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="d7a08-111">To update SequentialNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [<span data-ttu-id="d7a08-112">若要建置及執行 CreateUpdateMaps 應用程式</span><span class="sxs-lookup"><span data-stu-id="d7a08-112">To build and run the CreateUpdateMaps application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [<span data-ttu-id="d7a08-113">建置更新的工作流程組件</span><span class="sxs-lookup"><span data-stu-id="d7a08-113">To build the updated workflow assembly</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [<span data-ttu-id="d7a08-114">若要使用新的版本更新 WorkflowVersionMap</span><span class="sxs-lookup"><span data-stu-id="d7a08-114">To update WorkflowVersionMap with the new versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="d7a08-115">若要套用動態更新</span><span class="sxs-lookup"><span data-stu-id="d7a08-115">To apply the dynamic updates</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [<span data-ttu-id="d7a08-116">若要更新的工作流程執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d7a08-116">To run the application with the updated workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [<span data-ttu-id="d7a08-117">若要啟用 啟動工作流程的舊版本</span><span class="sxs-lookup"><span data-stu-id="d7a08-117">To enable starting previous versions of the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <a name="BKMK_CreateProject"></a> <span data-ttu-id="d7a08-118">若要建立 CreateUpdateMaps 專案</span><span class="sxs-lookup"><span data-stu-id="d7a08-118">To create the CreateUpdateMaps project</span></span>  
  
1.  <span data-ttu-id="d7a08-119">以滑鼠右鍵按一下**WF45GettingStartedTutorial**中**方案總管 中**選擇**新增**，**新專案**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="d7a08-120">在**已安裝**節點中，選取**Visual C#**， **Windows** (或**Visual Basic**， **Windows**)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7a08-121">依據設定哪個程式語言為 Visual Studio 主要語言而異，[ **Visual C#** ] 或 [ **Visual Basic** ] 節點可能會顯示在 [ **已安裝** ] 節點中的 [ **其他語言** ] 節點下。</span><span class="sxs-lookup"><span data-stu-id="d7a08-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="d7a08-122">確認已選取 [.NET Framework 版本] 下拉式清單中的 [ **.NET Framework 4.5** ]。</span><span class="sxs-lookup"><span data-stu-id="d7a08-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="d7a08-123">選取**主控台應用程式**從**Windows**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="d7a08-124">型別**CreateUpdateMaps**到**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="d7a08-125">以滑鼠右鍵按一下**CreateUpdateMaps**中**方案總管 中**選擇**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="d7a08-126">選取**Framework**從**組件**節點**加入參考**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="d7a08-127">型別**System.Activities**到**搜尋組件**方塊以篩選組件，並讓您更容易選取所需的參考。</span><span class="sxs-lookup"><span data-stu-id="d7a08-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>  
  
5.  <span data-ttu-id="d7a08-128">核取方塊旁的**System.Activities**從**搜尋結果**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
6.  <span data-ttu-id="d7a08-129">型別**序列化**到**搜尋組件**方塊中，並檢查旁邊的核取方塊**System.Runtime.Serialization**從**搜尋結果**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="d7a08-130">型別**System.Xaml**到**搜尋組件**方塊中，並檢查旁邊的核取方塊**System.Xaml**從**搜尋結果**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="d7a08-131">按一下**確定**關閉**參考管理員**並加入參考。</span><span class="sxs-lookup"><span data-stu-id="d7a08-131">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
9. <span data-ttu-id="d7a08-132">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.Statements  
    Imports System.Xaml  
    Imports System.Reflection  
    Imports System.IO  
    Imports System.Activities.XamlIntegration  
    Imports System.Activities.DynamicUpdate  
    Imports System.Runtime.Serialization  
    Imports Microsoft.VisualBasic.Activities  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.IO;  
    using System.Xaml;  
    using System.Reflection;  
    using System.Activities.XamlIntegration;  
    using System.Activities.DynamicUpdate;  
    using System.Runtime.Serialization;  
    using Microsoft.CSharp.Activities;  
    ```  
  
10. <span data-ttu-id="d7a08-133">將下列兩個字串成員加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. <span data-ttu-id="d7a08-134">將下列 `StartUpdate` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-135">此方法會將指定的 xaml 工作流程定義載入到 `ActivityBuilder`，然後呼叫 `DynamicUpdate.PrepareForUpdate`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="d7a08-136">`PrepareForUpdate` 會在 `ActivityBuilder` 中建立工作流程定義的複本。</span><span class="sxs-lookup"><span data-stu-id="d7a08-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="d7a08-137">修改工作流程定義後，會使用此複本和修改過的工作流程定義建立更新對應。</span><span class="sxs-lookup"><span data-stu-id="d7a08-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>  
  
    ```vb  
    Private Function StartUpdate(name As String) As ActivityBuilder  
        'Create the XamlXmlReaderSettings.  
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()  
        'In the XAML the "local" namespace referes to artifacts that come from   
        'the same project as the XAML. When loading XAML if the currently executing   
        'assembly is not the same assembly that was referred to as "local" in the XAML  
        'LocalAssembly must be set to the assembly containing the artifacts.  
        'Assembly.LoadFile requires an absolute path so convert this relative path  
        'to an absolute path.  
        readerSettings.LocalAssembly = Assembly.LoadFile(  
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
  
        Dim fullPath As String = Path.Combine(definitionPath, name)  
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)  
  
        'Load the workflow definition into an ActivityBuilder.  
        Dim wf As ActivityBuilder = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
  
        'PrepareForUpdate makes a copy of the workflow definition in the  
        'ActivityBuilder that is used for comparison when the update  
        'map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf)  
  
        Return wf  
    End Function  
    ```  
  
    ```csharp  
    private static ActivityBuilder StartUpdate(string name)  
    {  
        // Create the XamlXmlReaderSettings.  
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
        {  
            // In the XAML the "local" namespace referes to artifacts that come from   
            // the same project as the XAML. When loading XAML if the currently executing   
            // assembly is not the same assembly that was referred to as "local" in the XAML  
            // LocalAssembly must be set to the assembly containing the artifacts.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            LocalAssembly = Assembly.LoadFile(  
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
        };  
  
        string path = Path.Combine(definitionPath, name);  
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);  
  
        // Load the workflow definition into an ActivityBuilder.  
        ActivityBuilder wf = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
            as ActivityBuilder;  
  
        // PrepareForUpdate makes a copy of the workflow definition in the  
        // ActivityBuilder that is used for comparison when the update  
        // map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf);  
  
        return wf;  
    }  
    ```  
  
12. <span data-ttu-id="d7a08-138">接下來，將下列 `CreateUpdateMethod` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-139">這樣會呼叫 DynamicUpdateServices.CreateUpdateMap 來建立動態更新對應，然後使用指定名稱儲存更新對應。</span><span class="sxs-lookup"><span data-stu-id="d7a08-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="d7a08-140">此更新對應包含工作流程執行階段更新持續工作流程執行個體所需的資訊，該執行個體是使用包含在 `ActivityBuilder` 中的原始工作流程定義啟動的，這樣它才會使用更新的工作流程定義完成。</span><span class="sxs-lookup"><span data-stu-id="d7a08-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)  
        'Create the UpdateMap.  
        Dim map As DynamicUpdateMap =  
            DynamicUpdateServices.CreateUpdateMap(wf)  
  
        'Serialize it to a file.  
        Dim mapFullPath As String = Path.Combine(mapPath, name)  
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)  
            sz.WriteObject(fs, map)  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)  
    {  
        // Create the UpdateMap.  
        DynamicUpdateMap map =  
            DynamicUpdateServices.CreateUpdateMap(wf);  
  
        // Serialize it to a file.  
        string path = Path.Combine(mapPath, name);  
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));  
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))  
        {  
            sz.WriteObject(fs, map);  
        }  
    }  
    ```  
  
13. <span data-ttu-id="d7a08-141">將下列 `SaveUpdatedDefinition` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-142">這種方法會在建立更新對應之後，儲存更新的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="d7a08-142">This method saves the updated workflow definition once the update map is created.</span></span>  
  
    ```vb  
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)  
        Dim xamlPath As String = Path.Combine(definitionPath, name)  
        Dim sw As StreamWriter = File.CreateText(xamlPath)  
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(  
            New XamlXmlWriter(sw, New XamlSchemaContext()))  
        XamlServices.Save(xw, wf)  
        sw.Close()  
    End Sub  
    ```  
  
    ```csharp  
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)  
    {  
        string xamlPath = Path.Combine(definitionPath, name);  
        StreamWriter sw = File.CreateText(xamlPath);  
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(  
            new XamlXmlWriter(sw, new XamlSchemaContext()));  
        XamlServices.Save(xw, wf);  
        sw.Close();  
    }  
    ```  
  
###  <a name="BKMK_StateMachine"></a> <span data-ttu-id="d7a08-143">更新 StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="d7a08-143">To update StateMachineNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="d7a08-144">將 `CreateStateMachineUpdateMap` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  <span data-ttu-id="d7a08-145">呼叫 `StartUpdate`，然後取得工作流程的根 `StateMachine` 活動參考。</span><span class="sxs-lookup"><span data-stu-id="d7a08-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>  
  
    ```vb  
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
    'Get a reference to the root StateMachine activity.  
    Dim sm As StateMachine = wf.Implementation  
    ```  
  
    ```csharp  
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
    // Get a reference to the root StateMachine activity.  
    StateMachine sm = wf.Implementation as StateMachine;  
    ```  
  
3.  <span data-ttu-id="d7a08-146">接下來，更新兩個運算式`WriteLine`活動顯示使用者的猜測是太大或太小，使其一致中所做的更新是否[How to： 主機的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
    ```vb  
    'Update the Text of the two WriteLine activities that write the  
    'results of the user's guess. They are contained in the workflow as the  
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
    'Update the "too low" message.  
    Dim tooLow As WriteLine = guessLow.Then  
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
    'Update the "too high" message.  
    Dim tooHigh As WriteLine = guessLow.Else  
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
    ```  
  
    ```csharp  
    // Update the Text of the two WriteLine activities that write the  
    // results of the user's guess. They are contained in the workflow as the  
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    If guessLow = sm.States[1].Transitions[1].Action as If;  
  
    // Update the "too low" message.  
    WriteLine tooLow = guessLow.Then as WriteLine;  
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
    // Update the "too high" message.  
    WriteLine tooHigh = guessLow.Else as WriteLine;  
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
    ```  
  
4.  <span data-ttu-id="d7a08-147">接下來，加入顯示結束訊息的新 `WriteLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="d7a08-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>  
  
    ```vb  
    'Create the new WriteLine that displays the closing message.  
    Dim wl As New WriteLine() With  
    {  
        .Text = New VisualBasicValue(Of String) _  
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
    }  
  
    'Add it as the Action for the Guess Correct transition. The Guess Correct  
    'transition is the first transition of States[1]. The transitions are listed  
    'at the bottom of the State activity designer.  
    sm.States(1).Transitions(0).Action = wl  
    ```  
  
    ```csharp  
    // Create the new WriteLine that displays the closing message.  
    WriteLine wl = new WriteLine  
    {  
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
    };  
  
    // Add it as the Action for the Guess Correct transition. The Guess Correct  
    // transition is the first transition of States[1]. The transitions are listed  
    // at the bottom of the State activity designer.  
    sm.States[1].Transitions[0].Action = wl;  
    ```  
  
5.  <span data-ttu-id="d7a08-148">更新工作流程後，呼叫 `CreateUpdateMaps` 和 `SaveUpdatedDefinition`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="d7a08-149">`CreateUpdateMaps` 會建立和儲存 `DynamicUpdateMap`，而 `SaveUpdatedDefinition` 會儲存更新過的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="d7a08-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>  
  
    ```vb  
    'Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
    'Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    ```  
  
    ```csharp  
    // Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
    // Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    ```  
  
     <span data-ttu-id="d7a08-150">下列範例是完成的 `CreateStateMachineUpdateMap` 方法。</span><span class="sxs-lookup"><span data-stu-id="d7a08-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root StateMachine activity.  
        Dim sm As StateMachine = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
        'Update the "too low" message.  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Add it as the Action for the Guess Correct transition. The Guess Correct  
        'transition is the first transition of States[1]. The transitions are listed  
        'at the bottom of the State activity designer.  
        sm.States(1).Transitions(0).Action = wl  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root StateMachine activity.  
        StateMachine sm = wf.Implementation as StateMachine;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        If guessLow = sm.States[1].Transitions[1].Action as If;  
  
        // Update the "too low" message.  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Create the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Add it as the Action for the Guess Correct transition. The Guess Correct  
        // transition is the first transition of States[1]. The transitions are listed  
        // at the bottom of the State activity designer.  
        sm.States[1].Transitions[0].Action = wl;  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <a name="BKMK_Flowchart"></a> <span data-ttu-id="d7a08-151">更新 FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="d7a08-151">To update FlowchartNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="d7a08-152">將下列 `CreateFlowchartUpdateMethod` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-153">此方法類似 `CreateStateMachineUpdateMap`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="d7a08-154">它會從呼叫 `StartUpdate` 開始、更新流程圖工作流程定義，接著在儲存更新對應和更新的工作流程定後結束。</span><span class="sxs-lookup"><span data-stu-id="d7a08-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateFlowchartUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root Flowchart activity.  
        Dim fc As Flowchart = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'True and False action of the "Guess < Target" FlowDecision, which is  
        'Nodes[4].  
        Dim guessLow As FlowDecision = fc.Nodes(4)  
  
        'Update the "too low" message.  
        Dim trueStep As FlowStep = guessLow.True  
        Dim tooLow As WriteLine = trueStep.Action  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim falseStep As FlowStep = guessLow.False  
        Dim tooHigh As WriteLine = falseStep.Action  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Create a FlowStep to hold the WriteLine.  
        Dim closingStep As New FlowStep() With  
        {  
            .Action = wl  
        }  
  
        'Add this new FlowStep to the True action of the   
        '"Guess = Guess" FlowDecision  
        Dim guessCorrect As FlowDecision = fc.Nodes(3)  
        guessCorrect.True = closingStep  
  
        'Add the new FlowStep to the Nodes collection.  
        'If closingStep was replacing an existing node then  
        'we would need to remove that Step from the collection.  
        'In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateFlowchartUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root Flowchart activity.  
        Flowchart fc = wf.Implementation as Flowchart;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // True and False action of the "Guess < Target" FlowDecision, which is  
        // Nodes[4].  
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;  
  
        // Update the "too low" message.  
        FlowStep trueStep = guessLow.True as FlowStep;  
        WriteLine tooLow = trueStep.Action as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        FlowStep falseStep = guessLow.False as FlowStep;  
        WriteLine tooHigh = falseStep.Action as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Create a FlowStep to hold the WriteLine.  
        FlowStep closingStep = new FlowStep  
        {  
            Action = wl  
        };  
  
        // Add this new FlowStep to the True action of the   
        // "Guess == Guess" FlowDecision  
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;  
        guessCorrect.True = closingStep;  
  
        // Add the new FlowStep to the Nodes collection.  
        // If closingStep was replacing an existing node then  
        // we would need to remove that Step from the collection.  
        // In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");  
  
        //  Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <a name="BKMK_Sequential"></a> <span data-ttu-id="d7a08-155">更新 SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="d7a08-155">To update SequentialNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="d7a08-156">將下列 `CreateSequentialUpdateMethod` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-157">這個方法類似另外兩個方法。</span><span class="sxs-lookup"><span data-stu-id="d7a08-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="d7a08-158">它會從呼叫 `StartUpdate` 開始、更新循序工作流程定義，接著在儲存更新對應和更新的工作流程定後結束。</span><span class="sxs-lookup"><span data-stu-id="d7a08-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateSequentialUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root activity in the workflow.  
        Dim rootSequence As Sequence = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the "Guess < Target" If activity.  
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)  
        Dim gameBody As Sequence = gameLoop.Body  
        Dim guessCorrect As Statements.If = gameBody.Activities(2)  
        Dim guessLow As Statements.If = guessCorrect.Then  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateSequentialUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root activity in the workflow.  
        Sequence rootSequence = wf.Implementation as Sequence;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the "Guess < Target" If activity.  
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;  
        Sequence gameBody = gameLoop.Body as Sequence;  
        If guessCorrect = gameBody.Activities[2] as If;  
        If guessLow = guessCorrect.Then as If;  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="d7a08-159">若要建置及執行 CreateUpdateMaps 應用程式</span><span class="sxs-lookup"><span data-stu-id="d7a08-159">To build and run the CreateUpdateMaps application</span></span>  
  
1.  <span data-ttu-id="d7a08-160">更新 `Main` 方法，並加入下列三種方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d7a08-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="d7a08-161">這些方法會加入至下列區段。</span><span class="sxs-lookup"><span data-stu-id="d7a08-161">These methods are added in the following sections.</span></span> <span data-ttu-id="d7a08-162">每個方法會更新對應的數字猜測工作流程，並建立描述更新的 `DynamicUpdateMap`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>  
  
    ```vb  
    Sub Main()  
        'Create the update maps for the changes needed to the v1 activities  
        'so they match the v2 activities.  
        CreateSequentialUpdateMap()  
        CreateFlowchartUpdateMap()  
        CreateStateMachineUpdateMap()  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the update maps for the changes needed to the v1 activities  
        // so they match the v2 activities.  
        CreateSequentialUpdateMap();  
        CreateFlowchartUpdateMap();  
        CreateStateMachineUpdateMap();  
    }  
    ```  
  
2.  <span data-ttu-id="d7a08-163">以滑鼠右鍵按一下**CreateUpdateMaps**中**方案總管 中**選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
3.  <span data-ttu-id="d7a08-164">按 CTRL + SHIFT + B 建置方案，然後按 CTRL + F5 執行 `CreateUpdateMaps` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7a08-165">`CreateUpdateMaps`應用程式不會顯示任何狀態資訊，執行時，但如果您查看**NumberGuessWorkflowActivities_du**資料夾和**PreviousVersions**資料夾，您會看到已更新工作流程定義檔和更新對應。</span><span class="sxs-lookup"><span data-stu-id="d7a08-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>  
  
     <span data-ttu-id="d7a08-166">建立更新對應並更新工作流程定義後，下一步就是建置包含更新定義的更新工作流程組件。</span><span class="sxs-lookup"><span data-stu-id="d7a08-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>  
  
###  <a name="BKMK_BuildAssembly"></a> <span data-ttu-id="d7a08-167">建置更新的工作流程組件</span><span class="sxs-lookup"><span data-stu-id="d7a08-167">To build the updated workflow assembly</span></span>  
  
1.  <span data-ttu-id="d7a08-168">開啟第二個 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d7a08-168">Open a second instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="d7a08-169">選擇**開啟**，**專案/方案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="d7a08-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>  
  
3.  <span data-ttu-id="d7a08-170">瀏覽至**NumberGuessWorkflowActivities_du**您在建立的資料夾[How to： 主機的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)，選取**NumberGuessWorkflowActivities.csproj** (或**vbproj**)，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>  
  
4.  <span data-ttu-id="d7a08-171">在**方案總管 中**，以滑鼠右鍵按一下**SequentialNumberGuessWorkflow.xaml**選擇**從專案移除**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="d7a08-172">執行相同的動作， **FlowchartNumberGuessWorkflow.xaml**和**StateMachineNumberGuessWorkflow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="d7a08-173">此步驟會從專案中移除舊版的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="d7a08-173">This step removes the previous versions of the workflow definitions from the project.</span></span>  
  
5.  <span data-ttu-id="d7a08-174">選擇**加入現有項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="d7a08-174">Choose **Add Existing Item** from the **Project** menu.</span></span>  
  
6.  <span data-ttu-id="d7a08-175">瀏覽至**NumberGuessWorkflowActivities_du**您在建立的資料夾[How to： 主機的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
7.  <span data-ttu-id="d7a08-176">選擇**XAML 檔案 (\*.xaml;\*。xoml)** 從**檔案類型**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>  
  
8.  <span data-ttu-id="d7a08-177">選取**SequentialNumberGuessWorkflow_du.xaml**， **FlowchartNumberGuessWorkflow_du.xaml**，和**StateMachineNumberGuessWorkflow_du.xaml**按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7a08-178">按住 CTRL + 按一下以同時選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="d7a08-178">CTRL+Click to select multiple items at a time.</span></span>  
  
     <span data-ttu-id="d7a08-179">此步驟會將更新過的工作流程定義版本加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="d7a08-179">This step adds the updated versions of the workflow definitions to the project.</span></span>  
  
9. <span data-ttu-id="d7a08-180">按 CTRL+SHIFT+B 以建置專案。</span><span class="sxs-lookup"><span data-stu-id="d7a08-180">Press CTRL+SHIFT+B to build the project.</span></span>  
  
10. <span data-ttu-id="d7a08-181">選擇**關閉方案**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="d7a08-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="d7a08-182">方案檔的專案不是必要項目，因此按一下**否**以關閉 Visual Studio，而不儲存方案檔。</span><span class="sxs-lookup"><span data-stu-id="d7a08-182">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="d7a08-183">選擇**結束**從**檔案**以關閉 Visual Studio 的功能表。</span><span class="sxs-lookup"><span data-stu-id="d7a08-183">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>  
  
11. <span data-ttu-id="d7a08-184">開啟 Windows 檔案總管並瀏覽至**NumberGuessWorkflowActivities_du\bin\Debug**資料夾 (或**bin\Release**取決於您的專案設定)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>  
  
12. <span data-ttu-id="d7a08-185">重新命名**NumberGuessWorkflowActivities.dll**至**NumberGuessWorkflowActivities_v15.dll**，並將它複製到**PreviousVersions** 中建立的資料夾[How to： 裝載工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="d7a08-186">若要使用新的版本更新 WorkflowVersionMap</span><span class="sxs-lookup"><span data-stu-id="d7a08-186">To update WorkflowVersionMap with the new versions</span></span>  
  
1.  <span data-ttu-id="d7a08-187">切換回 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 的初始執行個體。</span><span class="sxs-lookup"><span data-stu-id="d7a08-187">Switch back to the initial instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="d7a08-188">按兩下**Numberguessworkflowhost** (或**Workflowversionmap.cs**) 下**NumberGuessWorkflowHost**專案加以開啟。</span><span class="sxs-lookup"><span data-stu-id="d7a08-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
3.  <span data-ttu-id="d7a08-189">將三個新的工作流程識別加入到六個現有工作流程識別宣告的正下方。</span><span class="sxs-lookup"><span data-stu-id="d7a08-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="d7a08-190">在本教學課程中，會使用 `1.5.0.0` 做為動態更新識別的 `WorkflowIdentity.Version`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="d7a08-191">這些新的 `v15` 工作流程識別，會為動態更新的持續性工作流程執行個體提供正確的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="d7a08-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
    'v1.5 (Dynamimc Update) identities.  
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
    ```  
  
    ```csharp  
    // Current version identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity;  
    static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
    // v1 identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
    // v1.5 (Dynamic Update) identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
    ```  
  
4.  <span data-ttu-id="d7a08-192">在建構函式結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="d7a08-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="d7a08-193">此程式碼會初始化動態更新工作流程識別、載入對應的工作流程定義，然後將定義加入至工作流程版本字典。</span><span class="sxs-lookup"><span data-stu-id="d7a08-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>  
  
    ```vb  
    'Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    'Add the dynamic update workflow identities to the dictionary along with  
    'the corresponding workflow definitions loaded from the v15 assembly.  
    'Assembly.LoadFile requires an absolute path so convert this relative path  
    'to an absolute path.  
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
    ```  
  
    ```csharp  
    // Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    // Add the dynamic update workflow identities to the dictionary along with  
    // the corresponding workflow definitions loaded from the v15 assembly.  
    // Assembly.LoadFile requires an absolute path so convert this relative path  
    // to an absolute path.  
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
    ```  
  
     <span data-ttu-id="d7a08-194">下列範例是已完成的 `WorkflowVersionMap` 類別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-194">The following example is the completed `WorkflowVersionMap` class.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
        'v1.5 (Dynamimc Update) identities.  
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
  
            'Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            'Add the previous version workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v1 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
  
            'Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            'Add the dynamic update workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v15 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        // v1 identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
        // v1.5 (Dynamic Update) identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
  
            // Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            // Add the previous version workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v1 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
  
            // Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            // Add the dynamic update workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v15 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {  
            return identity.ToString();  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="d7a08-195">按 CTRL+SHIFT+B 以建置專案。</span><span class="sxs-lookup"><span data-stu-id="d7a08-195">Press CTRL+SHIFT+B to build the project.</span></span>  
  
###  <a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="d7a08-196">若要套用動態更新</span><span class="sxs-lookup"><span data-stu-id="d7a08-196">To apply the dynamic updates</span></span>  
  
1.  <span data-ttu-id="d7a08-197">以滑鼠右鍵按一下**WF45GettingStartedTutorial**中**方案總管 中**選擇**新增**，**新專案**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="d7a08-198">在**已安裝**節點中，選取**Visual C#**， **Windows** (或**Visual Basic**， **Windows**)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7a08-199">依據設定哪個程式語言為 Visual Studio 主要語言而異，[ **Visual C#** ] 或 [ **Visual Basic** ] 節點可能會顯示在 [ **已安裝** ] 節點中的 [ **其他語言** ] 節點下。</span><span class="sxs-lookup"><span data-stu-id="d7a08-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="d7a08-200">確認已選取 [.NET Framework 版本] 下拉式清單中的 [ **.NET Framework 4.5** ]。</span><span class="sxs-lookup"><span data-stu-id="d7a08-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="d7a08-201">選取**主控台應用程式**從**Windows**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="d7a08-202">型別**ApplyDynamicUpdate**到**名稱**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="d7a08-203">以滑鼠右鍵按一下**ApplyDynamicUpdate**中**方案總管 中**選擇**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="d7a08-204">按一下**方案**旁的核取方塊和**NumberGuessWorkflowHost**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="d7a08-205">`ApplyDynamicUpdate` 需要此參考才能使用 `NumberGuessWorkflowHost.WorkflowVersionMap` 類別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>  
  
5.  <span data-ttu-id="d7a08-206">選取**Framework**從**組件**節點**加入參考**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="d7a08-207">型別**System.Activities**到**搜尋組件**方塊。</span><span class="sxs-lookup"><span data-stu-id="d7a08-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="d7a08-208">如此即會篩選組件，讓您更容易選取所需的參考。</span><span class="sxs-lookup"><span data-stu-id="d7a08-208">This will filter the assemblies and make the desired references easier to select.</span></span>  
  
6.  <span data-ttu-id="d7a08-209">核取方塊旁的**System.Activities**從**搜尋結果**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="d7a08-210">型別**序列化**到**搜尋組件**方塊中，並檢查旁邊的核取方塊**System.Runtime.Serialization**從**搜尋結果**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="d7a08-211">型別**DurableInstancing**到**搜尋組件**方塊中，並檢查旁邊的核取方塊**System.runtime.durableinstancing**和**System.activities.durableinstancing**從**搜尋結果**清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>  
  
9. <span data-ttu-id="d7a08-212">按一下**確定**關閉**參考管理員**並加入參考。</span><span class="sxs-lookup"><span data-stu-id="d7a08-212">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
10. <span data-ttu-id="d7a08-213">以滑鼠右鍵按一下**ApplyDynamicUpdate**方案總管] 中，然後選擇 [**新增**，**類別**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="d7a08-214">型別`DynamicUpdateInfo`到**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>  
  
11. <span data-ttu-id="d7a08-215">將下列兩個成員加入至 `DynamicUpdateInfo` 類別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="d7a08-216">下列範例是已完成的 `DynamicUpdateInfo` 類別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="d7a08-217">此類別包含更新對應的資訊，以及更新工作流程執行個體時所使用的新工作流程識別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>  
  
    ```vb  
    Public Class DynamicUpdateInfo  
        Public updateMap As DynamicUpdateMap  
        Public newIdentity As WorkflowIdentity  
    End Class  
    ```  
  
    ```csharp  
    class DynamicUpdateInfo  
    {  
        public DynamicUpdateMap updateMap;  
        public WorkflowIdentity newIdentity;  
    }  
    ```  
  
12. <span data-ttu-id="d7a08-218">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. <span data-ttu-id="d7a08-219">按兩下**Program.cs** (或**Module1.vb**) 在 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="d7a08-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>  
  
14. <span data-ttu-id="d7a08-220">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowHost  
    Imports System.Data.SqlClient  
    Imports System.Activities.DynamicUpdate  
    Imports System.IO  
    Imports System.Runtime.Serialization  
    Imports System.Activities  
    Imports System.Activities.DurableInstancing  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowHost;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    using System.IO;  
    using System.Runtime.Serialization;  
    using System.Activities.DurableInstancing;  
    ```  
  
15. <span data-ttu-id="d7a08-221">將下列連接字串成員加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d7a08-222">依據您的 SQL Server 版本，連接字串伺服器名稱可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="d7a08-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
16. <span data-ttu-id="d7a08-223">將下列 `GetIDs` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-224">此方法會傳回持續性工作流程執行個體識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="d7a08-224">This method returns a list of persisted workflow instance ids.</span></span>  
  
    ```vb  
    Function GetIds() As IList(Of Guid)  
        Dim Ids As New List(Of Guid)  
        Dim localCmd = _  
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")  
        Using localCon = New SqlConnection(connectionString)  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
                While reader.Read()  
                    'Get the InstanceId of the persisted Workflow  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
  
                    'Add it to the list.  
                    Ids.Add(id)  
                End While  
            End Using  
        End Using  
  
        Return Ids  
    End Function  
    ```  
  
    ```csharp  
    static IList<Guid> GetIds()  
    {  
        List<Guid> Ids = new List<Guid>();  
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");  
        using (SqlConnection localCon = new SqlConnection(connectionString))  
        {  
            SqlCommand cmd = localCon.CreateCommand();  
            cmd.CommandText = localCmd;  
            localCon.Open();  
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
            {  
                while (reader.Read())  
                {  
                    // Get the InstanceId of the persisted Workflow  
                    Guid id = Guid.Parse(reader[0].ToString());  
  
                    // Add it to the list.  
                    Ids.Add(id);  
                }  
            }  
        }  
  
        return Ids;  
    }  
    ```  
  
17. <span data-ttu-id="d7a08-225">將下列 `LoadMap` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-226">此方法會建立字典，此字典會將 `v1` 工作流程識別對應至更新對應，以及用來更新對應持續性工作流程執行個體的新工作流程識別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>  
  
    ```vb  
    Function LoadMap(mapName As String) As DynamicUpdateMap  
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)  
  
        Dim map As DynamicUpdateMap  
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)  
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
            Dim updateMap = serializer.ReadObject(fs)  
            If updateMap Is Nothing Then  
                Throw New ApplicationException("DynamicUpdateMap is null.")  
            End If  
  
            map = updateMap  
        End Using  
  
        Return map  
    End Function  
    ```  
  
    ```csharp  
    static DynamicUpdateMap LoadMap(string mapName)  
    {  
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);  
  
        DynamicUpdateMap map;  
        using (FileStream fs = File.Open(path, FileMode.Open))  
        {  
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
            object updateMap = serializer.ReadObject(fs);  
            if (updateMap == null)  
            {  
                throw new ApplicationException("DynamicUpdateMap is null.");  
            }  
  
            map = updateMap as DynamicUpdateMap;  
        }  
  
        return map;  
    }  
    ```  
  
18. <span data-ttu-id="d7a08-227">將下列 `LoadMaps` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="d7a08-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="d7a08-228">此方法會載入三個更新對應，並建立將 `v1` 工作流程識別對應至更新對應的字典。</span><span class="sxs-lookup"><span data-stu-id="d7a08-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>  
  
    ```vb  
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)  
        'There are 3 update maps to describe the changes to update v1 workflows,  
        'one for reach of the 3 workflow types in the tutorial.  
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()  
  
        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")  
        Dim sequentialInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = sequentialMap,  
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)  
  
        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")  
        Dim stateInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = stateMap,  
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)  
  
        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")  
        Dim flowchartInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = flowchartMap,  
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)  
  
        Return maps  
    End Function  
    ```  
  
    ```csharp  
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()  
    {  
        // There are 3 update maps to describe the changes to update v1 workflows,  
        // one for reach of the 3 workflow types in the tutorial.  
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =  
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();  
  
        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");  
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo  
        {  
            updateMap = sequentialMap,  
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);  
  
        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");  
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo  
        {  
            updateMap = stateMap,  
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);  
  
        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");  
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo  
        {  
            updateMap = flowchartMap,  
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);  
  
        return maps;              
    }  
    ```  
  
19. <span data-ttu-id="d7a08-229">將下列程式碼加入至 `Main`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-229">Add the following code to `Main`.</span></span> <span data-ttu-id="d7a08-230">此程式碼會逐一查看持續性工作流程執行個體，並檢查每個 `WorkflowIdentity`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="d7a08-231">如果 `WorkflowIdentity` 對應至 `v1` 工作流程執行個體，就會以更新的工作流程定義和更新的工作流程識別來設定 `WorkflowApplication`。</span><span class="sxs-lookup"><span data-stu-id="d7a08-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="d7a08-232">接下來會以執行個體和更新對應來呼叫 `WorkflowApplication.Load`，以套用動態更新對應。</span><span class="sxs-lookup"><span data-stu-id="d7a08-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="d7a08-233">一旦套用更新後，會藉由呼叫 `Unload` 來持續更新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d7a08-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>  
  
    ```vb  
    Dim store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()  
  
    For Each id As Guid In GetIds()  
        'Get a proxy to the instance.   
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)  
  
        'Only update v1 workflows.  
        If Not instance.DefinitionIdentity Is Nothing AndAlso _  
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then  
  
            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)  
  
            'Associate the persisted WorkflowApplicationInstance with  
            'a WorkflowApplication that is configured with the updated  
            'definition and updated WorkflowIdentity.  
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)  
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)  
  
            'Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap)  
  
            'Persist the updated instance.  
            wfApp.Unload()  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity)  
        Else  
            'Not updating this instance, so unload it.  
            instance.Abandon()  
        End If  
    Next  
    ```  
  
    ```csharp  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();  
  
    foreach (Guid id in GetIds())  
    {  
        // Get a proxy to the instance.   
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(id, store);  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);  
  
        // Only update v1 workflows.  
        if (instance.DefinitionIdentity != null &&  
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))  
        {  
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];  
  
            // Associate the persisted WorkflowApplicationInstance with  
            // a WorkflowApplication that is configured with the updated  
            // definition and updated WorkflowIdentity.  
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);  
            WorkflowApplication wfApp =  
                new WorkflowApplication(wf, info.newIdentity);  
  
            // Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap);  
  
            // Persist the updated instance.  
            wfApp.Unload();  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity);  
        }  
        else  
        {  
            // Not updating this instance, so unload it.  
            instance.Abandon();  
        }  
    }  
    ```  
  
20. <span data-ttu-id="d7a08-234">以滑鼠右鍵按一下**ApplyDynamicUpdate**中**方案總管 中**選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
21. <span data-ttu-id="d7a08-235">按下 CTRL + SHIFT + B 建置方案，然後按下 CTRL + F5 執行 `ApplyDynamicUpdate` 應用程式，並更新持續性工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="d7a08-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="d7a08-236">您應該會看到類似下方的輸出。</span><span class="sxs-lookup"><span data-stu-id="d7a08-236">You should see output similar to the following.</span></span> <span data-ttu-id="d7a08-237">1.0.0.0 版工作流程會更新為 1.5.0.0 版，但不會更新 2.0.0.0 版工作流程。</span><span class="sxs-lookup"><span data-stu-id="d7a08-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>  
  
 <span data-ttu-id="d7a08-238">**檢查： StateMachineNumberGuessWorkflow;版本 = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="d7a08-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>  
<span data-ttu-id="d7a08-239">**已更新為： StateMachineNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-240">**檢查： StateMachineNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-241">**已更新為： StateMachineNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-242">**檢查： FlowchartNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-243">**已更新為： FlowchartNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-244">**檢查： FlowchartNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-245">**已更新為： FlowchartNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-246">**檢查： SequentialNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-247">**已更新為： SequentialNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-248">**檢查： SequentialNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-249">**已更新為： SequentialNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-250">**檢查： SequentialNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-251">**已更新為： SequentialNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-252">**檢查： StateMachineNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-253">**已更新為： StateMachineNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-254">**檢查： FlowchartNumberGuessWorkflow;版本 = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="d7a08-255">**已更新為： FlowchartNumberGuessWorkflow;版本 = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="d7a08-256">**檢查： StateMachineNumberGuessWorkflow;版本 = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="d7a08-257">**檢查： StateMachineNumberGuessWorkflow;版本 = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="d7a08-258">**檢查： FlowchartNumberGuessWorkflow;版本 = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="d7a08-259">**檢查： FlowchartNumberGuessWorkflow;版本 = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="d7a08-260">**檢查： SequentialNumberGuessWorkflow;版本 = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="d7a08-261">**檢查： SequentialNumberGuessWorkflow;版本 = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="d7a08-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="d7a08-262">**請按任意鍵繼續...**</span><span class="sxs-lookup"><span data-stu-id="d7a08-262">**Press any key to continue . . .**</span></span>  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="d7a08-263">若要更新的工作流程執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d7a08-263">To run the application with the updated workflows</span></span>  
  
1.  <span data-ttu-id="d7a08-264">以滑鼠右鍵按一下**NumberGuessWorkflowHost**中**方案總管 中**選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="d7a08-265">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-265">Press CTRL+F5 to run the application.</span></span>  
  
3.  <span data-ttu-id="d7a08-266">按一下**新遊戲**啟動新的工作流程，並記下版本以下資訊指出工作流程狀態視窗是`v2`工作流程。</span><span class="sxs-lookup"><span data-stu-id="d7a08-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>  
  
4.  <span data-ttu-id="d7a08-267">選取其中一個`v1`工作流程的開頭啟動[How to： 主機的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)主題。</span><span class="sxs-lookup"><span data-stu-id="d7a08-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="d7a08-268">請注意在狀態視窗下的版本資訊，表示工作流程是版本**1.5.0.0**工作流程。</span><span class="sxs-lookup"><span data-stu-id="d7a08-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="d7a08-269">請注意，除太大或太小之外，沒有任何資訊指示先前的猜測。</span><span class="sxs-lookup"><span data-stu-id="d7a08-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>  
  
 <span data-ttu-id="d7a08-270">**請輸入介於 1 到 10 之間的數字**</span><span class="sxs-lookup"><span data-stu-id="d7a08-270">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="d7a08-271">**您猜得就太低。**</span><span class="sxs-lookup"><span data-stu-id="d7a08-271">**Your guess is too low.**</span></span>  
  
5.  <span data-ttu-id="d7a08-272">記下 `InstanceId`，然後輸入猜測值，直到工作流程完成。</span><span class="sxs-lookup"><span data-stu-id="d7a08-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="d7a08-273">狀態視窗會顯示猜測內容的相關資訊，因為動態更新已更新 `WriteLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="d7a08-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>  
  
 <span data-ttu-id="d7a08-274">**請輸入介於 1 到 10 之間的數字**</span><span class="sxs-lookup"><span data-stu-id="d7a08-274">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="d7a08-275">**您猜得就太低。** </span><span class="sxs-lookup"><span data-stu-id="d7a08-275">**Your guess is too low.** </span></span>  
<span data-ttu-id="d7a08-276">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="d7a08-276">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="d7a08-277">**5 就太低。** </span><span class="sxs-lookup"><span data-stu-id="d7a08-277">**5 is too low.** </span></span>  
<span data-ttu-id="d7a08-278">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="d7a08-278">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="d7a08-279">**7 太高。** </span><span class="sxs-lookup"><span data-stu-id="d7a08-279">**7 is too high.** </span></span>  
<span data-ttu-id="d7a08-280">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="d7a08-280">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="d7a08-281">**恭喜，您了 4 猜到數字。**</span><span class="sxs-lookup"><span data-stu-id="d7a08-281">**Congratulations, you guessed the number in 4 turns.**</span></span>  
  
6.  <span data-ttu-id="d7a08-282">開啟 Windows 檔案總管並瀏覽至**NumberGuessWorkflowHost\bin\debug**資料夾 (或**bin\release**取決於您的專案設定)，然後開啟使用 [記事本]，對應的追蹤檔案若要完成的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d7a08-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="d7a08-283">如果您未進行記下`InstanceId`您可以使用來識別正確的追蹤檔案**修改日期**Windows 檔案總管 中的資訊。</span><span class="sxs-lookup"><span data-stu-id="d7a08-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="d7a08-284">追蹤資訊的最後一行包含新加入之 `WriteLine` 活動的輸出。</span><span class="sxs-lookup"><span data-stu-id="d7a08-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>  
  
 <span data-ttu-id="d7a08-285">**請輸入介於 1 到 10 之間的數字**</span><span class="sxs-lookup"><span data-stu-id="d7a08-285">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="d7a08-286">**您猜得就太低。** </span><span class="sxs-lookup"><span data-stu-id="d7a08-286">**Your guess is too low.** </span></span>  
<span data-ttu-id="d7a08-287">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="d7a08-287">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="d7a08-288">**5 就太低。** </span><span class="sxs-lookup"><span data-stu-id="d7a08-288">**5 is too low.** </span></span>  
<span data-ttu-id="d7a08-289">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="d7a08-289">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="d7a08-290">**7 太高。** </span><span class="sxs-lookup"><span data-stu-id="d7a08-290">**7 is too high.** </span></span>  
<span data-ttu-id="d7a08-291">**請輸入介於 1 到 10 之間的數字** </span><span class="sxs-lookup"><span data-stu-id="d7a08-291">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="d7a08-292">**6 是正確的。您猜到它了 4。**</span><span class="sxs-lookup"><span data-stu-id="d7a08-292">**6 is correct. You guessed it in 4 turns.**</span></span>  
  
###  <a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="d7a08-293">若要啟用 啟動工作流程的舊版本</span><span class="sxs-lookup"><span data-stu-id="d7a08-293">To enable starting previous versions of the workflows</span></span>  
 <span data-ttu-id="d7a08-294">如果您執行完工作流程來進行更新，可以修改 `NumberGuessWorkflowHost` 應用程式，使其能啟動工作流程的舊版本。</span><span class="sxs-lookup"><span data-stu-id="d7a08-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>  
  
1.  <span data-ttu-id="d7a08-295">按兩下**WorkflowHostForm**中**方案總管 中**，然後選取**WorkflowType**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="d7a08-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>  
  
2.  <span data-ttu-id="d7a08-296">在**屬性**視窗中，選取**項目**屬性，然後按一下省略符號按鈕，以編輯**項目**集合。</span><span class="sxs-lookup"><span data-stu-id="d7a08-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>  
  
3.  <span data-ttu-id="d7a08-297">將下列三個項目加入至集合。</span><span class="sxs-lookup"><span data-stu-id="d7a08-297">Add the following three items to the collection.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     <span data-ttu-id="d7a08-298">完成的 `Items` 集合中會有六個項目。</span><span class="sxs-lookup"><span data-stu-id="d7a08-298">The completed `Items` collection will have six items.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  <span data-ttu-id="d7a08-299">按兩下**WorkflowHostForm**中**方案總管 中**，然後選取**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="d7a08-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="d7a08-300">將三個新案例加入`switch`(或`Select Case`) 中的陳述式`NewGame_Click`處理常式對應中的新項目**WorkflowType**下拉式方塊，以比對的工作流程識別。</span><span class="sxs-lookup"><span data-stu-id="d7a08-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>  
  
    ```vb  
    Case "SequentialNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
    Case "StateMachineNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
    Case "FlowchartNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    ```  
  
    ```csharp  
    case "SequentialNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
        break;  
  
    case "StateMachineNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
        break;  
  
    case "FlowchartNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
        break;  
    ```  
  
     <span data-ttu-id="d7a08-301">下列範例包含完整的 `switch` (或 `Select Case`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>  
  
    ```vb  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
  
        Case "SequentialNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
        Case "StateMachineNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
        Case "FlowchartNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    End Select  
    ```  
  
    ```csharp  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
  
        case "SequentialNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
            break;  
  
        case "StateMachineNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
            break;  
  
        case "FlowchartNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
            break;  
    };  
    ```  
  
6.  <span data-ttu-id="d7a08-302">按 CTRL+F5 建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="d7a08-303">您現在可以啟動工作流程的 `v1` 版本以及目前版本。</span><span class="sxs-lookup"><span data-stu-id="d7a08-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="d7a08-304">若要動態更新這些新執行個體，執行**ApplyDynamicUpdate**應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7a08-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
