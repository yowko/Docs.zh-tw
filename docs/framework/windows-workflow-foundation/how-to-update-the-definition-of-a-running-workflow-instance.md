---
title: 作法：更新執行中工作流程執行個體的定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: b94c7564b1ce87695f82f28eb6daf7686203b41f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190425"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="95966-102">作法：更新執行中工作流程執行個體的定義</span><span class="sxs-lookup"><span data-stu-id="95966-102">How to: Update the Definition of a Running Workflow Instance</span></span>

<span data-ttu-id="95966-103">動態更新提供的機制可讓工作流程應用程式開發人員更新持續性工作流程執行個體的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="95966-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="95966-104">必要的變更可以是實作錯誤修復、新要求，或是適應突如其來的變化。</span><span class="sxs-lookup"><span data-stu-id="95966-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="95966-105">本教學課程中的這個步驟將示範如何使用動態更新來修改 `v1` 數位猜測工作流程的持續性實例，以符合 [如何：並行裝載多個工作流程版本](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)的新功能。</span><span class="sxs-lookup"><span data-stu-id="95966-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="95966-106">本主題內容</span><span class="sxs-lookup"><span data-stu-id="95966-106">In this topic</span></span>

- [<span data-ttu-id="95966-107">建立 CreateUpdateMaps 專案</span><span class="sxs-lookup"><span data-stu-id="95966-107">To create the CreateUpdateMaps project</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [<span data-ttu-id="95966-108">更新 StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="95966-108">To update StateMachineNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [<span data-ttu-id="95966-109">更新 FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="95966-109">To update FlowchartNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [<span data-ttu-id="95966-110">更新 SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="95966-110">To update SequentialNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [<span data-ttu-id="95966-111">建置及執行 CreateUpdateMaps 應用程式</span><span class="sxs-lookup"><span data-stu-id="95966-111">To build and run the CreateUpdateMaps application</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [<span data-ttu-id="95966-112">建置更新的工作流程組件</span><span class="sxs-lookup"><span data-stu-id="95966-112">To build the updated workflow assembly</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [<span data-ttu-id="95966-113">以新版本更新 WorkflowVersionMap</span><span class="sxs-lookup"><span data-stu-id="95966-113">To update WorkflowVersionMap with the new versions</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="95966-114">套用動態更新</span><span class="sxs-lookup"><span data-stu-id="95966-114">To apply the dynamic updates</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [<span data-ttu-id="95966-115">以更新的工作流程執行應用程式</span><span class="sxs-lookup"><span data-stu-id="95966-115">To run the application with the updated workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [<span data-ttu-id="95966-116">使其能夠啟動工作流程的舊版本</span><span class="sxs-lookup"><span data-stu-id="95966-116">To enable starting previous versions of the workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> <span data-ttu-id="95966-117">若要建立 CreateUpdateMaps 專案</span><span class="sxs-lookup"><span data-stu-id="95966-117">To create the CreateUpdateMaps project</span></span>

1. <span data-ttu-id="95966-118">以滑鼠右鍵按一下 **方案總管** 中的 **WF45GettingStartedTutorial** ，然後選擇 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-118">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="95966-119">在 [ **已安裝** ] 節點中，選取 [ **Visual c #**]、[ **windows** (或 **Visual Basic**]、[ **windows**) 。</span><span class="sxs-lookup"><span data-stu-id="95966-119">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="95966-120">視 Visual Studio 中設為主要語言的程式設計語言而定，[Visual C#] 或 [Visual Basic] 節點可能位於 [已安裝] 節點中的 [其他語言] 下。</span><span class="sxs-lookup"><span data-stu-id="95966-120">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="95966-121">確定已在 .NET Framework 版本下拉清單中選取了 **.NET Framework 4.5**。</span><span class="sxs-lookup"><span data-stu-id="95966-121">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="95966-122">從 **Windows** 清單中選取 [**主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="95966-122">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="95966-123">在 [**名稱**] 方塊中輸入 **CreateUpdateMaps** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="95966-123">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="95966-124">以滑鼠右鍵按一下 **方案總管** 中的 [ **CreateUpdateMaps** ]，然後選擇 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="95966-124">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="95966-125">從 [**加入參考**] 清單中的 [**元件**] 節點選取 [**架構**]。</span><span class="sxs-lookup"><span data-stu-id="95966-125">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="95966-126">在 [**搜尋元件**] 方塊中輸入 [**系統**]，以篩選元件，並讓所需的參考更容易選取。</span><span class="sxs-lookup"><span data-stu-id="95966-126">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>

5. <span data-ttu-id="95966-127">核取 [**搜尋結果**] 清單中 [**系統**] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="95966-127">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

6. <span data-ttu-id="95966-128">在 [**搜尋元件**] 方塊中輸入 **序列化**，然後從 **搜尋結果** 清單中選取 [system.string **] 旁的核取方塊。**</span><span class="sxs-lookup"><span data-stu-id="95966-128">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

7. <span data-ttu-id="95966-129">在 [**搜尋元件**] 方塊 **中輸入 system.string** ，然後從 **搜尋結果** 清單中選取 [system.string] 旁的複選 **框。**</span><span class="sxs-lookup"><span data-stu-id="95966-129">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>

8. <span data-ttu-id="95966-130">按一下 **[確定] 關閉 [** **參考管理員** ] 並加入參考。</span><span class="sxs-lookup"><span data-stu-id="95966-130">Click **OK** to close **Reference Manager** and add the references.</span></span>

9. <span data-ttu-id="95966-131">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="95966-131">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

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

10. <span data-ttu-id="95966-132">將下列兩個字串成員加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-132">Add the following two string members to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. <span data-ttu-id="95966-133">將下列 `StartUpdate` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-133">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-134">此方法會將指定的 xaml 工作流程定義載入到 `ActivityBuilder`，然後呼叫 `DynamicUpdate.PrepareForUpdate`。</span><span class="sxs-lookup"><span data-stu-id="95966-134">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="95966-135">`PrepareForUpdate` 會在 `ActivityBuilder` 中建立工作流程定義的複本。</span><span class="sxs-lookup"><span data-stu-id="95966-135">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="95966-136">修改工作流程定義後，會使用此複本和修改過的工作流程定義建立更新對應。</span><span class="sxs-lookup"><span data-stu-id="95966-136">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
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
            // In the XAML the "local" namespace refers to artifacts that come from
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

12. <span data-ttu-id="95966-137">接下來，將下列 `CreateUpdateMethod` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-137">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-138">這樣會呼叫 DynamicUpdateServices.CreateUpdateMap 來建立動態更新對應，然後使用指定名稱儲存更新對應。</span><span class="sxs-lookup"><span data-stu-id="95966-138">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="95966-139">此更新對應包含工作流程執行階段更新持續工作流程執行個體所需的資訊，該執行個體是使用包含在 `ActivityBuilder` 中的原始工作流程定義啟動的，這樣它才會使用更新的工作流程定義完成。</span><span class="sxs-lookup"><span data-stu-id="95966-139">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>

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

13. <span data-ttu-id="95966-140">將下列 `SaveUpdatedDefinition` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-140">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-141">這種方法會在建立更新對應之後，儲存更新的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="95966-141">This method saves the updated workflow definition once the update map is created.</span></span>

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

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> <span data-ttu-id="95966-142">更新 StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="95966-142">To update StateMachineNumberGuessWorkflow</span></span>

1. <span data-ttu-id="95966-143">將 `CreateStateMachineUpdateMap` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-143">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. <span data-ttu-id="95966-144">呼叫 `StartUpdate`，然後取得工作流程的根 `StateMachine` 活動參考。</span><span class="sxs-lookup"><span data-stu-id="95966-144">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>

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

3. <span data-ttu-id="95966-145">接下來，更新兩個活動的運算式 `WriteLine` ，以顯示使用者的猜測是否太高或太低，使其符合 [如何：並行裝載多個工作流程版本](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)的更新。</span><span class="sxs-lookup"><span data-stu-id="95966-145">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

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

4. <span data-ttu-id="95966-146">接下來，加入顯示結束訊息的新 `WriteLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="95966-146">Next, add the new `WriteLine` activity that displays the closing message.</span></span>

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

5. <span data-ttu-id="95966-147">更新工作流程後，呼叫 `CreateUpdateMaps` 和 `SaveUpdatedDefinition`。</span><span class="sxs-lookup"><span data-stu-id="95966-147">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="95966-148">`CreateUpdateMaps` 會建立和儲存 `DynamicUpdateMap`，而 `SaveUpdatedDefinition` 會儲存更新過的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="95966-148">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>

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

    <span data-ttu-id="95966-149">下列範例是完成的 `CreateStateMachineUpdateMap` 方法。</span><span class="sxs-lookup"><span data-stu-id="95966-149">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>

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

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> <span data-ttu-id="95966-150">更新 FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="95966-150">To update FlowchartNumberGuessWorkflow</span></span>

1. <span data-ttu-id="95966-151">將下列 `CreateFlowchartUpdateMethod` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-151">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-152">此方法類似 `CreateStateMachineUpdateMap`。</span><span class="sxs-lookup"><span data-stu-id="95966-152">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="95966-153">它會從呼叫 `StartUpdate` 開始、更新流程圖工作流程定義，接著在儲存更新對應和更新的工作流程定後結束。</span><span class="sxs-lookup"><span data-stu-id="95966-153">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

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

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> <span data-ttu-id="95966-154">更新 SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="95966-154">To update SequentialNumberGuessWorkflow</span></span>

1. <span data-ttu-id="95966-155">將下列 `CreateSequentialUpdateMethod` 加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-155">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-156">這個方法類似另外兩個方法。</span><span class="sxs-lookup"><span data-stu-id="95966-156">This method is similar to the other two methods.</span></span> <span data-ttu-id="95966-157">它會從呼叫 `StartUpdate` 開始、更新循序工作流程定義，接著在儲存更新對應和更新的工作流程定後結束。</span><span class="sxs-lookup"><span data-stu-id="95966-157">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

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

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="95966-158">若要建立並執行 CreateUpdateMaps 應用程式</span><span class="sxs-lookup"><span data-stu-id="95966-158">To build and run the CreateUpdateMaps application</span></span>

1. <span data-ttu-id="95966-159">更新 `Main` 方法，並加入下列三種方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="95966-159">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="95966-160">這些方法會加入至下列區段。</span><span class="sxs-lookup"><span data-stu-id="95966-160">These methods are added in the following sections.</span></span> <span data-ttu-id="95966-161">每個方法會更新對應的數字猜測工作流程，並建立描述更新的 `DynamicUpdateMap`。</span><span class="sxs-lookup"><span data-stu-id="95966-161">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>

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

2. <span data-ttu-id="95966-162">以滑鼠右鍵按一下 **方案總管** 中的 [ **CreateUpdateMaps** ]，然後選擇 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-162">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

3. <span data-ttu-id="95966-163">按 CTRL + SHIFT + B 建置方案，然後按 CTRL + F5 執行 `CreateUpdateMaps` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95966-163">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="95966-164">`CreateUpdateMaps`執行時，應用程式不會顯示任何狀態資訊，但如果您查看 **NumberGuessWorkflowActivities_du** 資料夾和 **previousversions]** 資料夾，您會看到更新的工作流程定義檔案和更新對應。</span><span class="sxs-lookup"><span data-stu-id="95966-164">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>

    <span data-ttu-id="95966-165">建立更新對應並更新工作流程定義後，下一步就是建置包含更新定義的更新工作流程組件。</span><span class="sxs-lookup"><span data-stu-id="95966-165">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> <span data-ttu-id="95966-166">若要建立更新的工作流程元件</span><span class="sxs-lookup"><span data-stu-id="95966-166">To build the updated workflow assembly</span></span>

1. <span data-ttu-id="95966-167">開啟 Visual Studio 2012 的第二個實例。</span><span class="sxs-lookup"><span data-stu-id="95966-167">Open a second instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="95966-168">從 [檔案 **] 功能表中選擇 [** **開啟**]、[**專案/方案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-168">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>

3. <span data-ttu-id="95966-169">流覽至您在 [如何：並行裝載多個版本的工作流程](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)中建立的 **NumberGuessWorkflowActivities_du** 資料夾，選取 [ **[numberguessworkflowactivities]** ] (或 [ **Vbproj** ]) ，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="95966-169">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>

4. <span data-ttu-id="95966-170">在 **方案總管** 中，以滑鼠右鍵按一下 **SequentialNumberGuessWorkflow** ，然後選擇 [ **從專案排除**]。</span><span class="sxs-lookup"><span data-stu-id="95966-170">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="95966-171">針對 **FlowchartNumberGuessWorkflow** 和 **StateMachineNumberGuessWorkflow** 進行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="95966-171">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="95966-172">此步驟會從專案中移除舊版的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="95966-172">This step removes the previous versions of the workflow definitions from the project.</span></span>

5. <span data-ttu-id="95966-173">選擇 [**專案**] 功能表中的 [**加入現有專案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-173">Choose **Add Existing Item** from the **Project** menu.</span></span>

6. <span data-ttu-id="95966-174">流覽至您在 how [to：並存裝載工作流程的多個版本](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)中所建立的 **NumberGuessWorkflowActivities_du** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="95966-174">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

7. <span data-ttu-id="95966-175">選擇 **xaml 檔案 (\* .xaml; \* 。** 從 [ **檔案類型** ] 下拉式清單中 xoml) 。</span><span class="sxs-lookup"><span data-stu-id="95966-175">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>

8. <span data-ttu-id="95966-176">選取 **SequentialNumberGuessWorkflow_du .xaml**、 **FlowchartNumberGuessWorkflow_du .xaml** 和 **StateMachineNumberGuessWorkflow_du .Xaml** ，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="95966-176">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="95966-177">按住 CTRL + 按一下以同時選取多個項目。</span><span class="sxs-lookup"><span data-stu-id="95966-177">CTRL+Click to select multiple items at a time.</span></span>

    <span data-ttu-id="95966-178">此步驟會將更新過的工作流程定義版本加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="95966-178">This step adds the updated versions of the workflow definitions to the project.</span></span>

9. <span data-ttu-id="95966-179">按 CTRL+SHIFT+B 以建置專案。</span><span class="sxs-lookup"><span data-stu-id="95966-179">Press CTRL+SHIFT+B to build the project.</span></span>

10. <span data-ttu-id="95966-180">選擇 [檔案 **] 功能表中的 [** **關閉方案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-180">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="95966-181">不需要專案的方案檔，因此按一下 [ **否** ] 關閉 Visual Studio 而不儲存方案檔。</span><span class="sxs-lookup"><span data-stu-id="95966-181">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="95966-182">選擇 [檔案] 功能表 **上的 [** 結束 **]，關閉** Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="95966-182">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>

11. <span data-ttu-id="95966-183">開啟 Windows 檔案總管，然後根據您的專案設定) ，流覽至 **NumberGuessWorkflowActivities_du \bin\debug** 資料夾 (或 **bin\Release** 。</span><span class="sxs-lookup"><span data-stu-id="95966-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>

12. <span data-ttu-id="95966-184">將 **NumberGuessWorkflowActivities.dll** 重新命名為 **NumberGuessWorkflowActivities_v15.dll**，並將它複製到您在 How [To：並存裝載多個版本的工作流程](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)中建立的 **previousversions]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="95966-184">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="95966-185">使用新版本更新 WorkflowVersionMap</span><span class="sxs-lookup"><span data-stu-id="95966-185">To update WorkflowVersionMap with the new versions</span></span>

1. <span data-ttu-id="95966-186">切換回 Visual Studio 2012 的初始實例。</span><span class="sxs-lookup"><span data-stu-id="95966-186">Switch back to the initial instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="95966-187">按兩下 [ **[numberguessworkflowhost]** ] 專案底下的 [ **WorkflowVersionMap.cs** (或) **WorkflowVersionMap** ]，將它開啟。</span><span class="sxs-lookup"><span data-stu-id="95966-187">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

3. <span data-ttu-id="95966-188">將三個新的工作流程識別加入到六個現有工作流程識別宣告的正下方。</span><span class="sxs-lookup"><span data-stu-id="95966-188">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="95966-189">在本教學課程中，會使用 `1.5.0.0` 做為動態更新識別的 `WorkflowIdentity.Version`。</span><span class="sxs-lookup"><span data-stu-id="95966-189">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="95966-190">這些新的 `v15` 工作流程識別，會為動態更新的持續性工作流程執行個體提供正確的工作流程定義。</span><span class="sxs-lookup"><span data-stu-id="95966-190">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
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

4. <span data-ttu-id="95966-191">在建構函式結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="95966-191">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="95966-192">此程式碼會初始化動態更新工作流程識別、載入對應的工作流程定義，然後將定義加入至工作流程版本字典。</span><span class="sxs-lookup"><span data-stu-id="95966-192">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>

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

     <span data-ttu-id="95966-193">下列範例是已完成的 `WorkflowVersionMap` 類別。</span><span class="sxs-lookup"><span data-stu-id="95966-193">The following example is the completed `WorkflowVersionMap` class.</span></span>

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

        'v1.5 (Dynamic Update) identities.
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

5. <span data-ttu-id="95966-194">按 CTRL+SHIFT+B 以建置專案。</span><span class="sxs-lookup"><span data-stu-id="95966-194">Press CTRL+SHIFT+B to build the project.</span></span>

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="95966-195">套用動態更新</span><span class="sxs-lookup"><span data-stu-id="95966-195">To apply the dynamic updates</span></span>

1. <span data-ttu-id="95966-196">以滑鼠右鍵按一下 **方案總管** 中的 **WF45GettingStartedTutorial** ，然後選擇 [**加入**]、[**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-196">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="95966-197">在 [ **已安裝** ] 節點中，選取 [ **Visual c #**]、[ **windows** (或 **Visual Basic**]、[ **windows**) 。</span><span class="sxs-lookup"><span data-stu-id="95966-197">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="95966-198">視 Visual Studio 中設為主要語言的程式設計語言而定，[Visual C#] 或 [Visual Basic] 節點可能位於 [已安裝] 節點中的 [其他語言] 下。</span><span class="sxs-lookup"><span data-stu-id="95966-198">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

    <span data-ttu-id="95966-199">確定已在 .NET Framework 版本下拉清單中選取了 **.NET Framework 4.5**。</span><span class="sxs-lookup"><span data-stu-id="95966-199">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="95966-200">從 **Windows** 清單中選取 [**主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="95966-200">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="95966-201">在 [**名稱**] 方塊中輸入 **] applydynamicupdate]** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="95966-201">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="95966-202">以滑鼠右鍵按一下 **方案總管** 中的 [ **] applydynamicupdate]** ]，然後選擇 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="95966-202">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="95966-203">按一下 [ **方案** ]，然後核取 [ **[numberguessworkflowhost]**] 旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="95966-203">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="95966-204">`ApplyDynamicUpdate` 需要此參考才能使用 `NumberGuessWorkflowHost.WorkflowVersionMap` 類別。</span><span class="sxs-lookup"><span data-stu-id="95966-204">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>

5. <span data-ttu-id="95966-205">從 [**加入參考**] 清單中的 [**元件**] 節點選取 [**架構**]。</span><span class="sxs-lookup"><span data-stu-id="95966-205">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="95966-206">在 [**搜尋元件**] 方塊中輸入 [**系統**]。</span><span class="sxs-lookup"><span data-stu-id="95966-206">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="95966-207">如此即會篩選組件，讓您更容易選取所需的參考。</span><span class="sxs-lookup"><span data-stu-id="95966-207">This will filter the assemblies and make the desired references easier to select.</span></span>

6. <span data-ttu-id="95966-208">核取 [**搜尋結果**] 清單中 [**系統**] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="95966-208">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

7. <span data-ttu-id="95966-209">在 [**搜尋元件**] 方塊中輸入 **序列化**，然後從 **搜尋結果** 清單中選取 [system.string **] 旁的核取方塊。**</span><span class="sxs-lookup"><span data-stu-id="95966-209">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

8. <span data-ttu-id="95966-210">在 [**搜尋元件**] 方塊中輸入 **DurableInstancing** ，然後從 **搜尋結果** 清單中選取 [ **DurableInstancing** ] 和 [ **DurableInstancing** ] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="95966-210">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>

9. <span data-ttu-id="95966-211">按一下 **[確定] 關閉 [** **參考管理員** ] 並加入參考。</span><span class="sxs-lookup"><span data-stu-id="95966-211">Click **OK** to close **Reference Manager** and add the references.</span></span>

10. <span data-ttu-id="95966-212">以滑鼠右鍵按一下方案總管中的 **] applydynamicupdate]** ，然後選擇 [ **新增**]、[ **類別**]。</span><span class="sxs-lookup"><span data-stu-id="95966-212">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="95966-213">`DynamicUpdateInfo`在 [**名稱**] 方塊中輸入，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="95966-213">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>

11. <span data-ttu-id="95966-214">將下列兩個成員加入至 `DynamicUpdateInfo` 類別。</span><span class="sxs-lookup"><span data-stu-id="95966-214">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="95966-215">下列範例是已完成的 `DynamicUpdateInfo` 類別。</span><span class="sxs-lookup"><span data-stu-id="95966-215">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="95966-216">此類別包含更新對應的資訊，以及更新工作流程執行個體時所使用的新工作流程識別。</span><span class="sxs-lookup"><span data-stu-id="95966-216">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>

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

12. <span data-ttu-id="95966-217">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="95966-217">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. <span data-ttu-id="95966-218">按兩下方案總管中的 [ **Program.cs** (] 或 [) ] **。**</span><span class="sxs-lookup"><span data-stu-id="95966-218">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>

14. <span data-ttu-id="95966-219">將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="95966-219">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

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

15. <span data-ttu-id="95966-220">將下列連接字串成員加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-220">Add the following connection string member to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > <span data-ttu-id="95966-221">依據您的 SQL Server 版本，連接字串伺服器名稱可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="95966-221">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

16. <span data-ttu-id="95966-222">將下列 `GetIDs` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-222">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-223">此方法會傳回持續性工作流程執行個體識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="95966-223">This method returns a list of persisted workflow instance ids.</span></span>

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

17. <span data-ttu-id="95966-224">將下列 `LoadMap` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-224">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-225">此方法會建立字典，此字典會將 `v1` 工作流程識別對應至更新對應，以及用來更新對應持續性工作流程執行個體的新工作流程識別。</span><span class="sxs-lookup"><span data-stu-id="95966-225">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>

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

18. <span data-ttu-id="95966-226">將下列 `LoadMaps` 方法加入至 `Program` 類別 (或 `Module1`)。</span><span class="sxs-lookup"><span data-stu-id="95966-226">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="95966-227">此方法會載入三個更新對應，並建立將 `v1` 工作流程識別對應至更新對應的字典。</span><span class="sxs-lookup"><span data-stu-id="95966-227">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>

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

19. <span data-ttu-id="95966-228">將下列程式碼新增至 `Main`。</span><span class="sxs-lookup"><span data-stu-id="95966-228">Add the following code to `Main`.</span></span> <span data-ttu-id="95966-229">此程式碼會逐一查看持續性工作流程執行個體，並檢查每個 `WorkflowIdentity`。</span><span class="sxs-lookup"><span data-stu-id="95966-229">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="95966-230">如果 `WorkflowIdentity` 對應至 `v1` 工作流程執行個體，就會以更新的工作流程定義和更新的工作流程識別來設定 `WorkflowApplication`。</span><span class="sxs-lookup"><span data-stu-id="95966-230">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="95966-231">接下來會以執行個體和更新對應來呼叫 `WorkflowApplication.Load`，以套用動態更新對應。</span><span class="sxs-lookup"><span data-stu-id="95966-231">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="95966-232">一旦套用更新後，會藉由呼叫 `Unload` 來持續更新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="95966-232">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>

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

20. <span data-ttu-id="95966-233">以滑鼠右鍵按一下 **方案總管** 中的 [ **] applydynamicupdate]** ]，然後選擇 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-233">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

21. <span data-ttu-id="95966-234">按下 CTRL + SHIFT + B 建置方案，然後按下 CTRL + F5 執行 `ApplyDynamicUpdate` 應用程式，並更新持續性工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="95966-234">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="95966-235">您應該會看到如下輸出。</span><span class="sxs-lookup"><span data-stu-id="95966-235">You should see output similar to the following.</span></span> <span data-ttu-id="95966-236">1.0.0.0 版工作流程會更新為 1.5.0.0 版，但不會更新 2.0.0.0 版工作流程。</span><span class="sxs-lookup"><span data-stu-id="95966-236">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>

    <span data-ttu-id="95966-237">**檢查： StateMachineNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-237">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-238">**更新為： StateMachineNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-238">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-239">**檢查： StateMachineNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-239">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-240">**更新為： StateMachineNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-240">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-241">**檢查： FlowchartNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-241">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-242">**更新為： FlowchartNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-242">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-243">**檢查： FlowchartNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-243">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-244">**更新為： FlowchartNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-244">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-245">**檢查： SequentialNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-245">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-246">**更新為： SequentialNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-246">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-247">**檢查： SequentialNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-247">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-248">**更新為： SequentialNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-248">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-249">**檢查： SequentialNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-249">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-250">**更新為： SequentialNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-250">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-251">**檢查： StateMachineNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-251">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-252">**更新為： StateMachineNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-252">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-253">**檢查： FlowchartNumberGuessWorkflow;Version = 1.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-253">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="95966-254">**更新為： FlowchartNumberGuessWorkflow;Version = 1.5.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-254">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="95966-255">**檢查： StateMachineNumberGuessWorkflow;Version = 2.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-255">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="95966-256">**檢查： StateMachineNumberGuessWorkflow;Version = 2.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="95966-257">**檢查： FlowchartNumberGuessWorkflow;Version = 2.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-257">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="95966-258">**檢查： FlowchartNumberGuessWorkflow;Version = 2.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="95966-259">**檢查： SequentialNumberGuessWorkflow;Version = 2.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-259">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="95966-260">**檢查： SequentialNumberGuessWorkflow;Version = 2.0.0。0**</span><span class="sxs-lookup"><span data-stu-id="95966-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="95966-261">**按任意鍵繼續 .。。**</span><span class="sxs-lookup"><span data-stu-id="95966-261">**Press any key to continue . . .**</span></span>

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="95966-262">若要使用更新的工作流程執行應用程式</span><span class="sxs-lookup"><span data-stu-id="95966-262">To run the application with the updated workflows</span></span>

1. <span data-ttu-id="95966-263">以滑鼠右鍵按一下 **方案總管** 中的 [ **[numberguessworkflowhost]** ]，然後選擇 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="95966-263">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="95966-264">按 CTRL+F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="95966-264">Press CTRL+F5 to run the application.</span></span>

3. <span data-ttu-id="95966-265">按一下 [ **新遊戲** ] 以啟動新的工作流程，並記下狀態視窗下方的版本資訊，指出工作流程是 `v2` 工作流程。</span><span class="sxs-lookup"><span data-stu-id="95966-265">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>

4. <span data-ttu-id="95966-266">選取您在 how `v1` [To：裝載多個版本的工作流程並存](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) 主題的開頭所啟動的其中一個工作流程。</span><span class="sxs-lookup"><span data-stu-id="95966-266">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="95966-267">請注意，[狀態] 視窗下的版本資訊表示工作流程是 **1.5.0.0** 版的工作流程。</span><span class="sxs-lookup"><span data-stu-id="95966-267">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="95966-268">請注意，除太大或太小之外，沒有任何資訊指示先前的猜測。</span><span class="sxs-lookup"><span data-stu-id="95966-268">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>

    <span data-ttu-id="95966-269">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-269">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-270">**您猜得太低。**</span><span class="sxs-lookup"><span data-stu-id="95966-270">**Your guess is too low.**</span></span>

5. <span data-ttu-id="95966-271">記下 `InstanceId`，然後輸入猜測值，直到工作流程完成。</span><span class="sxs-lookup"><span data-stu-id="95966-271">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="95966-272">狀態視窗會顯示猜測內容的相關資訊，因為動態更新已更新 `WriteLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="95966-272">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>

    <span data-ttu-id="95966-273">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-273">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-274">**您的猜測太低。**</span><span class="sxs-lookup"><span data-stu-id="95966-274">**Your guess is too low.**</span></span>\
    <span data-ttu-id="95966-275">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-275">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-276">**5太低。**</span><span class="sxs-lookup"><span data-stu-id="95966-276">**5 is too low.**</span></span>\
    <span data-ttu-id="95966-277">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-277">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-278">**7太高。**</span><span class="sxs-lookup"><span data-stu-id="95966-278">**7 is too high.**</span></span>\
    <span data-ttu-id="95966-279">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-279">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-280">**恭喜您，您試了 4 次就猜到正確數字。**</span><span class="sxs-lookup"><span data-stu-id="95966-280">**Congratulations, you guessed the number in 4 turns.**</span></span>

6. <span data-ttu-id="95966-281">開啟 Windows 檔案總管並根據您的專案) 設定流覽至 [ **numberguessworkflowhost\bin\debug]** ] 資料夾 (或 [ **bin\release** ]，然後使用 [記事本] 來開啟對應至已完成工作流程的追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="95966-281">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="95966-282">如果您沒有記下， `InstanceId` 您可以使用 Windows 檔案總管中的 [ **修改日期** ] 資訊來識別正確的追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="95966-282">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="95966-283">追蹤資訊的最後一行包含新加入之 `WriteLine` 活動的輸出。</span><span class="sxs-lookup"><span data-stu-id="95966-283">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>

    <span data-ttu-id="95966-284">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-284">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-285">**您的猜測太低。**</span><span class="sxs-lookup"><span data-stu-id="95966-285">**Your guess is too low.**</span></span>\
    <span data-ttu-id="95966-286">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-286">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-287">**5太低。**</span><span class="sxs-lookup"><span data-stu-id="95966-287">**5 is too low.**</span></span>\
    <span data-ttu-id="95966-288">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-288">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-289">**7太高。**</span><span class="sxs-lookup"><span data-stu-id="95966-289">**7 is too high.**</span></span>\
    <span data-ttu-id="95966-290">**請輸入介於1到10之間的數位**</span><span class="sxs-lookup"><span data-stu-id="95966-290">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="95966-291">**6是正確的。您在4回合中猜到了。**</span><span class="sxs-lookup"><span data-stu-id="95966-291">**6 is correct. You guessed it in 4 turns.**</span></span>

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="95966-292">若要啟用舊版工作流程的啟動</span><span class="sxs-lookup"><span data-stu-id="95966-292">To enable starting previous versions of the workflows</span></span>

<span data-ttu-id="95966-293">如果您執行完工作流程來進行更新，可以修改 `NumberGuessWorkflowHost` 應用程式，使其能啟動工作流程的舊版本。</span><span class="sxs-lookup"><span data-stu-id="95966-293">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>

1. <span data-ttu-id="95966-294">在 **方案總管** 中按兩下 [ **workflowhostform.vb** ]，然後選取 [ **WorkflowType** ] 下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="95966-294">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>

2. <span data-ttu-id="95966-295">在 [ **屬性** ] 視窗中，選取 [ **items** ] 屬性，然後按一下省略號按鈕以編輯 **專案** 集合。</span><span class="sxs-lookup"><span data-stu-id="95966-295">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>

3. <span data-ttu-id="95966-296">將下列三個項目加入至集合。</span><span class="sxs-lookup"><span data-stu-id="95966-296">Add the following three items to the collection.</span></span>

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    <span data-ttu-id="95966-297">完成的 `Items` 集合中會有六個項目。</span><span class="sxs-lookup"><span data-stu-id="95966-297">The completed `Items` collection will have six items.</span></span>

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. <span data-ttu-id="95966-298">按兩下 **方案總管** 中的 [ **workflowhostform.vb** ]，然後選取 [**視圖程式碼**]。</span><span class="sxs-lookup"><span data-stu-id="95966-298">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>

5. <span data-ttu-id="95966-299">將三個新案例加入至 `switch` `Select Case` 處理常式中的 (或) 語句 `NewGame_Click` ，以將 [ **WorkflowType** ] 下拉式方塊中的新專案對應至相符的工作流程識別。</span><span class="sxs-lookup"><span data-stu-id="95966-299">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>

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

    <span data-ttu-id="95966-300">下列範例包含完整的 `switch` (或 `Select Case`) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="95966-300">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>

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

6. <span data-ttu-id="95966-301">按 CTRL+F5 建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="95966-301">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="95966-302">您現在可以啟動工作流程的 `v1` 版本以及目前版本。</span><span class="sxs-lookup"><span data-stu-id="95966-302">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="95966-303">若要動態更新這些新的實例，請執行 **] applydynamicupdate]** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="95966-303">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
