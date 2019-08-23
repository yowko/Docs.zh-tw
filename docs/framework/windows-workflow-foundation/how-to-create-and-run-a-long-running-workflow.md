---
title: 作法：建立及執行長時間執行的工作流程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 75fa4fcdef9bf8e2773264fff4a8404330909e6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962320"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>HOW TO：建立及執行長時間執行的工作流程
Windows Workflow Foundation (WF) 的其中一項主要功能是執行時間將閒置工作流程保存和卸載至資料庫的能力。 下列步驟[說明如何:執行工作流程](how-to-run-a-workflow.md) , 示範使用主控台應用程式裝載工作流程的基本概念。 範例包括啟動工作流程、工作流程開發週期處理常式，以及繼續使用書籤。 為有效示範工作流程持續性，必須要有較複雜的工作流程主機，以支援啟動與繼續使用多個工作流程執行個體。 教學課程中的這個步驟，示範如何建立 Windows 表單主應用程式，以支援啟動與繼續使用多個工作流程執行個體、工作流程持續性，並且為後續教學課程步驟中示範的追蹤和版本設定等進階功能提供基礎。  
  
> [!NOTE]
> 本教學課程步驟和後續步驟會使用下列三種工作[流程類型:建立工作流程](how-to-create-a-workflow.md)。 如果您未完成這三種類型, 您可以從[Windows Workflow Foundation (WF45)-消費者入門教學](https://go.microsoft.com/fwlink/?LinkID=248976)課程下載完整的步驟版本。  
  
> [!NOTE]
> 若要下載教學課程的完整版或觀看影片逐步解說, 請參閱[Windows Workflow Foundation (WF45)-消費者入門教學](https://go.microsoft.com/fwlink/?LinkID=248976)課程。  
  
## <a name="in-this-topic"></a>本主題內容  
  
- [若要建立持續性資料庫](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
- [若要加入 DurableInstancing 元件的參考](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
- [若要建立工作流程主機表單](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
- [若要加入表單的屬性和 helper 方法](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
- [設定實例存放區、工作流程生命週期處理常式和延伸模組](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
- [啟用啟動和繼續多個工作流程類型](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
- [啟動新的工作流程](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
- [繼續工作流程](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
- [終止工作流程](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
- [若要建立並執行應用程式](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
### <a name="BKMK_CreatePersistenceDatabase"></a>若要建立持續性資料庫  
  
1. 開啟 SQL Server Management Studio 並連接到本機伺服器, 例如 **.\SQLEXPRESS**。 以滑鼠右鍵按一下本機伺服器上的 [**資料庫**] 節點, 然後選取 [**新增資料庫**]。 將新的資料庫命名為**WF45GettingStartedTutorial**, 接受所有其他值, 然後選取 **[確定]** 。  
  
    > [!NOTE]
    > 在建立資料庫之前, 請確定您已在本機伺服器上**建立資料庫**許可權。  
  
2. 從 [檔案 ] 功能表中選擇 [**開啟**]、[檔案]。 瀏覽至下列資料夾：`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`  
  
     選取下列兩個檔案, 然後按一下 [**開啟**]。  
  
    - SqlWorkflowInstanceStoreLogic.sql  
  
    - SqlWorkflowInstanceStoreSchema.sql  
  
3. 從 [**視窗]** 功能表選擇 [ **sqlworkflowinstancestoreschema.sql** ]。 確定已在 [**可用的資料庫**] 下拉式選單中選取 [ **WF45GettingStartedTutorial** ], 然後從 [**查詢**] 功能表中選擇 [**執行**]。  
  
4. 從 [**視窗]** 功能表選擇 [ **sqlworkflowinstancestorelogic.sql** ]。 確定已在 [**可用的資料庫**] 下拉式選單中選取 [ **WF45GettingStartedTutorial** ], 然後從 [**查詢**] 功能表中選擇 [**執行**]。  
  
    > [!WARNING]
    >  務必按照正確順序執行前面的兩個步驟。 如果未按照正確順序執行查詢，會發生錯誤，而且也無法正確地設定持續性資料庫。  
  
### <a name="BKMK_AddReference"></a>若要加入 DurableInstancing 元件的參考  
  
1. 以滑鼠右鍵按一下**方案總管**中的 [ **[numberguessworkflowhost]** ], 然後選取 [**新增參考**]。  
  
2. 從 [**加入參考**] 清單中選取 [ `DurableInstancing` **元件**], 然後在 [**搜尋元件**] 方塊中輸入。 如此會篩選組件，讓您更容易選取所需的參考。  
  
3. 從 [**搜尋結果**] 清單中核取 [ **DurableInstancing** ] 和 [ **DurableInstancing** ] 旁邊的核取方塊, 然後按一下 **[確定]** 。  
  
### <a name="BKMK_CreateForm"></a>若要建立工作流程主機表單  
  
> [!NOTE]
> 此程序中的步驟描述如何手動加入及設定表單。 如果需要，可以下載教學課程的方案檔，並將完成的表單加入到專案中。 若要下載教學課程檔案, 請參閱[Windows Workflow Foundation (WF45)-消費者入門教學](https://go.microsoft.com/fwlink/?LinkID=248976)課程。 下載檔案之後, 以滑鼠右鍵按一下 [ **[numberguessworkflowhost]** ], 然後選擇 [**加入參考**]。 新增對**system.web**和**system.web**的參考。 如果您從 [新增]、[**新專案**] 功能表加入新的表單, 但必須在匯入表單時手動加入, 則會自動加入這些參考。 加入參考之後, 以滑鼠右鍵按一下**方案總管**中的 [ **[numberguessworkflowhost]** ], 然後選擇 [**加入**]、[**現有專案**]。 流覽至專案`Form`檔中的資料夾, 選取  **WorkflowHostForm.cs**  (或   **workflowhostform**), 然後按一下 **新增**。 如果您選擇匯入表單, 則可以跳到下一節,[以加入表單的屬性和 helper 方法](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)。  
  
1. 以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowhost]** , 然後選擇 [**加入**]、[**新增專案**]。  
  
2. 在 [**安裝**的範本] 清單中, 選擇 [ `WorkflowHostForm` **Windows Form**], 在 [**名稱**] 方塊中輸入, 然後按一下 [**新增**]。  
  
3. 設定表單中的下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|偽|  
    |大小|400, 420|  
  
4. 依指定順序將下列控制項加入到表單中，並依指示設定屬性。  
  
    |控制項|Property值|  
    |-------------|---------------------|  
    |**Button**|名稱：NewGame<br /><br /> 位置:13, 13<br /><br /> 大小：75, 23<br /><br /> 文字新遊戲|  
    |**Label**|位置:94, 18<br /><br /> 文字猜號碼，從 1 到|  
    |**ComboBox**|名稱：NumberRange<br /><br /> DropDownStyleDropDownList<br /><br /> Items：10、100、1000<br /><br /> 位置:228, 12<br /><br /> 大小：143, 21|  
    |**Label**|位置:13, 43<br /><br /> 文字工作流程類型|  
    |**ComboBox**|名稱：WorkflowType<br /><br /> DropDownStyleDropDownList<br /><br /> Items：StateMachineNumberGuessWorkflow、FlowchartNumberGuessWorkflow、SequentialNumberGuessWorkflow<br /><br /> 位置:94, 40<br /><br /> 大小：277, 21|  
    |**Label**|名稱：WorkflowVersion<br /><br /> 位置:13, 362<br /><br /> 文字工作流程版本|  
    |**GroupBox**|位置:13, 67<br /><br /> 大小：358, 287<br /><br /> 文字遊戲|  
  
    > [!NOTE]
    > 新增下列控制項時, 請將它們放入群組方塊中。  
  
    |控制項|Property值|  
    |-------------|---------------------|  
    |**Label**|位置:7, 20<br /><br /> 文字工作流程執行個體識別碼|  
    |**ComboBox**|名稱：InstanceId<br /><br /> DropDownStyleDropDownList<br /><br /> 位置:121, 17<br /><br /> 大小：227, 21|  
    |**Label**|位置:7, 47<br /><br /> 文字猜測|  
    |**TextBox**|名稱：猜測<br /><br /> 位置:50, 44<br /><br /> 大小：65, 20|  
    |**Button**|名稱：EnterGuess<br /><br /> 位置:121, 42<br /><br /> 大小：75, 23<br /><br /> 文字輸入猜測|  
    |**Button**|名稱：QuitGame<br /><br /> 位置:274, 42<br /><br /> 大小：75, 23<br /><br /> 文字結束|  
    |**TextBox**|名稱：WorkflowStatus<br /><br /> 位置:10, 73<br /><br /> 多行True<br /><br /> 唯讀True<br /><br /> 滾動垂直<br /><br /> 大小：338, 208|  
  
5. 將表單的**AcceptButton**屬性設定為**EnterGuess**。  
  
 下列範例示範完成的表單。  
  
 ![Windows Workflow Foundation 工作流程主機表單的螢幕擷取畫面。](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)  
  
### <a name="BKMK_AddHelperMethods"></a>若要加入表單的屬性和 helper 方法  
 本節中的步驟會將設定表單 UI 的屬性和 Helper 方法加入到表單類別中，以支援執行及繼續使用數字猜測工作流程。  
  
1. 以滑鼠右鍵按一下**方案總管**中的   **workflowhostform** , 然後選擇 **查看程式碼**。  
  
2. 將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3. 將下列成員宣告加入至 **workflowhostform**類別。  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    > 如果您的連接字串不同，請更新 `connectionString` 以參考您的資料庫。  
  
4. 將 `WorkflowInstanceId` 屬性加入至 `WorkflowFormHost` 類別。  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     下拉式方塊會顯示持續性工作流程實例識別碼的清單, `WorkflowInstanceId`而屬性會傳回目前選取的工作流程。 `InstanceId`  
  
5. 加入表單 `Load` 事件的處理常式。 若要加入處理常式, 請切換至表單的**設計檢視**, 按一下 [**屬性**] 視窗頂端的 [**事件**] 圖示, 然後按兩下 [**載入**]。  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6. 將下列程式碼加入至 `WorkflowHostForm_Load`。  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     當表單載入時，會設定 `SqlWorkflowInstanceStore`，範圍和工作流程型別下拉式方塊會設為預設值，而且持續性工作流程執行個體會加入至 `InstanceId` 下拉式方塊。  
  
7. 加入 `SelectedIndexChanged` 的 `InstanceId` 處理常式。 若要加入處理常式, 請切換至表單的 [**設計檢視**], 選取`InstanceId`下拉式方塊, 按一下 [**屬性**] 視窗頂端的 [**事件**] 圖示, 然後按兩下 [ **SelectedIndexChanged**]。  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8. 將下列程式碼加入至 `InstanceId_SelectedIndexChanged`。 只要使用者使用下拉式方塊選取工作流程，此處理常式就會更新狀態視窗。  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. 將下列 `ListPersistedWorkflows` 方法加入至表單類別。  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     `ListPersistedWorkflows` 會在執行個體存放區中查詢持續性工作流成執行個體，並將執行個體識別碼加入 `cboInstanceId` 下拉式方塊。  
  
10. 將下列 `UpdateStatus` 方法及對應的委派加入至表單類別。 此方法會將表單上的狀態視窗更新為目前執行中的工作流程狀態。  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. 將下列 `GameOver` 方法及對應的委派加入至表單類別。 當工作流程完成時, 這個方法會從**InstanceId**下拉式方塊中移除已完成工作流程的實例識別碼, 以更新表單 UI。  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
### <a name="BKMK_ConfigureWorkflowApplication"></a>設定實例存放區、工作流程生命週期處理常式和延伸模組  
  
1. 將 `ConfigureWorkflowApplication` 方法加入至表單類別。  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     此方法會設定 `WorkflowApplication`、加入所需的擴充，然後加入工作流程開發週期事件的處理常式。  
  
2. 在 `ConfigureWorkflowApplication` 中指定 `SqlWorkflowInstanceStore` 的 `WorkflowApplication`。  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3. 接下來，建立 `StringWriter` 執行個體，並將其加入到 `Extensions` 的 `WorkflowApplication` 集合中。 當新增至擴充`WriteLine` 功能時,它會捕捉所有活動輸出。`StringWriter` 工作流程閒置時，可以從 `WriteLine` 擷取 `StringWriter` 輸出並顯示在表單上。  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4. 加入 `Completed` 事件的下列處理常式。 當工作流程成功完成時，會在狀態視窗中顯示用來猜測數字的次數。 如果工作流程終止，會顯示導致終止的例外狀況資訊。 在處理常式結束時，會呼叫 `GameOver` 方法，此方法會移除工作流程清單中已完成的工作流程。  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5. 加入下列 `Aborted` 和 `OnUnhandledException` 處理常式。 不會從 `GameOver` 處理常式呼叫 `Aborted` 方法，因為當工作流程執行個體中止時，並沒有終止，稍後可以再繼續該執行個體。  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6. 加入下列 `PersistableIdle` 處理常式。 此處理常式會擷取所加入的 `StringWriter` 擴充，從 `WriteLine` 活動擷取輸出，並顯示在狀態視窗中。  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <xref:System.Activities.PersistableIdleAction> 列舉有三個值：<xref:System.Activities.PersistableIdleAction.None>、<xref:System.Activities.PersistableIdleAction.Persist> 及 <xref:System.Activities.PersistableIdleAction.Unload>。 <xref:System.Activities.PersistableIdleAction.Persist> 會使工作流程繼續持續，但不會導致工作流程卸載。 <xref:System.Activities.PersistableIdleAction.Unload> 會使工作流程繼續持續並卸載。  
  
     下列範例是完成的 `ConfigureWorkflowApplication` 方法。  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
### <a name="BKMK_WorkflowVersionMap"></a>啟用啟動和繼續多個工作流程類型  
 主機必須提供工作流程定義，才能繼續工作流程執行個體。 本教學課程包含三種工作流程型別，後續的教學課程將介紹這些類型的多個版本。 `WorkflowIdentity` 提供方法，讓主應用程式能夠將識別資訊與持續的工作流程執行個體建立關聯。 本節中的步驟示範如何建立公用程式類別，以協助將持續性工作流程執行個體的工作流程識別對應至相對應的工作流程定義。 如需`WorkflowIdentity`和版本設定的詳細資訊, 請參閱[使用 WorkflowIdentity 和版本控制](using-workflowidentity-and-versioning.md)。  
  
1. 以滑鼠右鍵按一下**方案總管**中的 **[numberguessworkflowhost]** , 然後選擇 [**新增**]、[**類別**]。 在`WorkflowVersionMap` [**名稱**] 方塊中輸入, 然後按一下 [**新增**]。  
  
2. 將下列 `using` 或 `Imports` 陳述式加入至檔案最上方的其他 `using` 或 `Imports` 陳述式。  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3. 用下列宣告取代 `WorkflowVersionMap` 類別宣告。  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
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
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
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
  
     `WorkflowVersionMap` 包含三個工作流程識別，其對應於此教學課程中的三個工作流程定義，在下列章節中，啟動及繼續使用工作流程時會使用這些識別。  
  
### <a name="BKMK_StartWorkflow"></a>啟動新的工作流程  
  
1. 加入 `Click` 的 `NewGame` 處理常式。 若要加入處理常式, 請切換至表單的**設計檢視**, 然後按兩下`NewGame`。 會加入 `NewGame_Click` 處理常式，且表單的檢視會切換成程式碼檢視。 每當使用者按一下此按鈕，就會啟動新的工作流程。  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. 將下列程式碼加入至 Click 處理常式。 此程式碼會建立工作流程的輸入引數字典，以引數名稱為索引鍵。 此字典有一個項目，其中包含從範圍下拉式方塊擷取之隨機產生號碼的範圍。  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3. 接下來，加入下列啟動工作流程的程式碼。 會使用 `WorkflowIdentity` Helper 類別，擷取對應至所選工作流程型別的 `WorkflowVersionMap` 和工作流程定義。 接下來會使用工作流程定義 `WorkflowApplication` 和輸入引數的字典來建立新的 `WorkflowIdentity` 執行個體。  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
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
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4. 接下來，加入下列程式碼，此程式碼會將工作流程加入到工作流程清單，並在表單上顯示該工作流程的版本資訊。  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5. 呼叫 `ConfigureWorkflowApplication` 以設定執行個體存放區、擴充，以及此 `WorkflowApplication` 執行個體的工作流程開發週期處理常式。  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6. 最後，請呼叫 `Run`。  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     下列範例是已完成的 `NewGame_Click` 處理常式。  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
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
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
### <a name="BKMK_ResumeWorkflow"></a>繼續工作流程  
  
1. 加入 `Click` 的 `EnterGuess` 處理常式。 若要加入處理常式, 請切換至表單的**設計檢視**, 然後按兩下`EnterGuess`。 每當使用者按一下此按鈕，就會繼續使用該工作流程。  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. 加入下列程式碼，以確保已在工作流程清單中選取工作流程，且使用者的猜測是有效的。  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3. 接下來，擷取持續性工作流程執行個體的 `WorkflowApplicationInstance`。 `WorkflowApplicationInstance` 代表尚未與工作流程定義相關聯的持續性工作流程執行個體。 `DefinitionIdentity` 的 `WorkflowApplicationInstance` 包含持續性工作流程執行個體的 `WorkflowIdentity`。 在本教學課程中，會使用 `WorkflowVersionMap` 公用程式類別，將 `WorkflowIdentity` 對應至正確的工作流程定義。 擷取工作流程定義後，會使用正確的工作流程定義來建立 `WorkflowApplication`。  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4. 建立 `WorkflowApplication` 後，呼叫 `ConfigureWorkflowApplication`，以設定執行個體存放區、工作流程開發週期處理常式和擴充。 每次建立新的 `WorkflowApplication` 時，都必須完成這些步驟，而且必須在將工作流程執行個體載入到 `WorkflowApplication` 之前完成。 載入工作流程後，會繼續進行使用者的猜測。  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5. 最後，清除猜測文字方塊，並準備表單以接受另一種猜測。  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     下列範例是已完成的 `EnterGuess_Click` 處理常式。  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
### <a name="BKMK_TerminateWorkflow"></a>終止工作流程  
  
1. 加入 `Click` 的 `QuitGame` 處理常式。 若要加入處理常式, 請切換至表單的**設計檢視**, 然後按兩下`QuitGame`。 每當使用者按一下此按鈕，就會終止目前選取的工作流程。  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. 將下列程式碼加入至 `QuitGame_Click` 處理常式。 此程式碼會先檢查，確定已在工作流程清單中選取工作流程。 接著會將持續性執行個體載入到 `WorkflowApplicationInstance`、使用 `DefinitionIdentity` 來判斷正確的工作流程定義，然後初始化 `WorkflowApplication`。 接下來會呼叫 `ConfigureWorkflowApplication` 以設定擴充和工作流程開發週期處理常式。 設定 `WorkflowApplication` 之後，會載入它，然後呼叫 `Terminate`。  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
### <a name="BKMK_BuildAndRun"></a> 若要建置及執行應用程式  
  
1. 按兩下**方案總管**中的 [ **Program.cs** ] (或 [ **Module1**]) 以顯示程式碼。  
  
2. 將下列 `using` (或 `Imports`) 陳述式加入至檔案最上方的其他 `using` (或 `Imports`) 陳述式。  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3. 移除或批註現有的工作流程裝載程式碼[, 方法如下:執行工作流程](how-to-run-a-workflow.md), 並以下列程式碼取代它。  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4. 以滑鼠右鍵按一下**方案總管**中的 [ **[numberguessworkflowhost]** ], 然後選擇 [**屬性**]。 在 [**應用程式**] 索引標籤中, 指定 [ **Windows 應用程式**] 作為**輸出類型**。 此步驟是選用性的，但如果不進行此步驟，除了表單外還會顯示主控台視窗。  
  
5. 按 Ctrl+Shift+B 建置應用程式。  
  
6. 確定 [ **[numberguessworkflowhost]** ] 已設定為 [啟動應用程式], 然後按下 Ctrl + F5 啟動應用程式。  
  
7. 選取猜測遊戲的範圍和要啟動的工作流程類型, 然後按一下 [**新遊戲**]。 在 [**猜測**] 方塊中輸入猜測, 然後按一下 [**移**至] 以提交您的猜測。 請注意，`WriteLine` 活動的輸出會顯示在表單上。  
  
8. 啟動數個使用不同工作流程類型和數位範圍的工作流程、輸入一些猜測, 然後從 [**工作流程實例識別碼**] 清單中選取來切換工作流程。  
  
     請注意，當您切換到新的工作流程時，先前的猜測和工作流程的進度都不會顯示在狀態視窗中。 不顯示狀態的原因是未擷取狀態，也未儲存在任何位置。 在教學課程的下一個步驟中[, 如何:建立自訂追蹤參與者](how-to-create-a-custom-tracking-participant.md), 您可以建立可儲存此資訊的自訂追蹤參與者。
