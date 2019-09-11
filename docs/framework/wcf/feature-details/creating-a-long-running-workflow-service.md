---
title: 建立長期執行的工作流程服務
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: ceda43cc41ceb3381b4700d6ea8b1871e368dccc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856200"
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="08a1f-102">建立長期執行的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="08a1f-102">Creating a Long-running Workflow Service</span></span>

<span data-ttu-id="08a1f-103">本主題會說明如何建立長時間執行的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="08a1f-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="08a1f-104">長時間執行的工作流程服務可能會執行一段很長的時間。</span><span class="sxs-lookup"><span data-stu-id="08a1f-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="08a1f-105">有時候，此工作流程可能會處於閒置狀態，等候其他某些資訊。</span><span class="sxs-lookup"><span data-stu-id="08a1f-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="08a1f-106">發生這種情況時，此工作流程會保存至 SQL 資料庫並從記憶體中移除。</span><span class="sxs-lookup"><span data-stu-id="08a1f-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="08a1f-107">當其他資訊可用時，此工作流程執行個體就會重新載入記憶體中並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="08a1f-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="08a1f-108">在本案例中，您要實作非常簡化的訂購系統。</span><span class="sxs-lookup"><span data-stu-id="08a1f-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="08a1f-109">用戶端會將初始訊息傳送至工作流程服務，以便啟動訂單。</span><span class="sxs-lookup"><span data-stu-id="08a1f-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="08a1f-110">然後，服務會將訂單 ID 傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="08a1f-110">It returns an order ID to the client.</span></span> <span data-ttu-id="08a1f-111">此時，工作流程服務會等候用戶端的其他訊息、進入閒置狀態並保存至 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="08a1f-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="08a1f-112">當用戶端傳送下一則訊息以訂購項目時，工作流程服務就會重新載入記憶體中，並且完成訂單處理作業。</span><span class="sxs-lookup"><span data-stu-id="08a1f-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="08a1f-113">在程式碼範例中，它會傳回一個字串，表示項目已經加入至訂單。</span><span class="sxs-lookup"><span data-stu-id="08a1f-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="08a1f-114">此程式碼範例並非採用此技術的實際應用程式，而是說明長時間執行工作流程服務的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="08a1f-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="08a1f-115">本主題假設您知道如何建立 Visual Studio 2012 專案和解決方案。</span><span class="sxs-lookup"><span data-stu-id="08a1f-115">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08a1f-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="08a1f-116">Prerequisites</span></span>

<span data-ttu-id="08a1f-117">您必須先安裝下列軟體，才能使用此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="08a1f-117">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="08a1f-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="08a1f-118">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="08a1f-119">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="08a1f-119">Visual Studio 2012</span></span>

3. <span data-ttu-id="08a1f-120">Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a1f-120">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="08a1f-121">您已熟悉 WCF 和 Visual Studio 2012，並知道如何建立專案/方案。</span><span class="sxs-lookup"><span data-stu-id="08a1f-121">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

### <a name="to-setup-the-sql-database"></a><span data-ttu-id="08a1f-122">若要設定 SQL 資料庫</span><span class="sxs-lookup"><span data-stu-id="08a1f-122">To Setup the SQL Database</span></span>

