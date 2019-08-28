---
title: 建立長期執行的工作流程服務
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: e6206babdb728b6ce38c94441f775e1fdffe7d79
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040420"
---
# <a name="creating-a-long-running-workflow-service"></a>建立長期執行的工作流程服務

本主題會說明如何建立長時間執行的工作流程服務。 長時間執行的工作流程服務可能會執行一段很長的時間。 有時候，此工作流程可能會處於閒置狀態，等候其他某些資訊。 發生這種情況時，此工作流程會保存至 SQL 資料庫並從記憶體中移除。 當其他資訊可用時，此工作流程執行個體就會重新載入記憶體中並繼續執行。  在本案例中，您要實作非常簡化的訂購系統。  用戶端會將初始訊息傳送至工作流程服務，以便啟動訂單。 然後，服務會將訂單 ID 傳回給用戶端。 此時，工作流程服務會等候用戶端的其他訊息、進入閒置狀態並保存至 SQL Server 資料庫。  當用戶端傳送下一則訊息以訂購項目時，工作流程服務就會重新載入記憶體中，並且完成訂單處理作業。 在程式碼範例中，它會傳回一個字串，表示項目已經加入至訂單。 此程式碼範例並非採用此技術的實際應用程式，而是說明長時間執行工作流程服務的簡單範例。 本主題假設您知道如何建立 Visual Studio 2012 專案和解決方案。

## <a name="prerequisites"></a>必要條件

您必須先安裝下列軟體，才能使用此逐步解說：

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. 您已熟悉 WCF 和 Visual Studio 2012, 並知道如何建立專案/方案。

### <a name="to-setup-the-sql-database"></a>若要設定 SQL 資料庫

1. 為了保存工作流程服務執行個體，您必須已經安裝 Microsoft SQL Server 而且必須設定資料庫來儲存已保存的工作流程執行個體。 按一下 [**開始**] 按鈕、選取 [**所有程式**]、[ **Microsoft SQL Server 2008**] 和 **[Microsoft SQL Management Studio**], 以執行 microsoft sql Management Studio。

2. 按一下 [連線 **]** 按鈕以登入 SQL Server 實例

3. 以滑鼠右鍵按一下樹狀檢視中的 [**資料庫**], 然後選取 [**新增資料庫]。** 建立名`SQLPersistenceStore`為的新資料庫。

4. 執行 SqlWorkflowInstanceStoreSchema.sql 指令碼檔 (位於 SQLPersistenceStore 資料庫的 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目錄中)，以便設定所需的資料庫結構描述。

5. 執行 SqlWorkflowInstanceStoreLogic.sql 指令碼檔 (位於 SQLPersistenceStore 資料庫的 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目錄中)，以便設定所需的資料庫邏輯。

### <a name="to-create-the-web-hosted-workflow-service"></a>若要建立 Web 裝載的工作流程服務

1. 建立空的 Visual Studio 2012 解決方案, 將其`OrderProcessing`命名為。

2. 將名為 `OrderService` 的新 WCF 工作流程服務應用程式專案加入至此方案。

3. 在 [專案屬性] 對話方塊中, 選取 [ **Web** ] 索引標籤。

    1. 在 [**起始動作**] 底下, 選取`Service1.xamlx`[**特定頁面**], 並指定。

        ![工作流程服務專案 Web 屬性](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "建立 web 裝載的工作流程服務特定頁面選項")

    2. 在 [**伺服器**] 下, 選取 [**使用本機 IIS Web 服務器**]。

        ![本機 Web 服務器設定](./media/creating-a-long-running-workflow-service/use-local-web-server.png "建立 web 裝載的工作流程服務-使用本機 IIS Web 服務器選項")

        > [!WARNING]
        > 您必須在系統管理員模式下執行 Visual Studio 2012, 才能進行這項設定。

        這兩個步驟會將工作流程服務專案設定為由 IIS 裝載。

4. 如果`Service1.xamlx`尚未開啟, 請開啟, 並刪除現有的**ReceiveRequest**和**SendResponse**活動。

