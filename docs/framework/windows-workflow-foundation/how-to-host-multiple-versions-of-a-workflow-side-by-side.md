---
title: "HOW TO：裝載工作流程並存的多個版本 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09c575df-e0a3-4f3b-9e01-a7ac59d65287
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# HOW TO：裝載工作流程並存的多個版本
`WorkflowIdentity` 提供一種方法，讓工作流程應用程式開發人員能夠將名稱和版本與工作流程定義產生關聯性，並為這項資訊與持續性工作流程執行個體建立關聯性。此身分識別資訊可由工作流程應用程式開發人員使用以啟用案例 \(例如並存執行多個版本的工作流程定義\)，以及提供動態更新等其他功能的基礎。教學課程中的此步驟示範如何使用 `WorkflowIdentity` 同時裝載工作流程的多個版本。  
  
> [!NOTE]
>  若要下載教學課程的完整版或觀看影片逐步解說，請參閱 [Windows Workflow Foundation \(WF45\) \- 快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)。  
  
## 本主題內容  
 在教學課程的這個步驟中，會修改工作流程的 `WriteLine` 活動以提供其他資訊，並新增 `WriteLine` 活動。我們會儲存原始工作流程組件的複本，並更新主應用程式，以便同時執行原始和更新的工作流程。  
  
-   [製作 NumberGuessWorkflowActivities 專案的複本](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BackupCopy)  
  
-   [更新工作流程](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflows)  
  
    -   [更新狀態機器工作流程](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateStateMachine)  
  
    -   [更新流程圖工作流程](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateFlowchart)  
  
    -   [更新循序工作流程](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateSequential)  
  