1. <span data-ttu-id="08a1f-123">為了保存工作流程服務執行個體，您必須已經安裝 Microsoft SQL Server 而且必須設定資料庫來儲存已保存的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="08a1f-123">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="08a1f-124">按一下 [**開始**] 按鈕、選取 [**所有程式**]、[ **Microsoft SQL Server 2008**] 和 **[Microsoft SQL Management Studio**]，以執行 microsoft sql Management Studio。</span><span class="sxs-lookup"><span data-stu-id="08a1f-124">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="08a1f-125">按一下 [連線 **]** 按鈕以登入 SQL Server 實例</span><span class="sxs-lookup"><span data-stu-id="08a1f-125">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="08a1f-126">以滑鼠右鍵按一下樹狀檢視中的 [**資料庫**]，然後選取 [**新增資料庫]。**</span><span class="sxs-lookup"><span data-stu-id="08a1f-126">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="08a1f-127">建立名`SQLPersistenceStore`為的新資料庫。</span><span class="sxs-lookup"><span data-stu-id="08a1f-127">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="08a1f-128">執行 SqlWorkflowInstanceStoreSchema.sql 指令碼檔 (位於 SQLPersistenceStore 資料庫的 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目錄中)，以便設定所需的資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="08a1f-128">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="08a1f-129">執行 SqlWorkflowInstanceStoreLogic.sql 指令碼檔 (位於 SQLPersistenceStore 資料庫的 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目錄中)，以便設定所需的資料庫邏輯。</span><span class="sxs-lookup"><span data-stu-id="08a1f-129">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="08a1f-130">若要建立 Web 裝載的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="08a1f-130">To Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="08a1f-131">建立空的 Visual Studio 2012 解決方案，將其`OrderProcessing`命名為。</span><span class="sxs-lookup"><span data-stu-id="08a1f-131">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="08a1f-132">將名為 `OrderService` 的新 WCF 工作流程服務應用程式專案加入至此方案。</span><span class="sxs-lookup"><span data-stu-id="08a1f-132">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="08a1f-133">在 [專案屬性] 對話方塊中，選取 [ **Web** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="08a1f-133">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="08a1f-134">在 [**起始動作**] 底下，選取`Service1.xamlx`[**特定頁面**]，並指定。</span><span class="sxs-lookup"><span data-stu-id="08a1f-134">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

        <span data-ttu-id="08a1f-135">![工作流程服務專案 Web 屬性](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "建立 web 裝載的工作流程服務特定頁面選項")</span><span class="sxs-lookup"><span data-stu-id="08a1f-135">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="08a1f-136">在 [**伺服器**] 下，選取 [**使用本機 IIS Web 服務器**]。</span><span class="sxs-lookup"><span data-stu-id="08a1f-136">Under **Servers** select **Use Local IIS Web server**.</span></span>

        <span data-ttu-id="08a1f-137">![本機 Web 服務器設定](./media/creating-a-long-running-workflow-service/use-local-web-server.png "建立 web 裝載的工作流程服務-使用本機 IIS Web 服務器選項")</span><span class="sxs-lookup"><span data-stu-id="08a1f-137">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        > <span data-ttu-id="08a1f-138">您必須在系統管理員模式下執行 Visual Studio 2012，才能進行這項設定。</span><span class="sxs-lookup"><span data-stu-id="08a1f-138">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

        <span data-ttu-id="08a1f-139">這兩個步驟會將工作流程服務專案設定為由 IIS 裝載。</span><span class="sxs-lookup"><span data-stu-id="08a1f-139">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="08a1f-140">如果`Service1.xamlx`尚未開啟，請開啟，並刪除現有的**ReceiveRequest**和**SendResponse**活動。</span><span class="sxs-lookup"><span data-stu-id="08a1f-140">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="08a1f-141">選取 [**順序服務**] 活動，然後按一下 [**變數**] 連結並加入下圖所示的變數。</span><span class="sxs-lookup"><span data-stu-id="08a1f-141">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="08a1f-142">這樣做就會加入一些之後將用於工作流程服務的變數。</span><span class="sxs-lookup"><span data-stu-id="08a1f-142">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="08a1f-143">如果 [CorrelationHandle] 不在 [變數型別] 下拉式選單中，請從下拉式下選取 **[流覽類型]** 。</span><span class="sxs-lookup"><span data-stu-id="08a1f-143">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="08a1f-144">在 [**類型名稱**] 方塊中輸入 CorrelationHandle，從清單方塊中選取 [CorrelationHandle]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="08a1f-144">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

    <span data-ttu-id="08a1f-145">![新增變數](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "將變數加入至順序服務活動。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-145">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="08a1f-146">將  **receiveandsendreply**  活動範本拖放到 **順序服務** 活動中。</span><span class="sxs-lookup"><span data-stu-id="08a1f-146">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="08a1f-147">這組活動將會接收用戶端的訊息並傳回回覆。</span><span class="sxs-lookup"><span data-stu-id="08a1f-147">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="08a1f-148">選取 [ **Receive** ] 活動，然後設定下圖中反白顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="08a1f-148">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

        <span data-ttu-id="08a1f-149">![設定 Receive 活動屬性](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "設定 Receive 活動屬性。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-149">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

        <span data-ttu-id="08a1f-150">DisplayName 屬性會針對設計工具中的 Receive 活動設定顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="08a1f-150">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="08a1f-151">ServiceContractName 和 OperationName 屬性會指定 Receive 活動所實作之服務合約和作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="08a1f-151">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="08a1f-152">如需有關如何在工作流程服務中使用合約的詳細資訊，請參閱[在工作流程中使用合約](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="08a1f-152">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="08a1f-153">按一下 [ **ReceiveStartOrder** ] 活動中的 [**定義**] 連結，然後設定下圖所示的屬性。</span><span class="sxs-lookup"><span data-stu-id="08a1f-153">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="08a1f-154">請注意，[**參數**] 選項按鈕已選取，名`p_customerName`為的參數`customerName`會系結至變數。</span><span class="sxs-lookup"><span data-stu-id="08a1f-154">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="08a1f-155">這會設定**receive**活動來接收某些資料，並將該資料系結至本機變數。</span><span class="sxs-lookup"><span data-stu-id="08a1f-155">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

        <span data-ttu-id="08a1f-156">![設定 Receive 活動所接收的資料](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "設定 Receive 活動所接收之資料的屬性。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-156">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="08a1f-157">選取 [ **SendReplyToReceive** ] 活動並設定反白顯示的屬性，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="08a1f-157">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

        <span data-ttu-id="08a1f-158">![設定 SendReply 活動的屬性](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="08a1f-158">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="08a1f-159">按一下 [ **SendReplyToStartOrder** ] 活動中的 [**定義**] 連結，然後設定下圖所示的屬性。</span><span class="sxs-lookup"><span data-stu-id="08a1f-159">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="08a1f-160">請注意，[**參數**] 選項按鈕已選取;名`p_orderId`為的參數會系結`orderId`至變數。</span><span class="sxs-lookup"><span data-stu-id="08a1f-160">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="08a1f-161">這項設定會指定 SendReplyToStartOrder 活動將字串型別的值傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="08a1f-161">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

        <span data-ttu-id="08a1f-162">設定![SendReply 活動內容資料](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "設定 SetReplyToStartOrder 活動的設定。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-162">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="08a1f-163">將 [Assign] 活動拖放到 [ **Receive** ] 和 [ **SendReply** ] 活動之間，然後設定屬性，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="08a1f-163">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

        <span data-ttu-id="08a1f-164">![新增 assign 活動](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "新增 [指派] 活動。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-164">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

        <span data-ttu-id="08a1f-165">這樣就會建立新的訂單 ID 並將此值放入 orderId 變數中。</span><span class="sxs-lookup"><span data-stu-id="08a1f-165">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="08a1f-166">選取 [ **ReplyToStartOrder** ] 活動。</span><span class="sxs-lookup"><span data-stu-id="08a1f-166">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="08a1f-167">在 [屬性] 視窗中，按一下 [ **CorrelationInitializers**] 的省略號按鈕。</span><span class="sxs-lookup"><span data-stu-id="08a1f-167">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="08a1f-168">選取 [**新增初始化運算式**] 連結`orderIdHandle` ，在 [初始化運算式] 文字方塊中輸入，選取相互關聯類型的 [查詢相互關聯初始化運算式]，然後選取 [XPATH 查詢] 下拉式方塊下的 [p_orderId]。</span><span class="sxs-lookup"><span data-stu-id="08a1f-168">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="08a1f-169">下圖將顯示這些設定。</span><span class="sxs-lookup"><span data-stu-id="08a1f-169">These settings are shown in the following illustration.</span></span> <span data-ttu-id="08a1f-170">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="08a1f-170">Click **OK**.</span></span>  <span data-ttu-id="08a1f-171">這樣就會初始化用戶端與這個工作流程服務執行個體之間的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="08a1f-171">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="08a1f-172">收到包含此訂單 ID 的訊息時，它就會路由傳送至這個工作流程服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="08a1f-172">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

        <span data-ttu-id="08a1f-173">![新增相互關聯初始化運算式](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "新增相互關聯初始化運算式。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-173">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="08a1f-174">將另一個  **receiveandsendreply**  活動拖放到工作流程的結尾（在包含第一個**Receive**和**SendReply**活動的**序列**外）。</span><span class="sxs-lookup"><span data-stu-id="08a1f-174">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="08a1f-175">這樣就會接收用戶端所傳送的第二則訊息並回應訊息。</span><span class="sxs-lookup"><span data-stu-id="08a1f-175">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="08a1f-176">選取包含新加入之**receive**和**SendReply**活動的**順序**，然後按一下 [**變數**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08a1f-176">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="08a1f-177">加入在下圖中反白顯示的變數：</span><span class="sxs-lookup"><span data-stu-id="08a1f-177">Add the variable highlighted in the following illustration:</span></span>

        <span data-ttu-id="08a1f-178">![加入新的變數](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "新增 ItemId 變數。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-178">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>

        <span data-ttu-id="08a1f-179">也會`orderResult`在 `Sequence`範圍中新增 as 字串。</span><span class="sxs-lookup"><span data-stu-id="08a1f-179">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="08a1f-180">選取 [ **Receive** ] 活動，然後設定下圖所示的屬性：</span><span class="sxs-lookup"><span data-stu-id="08a1f-180">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

        <span data-ttu-id="08a1f-181">![設定 Receive 活動屬性](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "設定 [接收活動屬性]。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-181">![Set the Receive activity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>

        > [!NOTE]
        > <span data-ttu-id="08a1f-182">別忘了使用 `../IAddItem`變更 ServiceContractName 欄位。</span><span class="sxs-lookup"><span data-stu-id="08a1f-182">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="08a1f-183">按一下  **receiveadditem 後面** 活動中的 **定義** 連結，然後加入下圖所示的參數：這會將 receive 活動設定為接受兩個參數，也就是訂單識別碼和要排序之專案的識別碼。</span><span class="sxs-lookup"><span data-stu-id="08a1f-183">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

        <span data-ttu-id="08a1f-184">![指定第二個接收的參數](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "設定 receive 活動以接收兩個參數。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-184">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="08a1f-185">按一下 [ **CorrelateOn** ] 省略號按鈕， `orderIdHandle`然後輸入。</span><span class="sxs-lookup"><span data-stu-id="08a1f-185">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="08a1f-186">在 [ **XPath 查詢**] 底下，按一下下拉式箭號`p_orderId`，然後選取 []。</span><span class="sxs-lookup"><span data-stu-id="08a1f-186">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="08a1f-187">這樣就會設定第二個 Receive 活動的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="08a1f-187">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="08a1f-188">如需相互關聯的詳細資訊，請參閱相互[關聯](../../../../docs/framework/wcf/feature-details/correlation.md)。</span><span class="sxs-lookup"><span data-stu-id="08a1f-188">For more information about correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>

        <span data-ttu-id="08a1f-189">![設定 CorrelatesOn 屬性](./media/creating-a-long-running-workflow-service/correlateson-setting.png "設定 CorrelatesOn 屬性。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-189">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="08a1f-190">將  **If**  活動立即拖放到**receiveadditem 後面**活動之後。</span><span class="sxs-lookup"><span data-stu-id="08a1f-190">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="08a1f-191">這個活動的運作方式就如同 if 陳述式。</span><span class="sxs-lookup"><span data-stu-id="08a1f-191">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="08a1f-192">將**Condition**屬性設定為`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="08a1f-192">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="08a1f-193">將 [**指派**] 活動拖放至 [ **Then** ] 區段，然後將另一個拖曳至 [ **Else** ] 區段，設定**指派**活動的屬性，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="08a1f-193">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

            <span data-ttu-id="08a1f-194">![指派服務呼叫的結果](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "指派服務呼叫的結果。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-194">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

            <span data-ttu-id="08a1f-195">如果條件為`true` ，則會執行 [ **Then** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="08a1f-195">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="08a1f-196">如果條件為`false` ，則會執行 [ **Else** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="08a1f-196">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="08a1f-197">選取 [ **SendReplyToReceive** ] 活動，然後設定下圖所示的 [ **DisplayName** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="08a1f-197">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

            <span data-ttu-id="08a1f-198">![設定 SendReply 活動屬性](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "設定 [SendReply 活動] 屬性。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-198">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="08a1f-199">按一下 [ **SetReplyToAddItem** ] 活動中的 [**定義**] 連結，並加以設定，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="08a1f-199">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="08a1f-200">這會設定**SendReplyToAddItem**活動，以傳回`orderResult`變數中的值。</span><span class="sxs-lookup"><span data-stu-id="08a1f-200">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

            <span data-ttu-id="08a1f-201">![設定 SendReply 活動的資料]系結(./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "設定 SendReplyToAddItem 活動的屬性。")</span><span class="sxs-lookup"><span data-stu-id="08a1f-201">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="08a1f-202">開啟 web.config 檔案，並在 [ \<行為 >] 區段中加入下列元素，以啟用工作流程持續性。</span><span class="sxs-lookup"><span data-stu-id="08a1f-202">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > <span data-ttu-id="08a1f-203">請務必取代上一個程式碼片段中的主機和 SQL Server 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="08a1f-203">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="08a1f-204">建置方案。</span><span class="sxs-lookup"><span data-stu-id="08a1f-204">Build the solution.</span></span>

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="08a1f-205">若要建立用戶端應用程式來呼叫工作流程服務</span><span class="sxs-lookup"><span data-stu-id="08a1f-205">To Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="08a1f-206">將名為 `OrderClient` 的新主控台應用程式專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="08a1f-206">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="08a1f-207">將下列組件的參考加入至 `OrderClient` 專案。</span><span class="sxs-lookup"><span data-stu-id="08a1f-207">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="08a1f-208">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="08a1f-208">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="08a1f-209">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="08a1f-209">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="08a1f-210">將服務參考加入至工作流程服務並將 `OrderService` 指定為命名空間。</span><span class="sxs-lookup"><span data-stu-id="08a1f-210">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="08a1f-211">在用戶端專案的 `Main()` 方法中，加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="08a1f-211">In the `Main()` method of the client project add the following code:</span></span>

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

5. <span data-ttu-id="08a1f-212">建置方案並執行 `OrderClient` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="08a1f-212">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="08a1f-213">用戶端就會顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="08a1f-213">The client will display the following text:</span></span>

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="08a1f-214">若要確認已保存工作流程服務，請前往 [**開始**] 功能表，選取 [**所有程式**]、[ **Microsoft SQL Server 2008**]、[ **SQL Server Management Studio**] 來啟動 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="08a1f-214">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="08a1f-215">在左窗格中，展開 [**資料庫**]、[ **SQLPersistenceStore**]、[ **Views** ]，然後以滑鼠右鍵按一下 [ **DurableInstancing 實例**]，然後選取 [**選取前 1000**個數據列]。</span><span class="sxs-lookup"><span data-stu-id="08a1f-215">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="08a1f-216">在 [**結果**] 窗格中，確認您至少看到一個列出的實例。</span><span class="sxs-lookup"><span data-stu-id="08a1f-216">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="08a1f-217">如果執行時發生例外狀況，可能會有先前執行的其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="08a1f-217">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="08a1f-218">若要刪除現有的資料列，請以滑鼠右鍵按一下 [ **DurableInstancing** ]，然後選取 [**編輯前 200**個數據列]，按下 [**執行**] 按鈕，選取 [結果] 窗格中的所有資料列，然後選取 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="08a1f-218">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="08a1f-219">若要確認顯示在資料庫中的執行個體就是應用程式所建立的執行個體，請先確認 Instances 檢視表是空的，然後再執行用戶端。</span><span class="sxs-lookup"><span data-stu-id="08a1f-219">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="08a1f-220">一旦用戶端執行之後，請重新執行查詢 (選取前 1000 個資料列) 並確認已經加入新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="08a1f-220">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="08a1f-221">按下 Enter，將 add item 訊息傳送至工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="08a1f-221">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="08a1f-222">用戶端就會顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="08a1f-222">The client will display the following text:</span></span>

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="08a1f-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08a1f-223">See also</span></span>

- [<span data-ttu-id="08a1f-224">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="08a1f-224">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