5. 選取 [**順序服務**] 活動, 然後按一下 [**變數**] 連結並加入下圖所示的變數。 這樣做就會加入一些之後將用於工作流程服務的變數。

    > [!NOTE]
    > 如果 [CorrelationHandle] 不在 [變數型別] 下拉式選單中, 請從下拉式下選取 **[流覽類型]** 。 在 [**類型名稱**] 方塊中輸入 CorrelationHandle, 從清單方塊中選取 [CorrelationHandle], 然後按一下 **[確定]** 。

    ![新增變數](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "將變數加入至順序服務活動。")

6. 將  **receiveandsendreply**  活動範本拖放到 **順序服務** 活動中。 這組活動將會接收用戶端的訊息並傳回回覆。

    1. 選取 [ **Receive** ] 活動, 然後設定下圖中反白顯示的屬性。

        ![設定 Receive 活動屬性](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "設定 Receive 活動屬性。")

        DisplayName 屬性會針對設計工具中的 Receive 活動設定顯示名稱。 ServiceContractName 和 OperationName 屬性會指定 Receive 活動所實作之服務合約和作業的名稱。 如需有關如何在工作流程服務中使用合約的詳細資訊, 請參閱[在工作流程中使用合約](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。

    2. 按一下 [ **ReceiveStartOrder** ] 活動中的 [**定義**] 連結, 然後設定下圖所示的屬性。  請注意, [**參數**] 選項按鈕已選取, 名`p_customerName`為的參數`customerName`會系結至變數。 這會設定**receive**活動來接收某些資料, 並將該資料系結至本機變數。

        ![設定 Receive 活動所接收的資料](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "設定 Receive 活動所接收之資料的屬性。")

    3. 選取 [ **SendReplyToReceive** ] 活動並設定反白顯示的屬性, 如下圖所示。

        ![設定 SendReply 活動的屬性](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. 按一下 [ **SendReplyToStartOrder** ] 活動中的 [**定義**] 連結, 然後設定下圖所示的屬性。 請注意, [**參數**] 選項按鈕已選取;名`p_orderId`為的參數會系結`orderId`至變數。 這項設定會指定 SendReplyToStartOrder 活動將字串型別的值傳回給呼叫端。

        設定![SendReply 活動內容資料](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "設定 SetReplyToStartOrder 活動的設定。")

    5. 將 [Assign] 活動拖放到 [ **Receive** ] 和 [ **SendReply** ] 活動之間, 然後設定屬性, 如下圖所示:

        ![新增 assign 活動](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "新增 [指派] 活動。")

        這樣就會建立新的訂單 ID 並將此值放入 orderId 變數中。

    6. 選取 [ **ReplyToStartOrder** ] 活動。 在 [屬性] 視窗中, 按一下 [ **CorrelationInitializers**] 的省略號按鈕。 選取 [**新增初始化運算式**] 連結`orderIdHandle` , 在 [初始化運算式] 文字方塊中輸入, 選取相互關聯類型的 [查詢相互關聯初始化運算式], 然後選取 [XPATH 查詢] 下拉式方塊下的 [p_orderId]。 下圖將顯示這些設定。 按一下 [確定 **Deploying Office Solutions**]。  這樣就會初始化用戶端與這個工作流程服務執行個體之間的相互關聯。 收到包含此訂單 ID 的訊息時，它就會路由傳送至這個工作流程服務執行個體。

        ![新增相互關聯初始化運算式](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "新增相互關聯初始化運算式。")

7. 將另一個  **receiveandsendreply**  活動拖放到工作流程的結尾 (在包含第一個**Receive**和**SendReply**活動的**序列**外)。 這樣就會接收用戶端所傳送的第二則訊息並回應訊息。

    1. 選取包含新加入之**receive**和**SendReply**活動的**順序**, 然後按一下 [**變數**] 按鈕。 加入在下圖中反白顯示的變數：

        ![加入新的變數](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "新增 ItemId 變數。")

        也會`orderResult`在 `Sequence`範圍中新增 as 字串。

    2. 選取 [ **Receive** ] 活動, 然後設定下圖所示的屬性:

        ![設定 Receive 活動屬性](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "設定 [接收活動屬性]。")

        > [!NOTE]
        > 別忘了使用 `../IAddItem`變更 ServiceContractName 欄位。

    3. 按一下  **receiveadditem 後面** 活動中的 **定義** 連結, 然後加入下圖所示的參數: 這會將 receive 活動設定為接受兩個參數, 也就是訂單識別碼和要排序之專案的識別碼。

        ![指定第二個接收的參數](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "設定 receive 活動以接收兩個參數。")

    4. 按一下 [ **CorrelateOn** ] 省略號按鈕, `orderIdHandle`然後輸入。 在 [ **XPath 查詢**] 底下, 按一下下拉式箭號`p_orderId`, 然後選取 []。 這樣就會設定第二個 Receive 活動的相互關聯。 如需相互關聯的詳細資訊, 請參閱相互[關聯](../../../../docs/framework/wcf/feature-details/correlation.md)。

        ![設定 CorrelatesOn 屬性](./media/creating-a-long-running-workflow-service/correlateson-setting.png "設定 CorrelatesOn 屬性。")

    5. 將  **If**  活動立即拖放到**receiveadditem 後面**活動之後。 這個活動的運作方式就如同 if 陳述式。

        1. 將**Condition**屬性設定為`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. 將 [**指派**] 活動拖放至 [ **Then** ] 區段, 然後將另一個拖曳至 [ **Else** ] 區段, 設定**指派**活動的屬性, 如下圖所示。

            ![指派服務呼叫的結果](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "指派服務呼叫的結果。")

            如果條件為`true` , 則會執行 [ **Then** ] 區段。 如果條件為`false` , 則會執行 [ **Else** ] 區段。

        3. 選取 [ **SendReplyToReceive** ] 活動, 然後設定下圖所示的 [ **DisplayName** ] 屬性。

            ![設定 SendReply 活動屬性](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "設定 [SendReply 活動] 屬性。")

        4. 按一下 [ **SetReplyToAddItem** ] 活動中的 [**定義**] 連結, 並加以設定, 如下圖所示。 這會設定**SendReplyToAddItem**活動, 以傳回`orderResult`變數中的值。

            ![設定 SendReply 活動的資料]系結(./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "設定 SendReplyToAddItem 活動的屬性。")

8. 開啟 web.config 檔案, 並在 [ \<行為 >] 區段中加入下列元素, 以啟用工作流程持續性。

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > 請務必取代上一個程式碼片段中的主機和 SQL Server 執行個體名稱。

9. 建置方案。

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>若要建立用戶端應用程式來呼叫工作流程服務

1. 將名為 `OrderClient` 的新主控台應用程式專案加入至方案。

2. 將下列組件的參考加入至 `OrderClient` 專案。

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. 將服務參考加入至工作流程服務並將 `OrderService` 指定為命名空間。

4. 在用戶端專案的 `Main()` 方法中，加入下列程式碼：

    ```csharp
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. 建置方案並執行 `OrderClient` 應用程式。 用戶端就會顯示下列文字：

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. 若要確認已保存工作流程服務, 請前往 [**開始**] 功能表, 選取 [**所有程式**]、[ **Microsoft SQL Server 2008**]、[ **SQL Server Management Studio**] 來啟動 SQL Server Management Studio。

    1. 在左窗格中, 展開 [**資料庫**]、[ **SQLPersistenceStore**]、[ **Views** ], 然後以滑鼠右鍵按一下 [ **DurableInstancing 實例**], 然後選取 [**選取前 1000**個數據列]。 在 [**結果**] 窗格中, 確認您至少看到一個列出的實例。 如果執行時發生例外狀況，可能會有先前執行的其他執行個體。 若要刪除現有的資料列, 請以滑鼠右鍵按一下 [ **DurableInstancing** ], 然後選取 [**編輯前 200**個數據列], 按下 [**執行**] 按鈕, 選取 [結果] 窗格中的所有資料列, 然後選取 [**刪除**]。  若要確認顯示在資料庫中的執行個體就是應用程式所建立的執行個體，請先確認 Instances 檢視表是空的，然後再執行用戶端。 一旦用戶端執行之後，請重新執行查詢 (選取前 1000 個資料列) 並確認已經加入新的執行個體。

7. 按下 Enter，將 add item 訊息傳送至工作流程服務。 用戶端就會顯示下列文字：

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>另請參閱

- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