-   [更新 WorkflowVersionMap 以包含舊版的工作流程](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [若要建置及執行應用程式](../../../docs/framework/windows-workflow-foundation//how-to-host-multiple-versions-of-a-workflow-side-by-side.md#BKMK_BuildAndRun)  
  
> [!NOTE]
>  依照本主題中的步驟進行之前，請執行應用程式、啟動每種型別的數個工作流程，然後針對每個工作流程進行一或兩次猜測。此步驟和下一個步驟 \([HOW TO：更新執行中工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation//how-to-update-the-definition-of-a-running-workflow-instance.md)\) 均使用這些保存的工作流程。  
  
> [!NOTE]
>  「快速入門教學課程」中的每個步驟都與之前的步驟息息相關。如果您未完成前面的步驟，可以從 [Windows Workflow Foundation \(WF45\)\-快速入門教學課程](http://go.microsoft.com/fwlink/?LinkID=248976)下載完整版的教學課程。  
  
###  <a name="BKMK_BackupCopy"></a> 製作 NumberGuessWorkflowActivities 專案的複本  
  
1.  在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中開啟 \[**WF45GettingStartedTutorial**\] 方案 \(如果尚未開啟\)。  
  
2.  按下 CTRL\+SHIFT\+B 建置方案。  
  
3.  關閉 \[**WF45GettingStartedTutorial**\] 方案。  
  
4.  開啟 \[Windows 檔案總管\]，並巡覽至教學課程方案檔和專案資料夾所在的資料夾。  
  
5.  在 \[**NumberGuessWorkflowHost**\] 和 \[**NumberGuessWorkflowActivities**\] 所在的資料夾中建立名為 \[**PreviousVersions**\] 的新資料夾。此資料夾用來儲存組件，這些組件包含在後續教學課程步驟中使用的不同工作流程版本。  
  
6.  巡覽至 \[**NumberGuessWorkflowActivities\\bin\\debug**\] 資料夾 \(或 \[**bin\\release**\]，取決於您的專案設定\)。複製 \[**NumberGuessWorkflowActivities.dll**\] 並將其貼入 \[**PreviousVersions**\] 資料夾。  
  
7.  將 \[**PreviousVersions**\] 資料夾中的 \[**NumberGuessWorkflowActivities.dll**\] 重新命名為 \[**NumberGuessWorkflowActivities\_v1.dll**\]。  
  
    > [!NOTE]
    >  本主題中的步驟示範管理組件的方法，這些組件用於包含多個工作流程版本。您也可以使用其他方法，例如強式命名組件以及在全域組件快取中登錄這些組件。  
  
8.  在儲存 \[**NumberGuessWorkflowHost**\]、\[**NumberGuessWorkflowActivities**\] 以及新加入之 \[**PreviousVersions**\] 資料夾的相同資料夾中，建立資料夾並將其命名為 \[**NumberGuessWorkflowActivities\_du**\]，然後將 \[**NumberGuessWorkflowActivities**\] 資料夾中的所有檔案和子資料夾複製到新的 \[**NumberGuessWorkflowActivities\_du**\] 資料夾中。[HOW TO：更新執行中工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation//how-to-update-the-definition-of-a-running-workflow-instance.md)中會使用活動初始版本專案的備份複本。  
  
9. 在 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中重新開啟 \[**WF45GettingStartedTutorial**\] 方案。  
  
###  <a name="BKMK_UpdateWorkflows"></a> 更新工作流程  
 本節已更新工作流程定義。已更新回應使用者猜測的兩個 `WriteLine` 活動，並新增可在猜測數字後提供遊戲其他相關資訊的 `WriteLine` 活動。  
  
####  <a name="BKMK_UpdateStateMachine"></a> 更新狀態機器工作流程  
  
1.  在 \[**方案總管**\] 中的 \[**NumberGuessWorkflowActivities**\] 專案下，按兩下 \[**StateMachineNumberGuessWorkflow.xaml**\]。  
  
2.  按兩下狀態機器上的 \[**猜測不正確**\] 轉換。  
  
3.  更新 `If` 活動中最左邊 `WriteLine` 的 `Text`。  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
4.  更新 `If` 活動中最右邊 `WriteLine` 的 `Text`。  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
5.  按一下工作流程設計工具最上方階層連接列中的 \[**StateMachine**\]，返回工作流程設計工具中的整體狀態機器檢視。  
  
6.  按兩下狀態機器上的 \[**猜測正確**\] 轉換。  
  
7.  從 \[**工具箱**\] 的 \[**Primitives**\] 區段，將 \[**WriteLine**\] 活動拖放到轉換的 \[**在此置放動作活動**\] 標籤上。  
  
8.  在 `Text` 屬性方塊中輸入下列運算式。  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateFlowchart"></a> 更新流程圖工作流程  
  
1.  在 \[**方案總管**\] 中的 \[**NumberGuessWorkflowActivities**\] 專案下，按兩下 \[**FlowchartNumberGuessWorkflow.xaml**\]。  
  
2.  更新最左邊 `WriteLine` 活動的 `Text`。  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  更新最右邊 `WriteLine` 活動的 `Text`。  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  從 \[**工具箱**\] 的 \[**Primitives**\] 區段，將 \[**WriteLine**\] 活動拖放到最上方 `FlowDecision` 之 `True` 動作的置放點。`WriteLine` 活動會加入到流程圖中，並連結至 `FlowDecision` 動作的 `True`。  
  
5.  在 `Text` 屬性方塊中輸入下列運算式。  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
####  <a name="BKMK_UpdateSequential"></a> 更新循序工作流程  
  
1.  在 \[**方案總管**\] 中的 \[**NumberGuessWorkflowActivities**\] 專案下，按兩下 \[**SequentialNumberGuessWorkflow.xaml**\]。  
  
2.  更新 `If` 活動中最左邊 `WriteLine` 的 `Text`。  
  
    ```vb  
    Guess & " is too low."  
    ```  
  
    ```csharp  
    Guess + " is too low."  
    ```  
  
3.  更新 `If` 活動中最右邊 `WriteLine` 活動的 `Text`。  
  
    ```vb  
    Guess & " is too high."  
    ```  
  
    ```csharp  
    Guess + " is too high."  
    ```  
  
4.  從 \[**工具箱**\] 的 \[**Primitives**\] 區段將 \[**WriteLine**\] 活動拖放到 \[**DoWhile**\] 活動之後，使 \[**WriteLine**\] 成為根 `Sequence` 活動中的最後一個活動。  
  
5.  在 `Text` 屬性方塊中輸入下列運算式。  
  
    ```vb  
    Guess & " is correct. You guessed it in " & Turns & " turns."  
    ```  
  
    ```csharp  
    Guess + " is correct. You guessed it in " + Turns + " turns."  
    ```  
  
###  <a name="BKMK_UpdateWorkflowVersionMap"></a> 更新 WorkflowVersionMap 以包含舊版的工作流程  
  
1.  按兩下 \[**NumberGuessWorkflowHost**\] 專案下的 \[**WorkflowVersionMap.cs**\] \(或 \[**WorkflowVersionMap.vb**\]\) 將它開啟。  
  
2.  將下列 `using` \(或 `Imports`\) 陳述式加入至檔案最上方的其他 `using` \(或 `Imports`\) 陳述式。  
  
    ```vb  
    Imports System.Reflection  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Reflection;  
    using System.IO;  
    ```  
  
3.  將三個新的工作流程識別加入到三個現有工作流程識別宣告的正下方。這些新的 `v1` 工作流程識別將用來針對在更新前啟動之工作流程，提供正確的工作流程定義。  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 Identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
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
    ```  
  
4.  在 `WorkflowVersionMap` 建構函式中，將三個目前工作流程識別的 `Version` 屬性更新為 `2.0.0.0`。  
  
    ```vb  
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
    ```  
  
    ```csharp  
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
    ```  
  
     將目前工作流程版本加入到字典中的程式碼會使用專案中參考的目前版本，因此您不需要更新初始化工作流程定義的程式碼。  
  
5.  將下列程式碼加入到建構函式中，放在將目前版本加入到字典中的程式碼之後。  
  
    ```vb  
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
    ```  
  
    ```csharp  
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
    ```  
  
     這些工作流程識別都與對應工作流程定義的初始版本相關聯。  
  
6.  接下來，載入包含工作流程定義初始版本的組件，建立對應的工作流程定義並將其加入到字典中。  
  
    ```vb  
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
    ```  
  
    ```csharp  
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
  
    ```  
  
     以下範例是更新之 `WorkflowVersionMap` 類別的完整清單。  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 Identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> 若要建置及執行應用程式  
  
1.  按下 CTRL\+SHIFT\+B 建置應用程式，然後按下 CTRL\+F5 啟動。  
  
2.  按一下 \[**New Game**\] 啟動新的工作流程。工作流程的版本會顯示在狀態視窗下，反映從相關聯的 `WorkflowIdentity` 更新的版本。記下 `InstanceId`，當工作流程完成時，您就可以檢視該工作流程的追蹤檔案，然後輸入猜測直到遊戲完成為止。請注意，狀態視窗中所顯示的使用者猜測資訊，會以 `WriteLine` 活動的更新為根據。  
  
 **請輸入 1 到 10 之間的數字**   
**5 太大了。**   
**請輸入 1 到 10 之間的數字**   
**3 太大了。**   
**請輸入 1 到 10 之間的數字**   
**1 太小了。**   
**請輸入 1 到 10 之間的數字**   
**恭喜您，您試了 4 次就猜到正確數字。**    
    > [!NOTE]
    >  即會顯示從 `WriteLine` 活動更新的文字，但不會顯示本主題中最後加入的 `WriteLine` 活動的輸出。這是因為狀態視窗是由 `PersistableIdle` 處理常式更新的。由於工作流程已完成且不會在最後一個活動之後閒置，因此不會呼叫 `PersistableIdle` 處理常式。但是，`Completed` 處理常式會在狀態視窗顯示類似的訊息。如果需要，可以將程式碼加入到 `Completed` 處理常式，從 `StringWriter` 擷取文字並將其顯示在狀態視窗中。  
  
3.  開啟 \[Windows 檔案總管\] 並巡覽至 \[**NumberGuessWorkflowHost\\bin\\debug**\] 資料夾 \(或 \[**bin\\release**\]，取決於您的專案設定\)，然後使用記事本開啟已完成工作流程對應的追蹤檔案。如果您沒有記下 `InstanceId`，可以使用 Windows 檔案總管中的 \[**修改日期**\] 資訊找到正確的追蹤檔案。  
  
 **請輸入 1 到 10 之間的數字**   
**5 太大了。**   
**請輸入 1 到 10 之間的數字**   
**3 太大了。**   
**請輸入 1 到 10 之間的數字**   
**1 太小了。**   
**請輸入 1 到 10 之間的數字**   
**2 是正確的。您試了 4 次就猜到正確數字。**      追蹤檔中包含更新的 `WriteLine` 輸出，包括在本主題中加入之 `WriteLine` 的輸出。  
  
4.  切換回猜數字應用程式，並選取其中一個在更新之前啟動的工作流程。您可以查看顯示在狀態視窗下方的版本資訊，找出目前選取之工作流程的版本。輸入一些猜測，請注意，狀態更新會比對 `WriteLine` 活動輸出與舊版的輸出，而且不包含使用者的猜測。這是因為這些工作流程使用的舊版工作流程定義不含 `WriteLine` 更新。  
  
     在下一個步驟 \([HOW TO：更新執行中工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation//how-to-update-the-definition-of-a-running-workflow-instance.md)\) 中，會更新執行中的 `v1` 工作流程執行個體，使其包含新的功能作為 `v2` 執行個體。