---
title: WCF 測試用戶端 (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: e637a2bb26bd0cc4bea653155c2a85ef5af19fd9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038357"
---
# <a name="wcf-test-client-wcftestclientexe"></a><span data-ttu-id="18ec5-102">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="18ec5-102">WCF Test Client (WcfTestClient.exe)</span></span>
<span data-ttu-id="18ec5-103">Windows Communication Foundation (WCF) 測試用戶端 (WcfTestClient) 是一種 GUI 工具, 可讓使用者輸入測試參數、將該輸入提交至服務, 以及查看服務傳回的回應。</span><span class="sxs-lookup"><span data-stu-id="18ec5-103">Windows Communication Foundation (WCF) Test Client (WcfTestClient.exe) is a GUI tool that enables users to input test parameters, submit that input to the service, and view the response that the service sends back.</span></span> <span data-ttu-id="18ec5-104">結合 WCF 服務主機時, 它提供了順暢的服務測試體驗。</span><span class="sxs-lookup"><span data-stu-id="18ec5-104">It provides a seamless service testing experience when combined with WCF Service Host.</span></span>

<span data-ttu-id="18ec5-105">您通常可以在下列位置找到 WCF 測試用戶端 (WcfTestClient): `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` -「社區」可能是「企業」、「專業」或「社區」的其中一個, 視安裝的 Visual Studio 層級而定。</span><span class="sxs-lookup"><span data-stu-id="18ec5-105">You can typically find the WCF Test Client (WcfTestClient.exe) in the following location: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - Community may be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed.</span></span>

## <a name="scenarios-for-using-test-client"></a><span data-ttu-id="18ec5-106">使用測試用戶端的案例</span><span class="sxs-lookup"><span data-stu-id="18ec5-106">Scenarios for Using Test Client</span></span>

<span data-ttu-id="18ec5-107">下列各節討論最常見的案例, 您可以使用 WCF 測試用戶端來簡化您的開發流程。</span><span class="sxs-lookup"><span data-stu-id="18ec5-107">The following sections discuss the most common scenarios in which you can use WCF Test Client to streamline your development process.</span></span>

### <a name="inside-visual-studio"></a><span data-ttu-id="18ec5-108">在 Visual Studio 內部</span><span class="sxs-lookup"><span data-stu-id="18ec5-108">Inside Visual Studio</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a><span data-ttu-id="18ec5-109">WCF 服務主機啟動具有單一服務的 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="18ec5-109">WCF Service Host Starts WCF Test Client with a Single Service</span></span>

<span data-ttu-id="18ec5-110">在您建立新的 WCF 服務專案並按下 F5 啟動偵錯工具之後, WCF 服務主機就會開始在您的專案中裝載服務。</span><span class="sxs-lookup"><span data-stu-id="18ec5-110">After you create a new WCF service project and press F5 to start the debugger, the WCF Service Host begins to host the service in your project.</span></span> <span data-ttu-id="18ec5-111">然後, WCF 測試用戶端會開啟並顯示在設定檔案中定義的服務端點清單。</span><span class="sxs-lookup"><span data-stu-id="18ec5-111">Then, WCF Test Client opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="18ec5-112">您可以測試參數並叫用服務，然後重複這個程序以持續測試及驗證服務。</span><span class="sxs-lookup"><span data-stu-id="18ec5-112">You can test the parameters and invoke the service, and repeat this process to continuously test and validate your service.</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a><span data-ttu-id="18ec5-113">WCF 服務主機啟動具有多個服務的 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="18ec5-113">WCF Service Host Starts WCF Test Client with Multiple Services</span></span>

<span data-ttu-id="18ec5-114">您也可以使用 WCF 測試用戶端, 協助您對包含多個服務的服務專案進行 debug。</span><span class="sxs-lookup"><span data-stu-id="18ec5-114">You can also use WCF Test Client to help debug a service project that contains multiple services.</span></span> <span data-ttu-id="18ec5-115">當 WCF 測試用戶端開啟時, 它會自動逐一查看專案中的服務清單, 並開啟它們進行測試。</span><span class="sxs-lookup"><span data-stu-id="18ec5-115">When WCF Test Client opens, it automatically iterates the list of services in your project and opens them for testing.</span></span>

### <a name="outside-visual-studio"></a><span data-ttu-id="18ec5-116">在 Visual Studio 外部</span><span class="sxs-lookup"><span data-stu-id="18ec5-116">Outside Visual Studio</span></span>

<span data-ttu-id="18ec5-117">您也可以叫用 Visual Studio 外部的 WCF 測試用戶端 (WcfTestClient), 以在網際網路上測試任意服務。</span><span class="sxs-lookup"><span data-stu-id="18ec5-117">You can also invoke the WCF Test Client (WcfTestClient.exe) outside Visual Studio to test an arbitrary service on the Internet.</span></span> <span data-ttu-id="18ec5-118">若要找出該工具，請移至下列位置：</span><span class="sxs-lookup"><span data-stu-id="18ec5-118">To locate the tool, go to the following location:</span></span>

<span data-ttu-id="18ec5-119">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`(其中的「社區」可以是「企業」、「專業」或「社區」的其中一個, 視電腦上安裝的 Visual Studio 層級而定)</span><span class="sxs-lookup"><span data-stu-id="18ec5-119">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (where community can be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed on the machine)</span></span>

<span data-ttu-id="18ec5-120">若要使用該工具，按兩下檔名即可從這個位置開啟，或者是從命令列進行啟動。</span><span class="sxs-lookup"><span data-stu-id="18ec5-120">To use the tool, double-click the file name to open it from this location, or launch it from a command line.</span></span>

<span data-ttu-id="18ec5-121">WCF 測試用戶端會接受任意數目的 Uri 做為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="18ec5-121">WCF Test Client takes an arbitrary number of URIs as command line arguments.</span></span>  <span data-ttu-id="18ec5-122">這些引數是可以測試的服務 URI。</span><span class="sxs-lookup"><span data-stu-id="18ec5-122">These are the URIs of services that can be tested.</span></span>

`wcfTestClient.exe URI1 URI2 …`

<span data-ttu-id="18ec5-123">在 [WCF 測試用戶端] 視窗開啟之後 ->, 按一下 [檔案] [**新增服務**], 然後輸入您想要開啟之服務的端點位址。</span><span class="sxs-lookup"><span data-stu-id="18ec5-123">After the WCF Test Client window is opened, click **File**->**Add Service**, and enter the endpoint address of the service you want to open.</span></span>

## <a name="wcf-test-client-user-interface"></a><span data-ttu-id="18ec5-124">WCF 測試用戶端使用者介面</span><span class="sxs-lookup"><span data-stu-id="18ec5-124">WCF Test Client User Interface</span></span>

<span data-ttu-id="18ec5-125">您可以搭配單一服務或多個服務使用 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="18ec5-125">You can use WCF Test Client with a single service or multiple services.</span></span>

### <a name="service-operations"></a><span data-ttu-id="18ec5-126">服務作業</span><span class="sxs-lookup"><span data-stu-id="18ec5-126">Service Operations</span></span>

<span data-ttu-id="18ec5-127">[WCF 測試用戶端] 主視窗的左窗格會列出所有可用的服務, 以及其各自的端點和作業。</span><span class="sxs-lookup"><span data-stu-id="18ec5-127">The left pane of the WCF Test Client main window lists all the available services, along with their respective endpoints and operations.</span></span>

<span data-ttu-id="18ec5-128">按兩下某項作業時，您可以在右窗格中具有該作業名稱的新索引標籤內，檢視其內容。</span><span class="sxs-lookup"><span data-stu-id="18ec5-128">When you double-click an operation, you can view its content in the right pane inside a new tab with the operation's name.</span></span>

<span data-ttu-id="18ec5-129">左窗格還會列出用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="18ec5-129">The left pane also lists client configuration files.</span></span> <span data-ttu-id="18ec5-130">按兩下任何項目，即可在右窗格中新出現的索引視窗上看見檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="18ec5-130">Double-click any of the items to display the content of the file in a new tabbed window in the right pane.</span></span>

### <a name="entering-test-parameters"></a><span data-ttu-id="18ec5-131">輸入測試參數</span><span class="sxs-lookup"><span data-stu-id="18ec5-131">Entering Test Parameters</span></span>

<span data-ttu-id="18ec5-132">若要檢視測試參數，請按兩下作業，在右窗格中開啟它。</span><span class="sxs-lookup"><span data-stu-id="18ec5-132">To view the test parameters, double-click an operation to open it in the right pane.</span></span> <span data-ttu-id="18ec5-133">根據預設, 參數會顯示在**格式化**視圖中, 您可以為參數輸入任意值來測試服務。</span><span class="sxs-lookup"><span data-stu-id="18ec5-133">The parameters are showed in **Formatted** view by default, and you can enter arbitrary values for the parameters to test the service.</span></span>

<span data-ttu-id="18ec5-134">若要查看訊息的 XML, 請按一下 [ **xml**]。</span><span class="sxs-lookup"><span data-stu-id="18ec5-134">To view the message's XML, click **XML**.</span></span> <span data-ttu-id="18ec5-135">若要將它們傳送至服務,請按一下 [叫用]。</span><span class="sxs-lookup"><span data-stu-id="18ec5-135">To send them to the service, click **Invoke**.</span></span>

<span data-ttu-id="18ec5-136">針對資料集參數, 按一下 [ **...** ]</span><span class="sxs-lookup"><span data-stu-id="18ec5-136">For a DataSet parameter, click the **…**</span></span> <span data-ttu-id="18ec5-137">按鈕, 位於 [**編輯**] 旁 。</span><span class="sxs-lookup"><span data-stu-id="18ec5-137">button next to **Edit…**</span></span> <span data-ttu-id="18ec5-138">若要在顯示 DataGrid 的新視窗中編輯它。</span><span class="sxs-lookup"><span data-stu-id="18ec5-138">to edit it in a new window showing the DataGrid.</span></span> <span data-ttu-id="18ec5-139">請注意 [**複製資料集**] 和 [**貼上資料集**] 按鈕的外觀。</span><span class="sxs-lookup"><span data-stu-id="18ec5-139">Notice the appearance of the **Copy DataSet** and **Paste DataSet** buttons.</span></span> <span data-ttu-id="18ec5-140">如果在第一次編輯時 DataSet 物件的結構描述為未知，DataGrid 為空白。</span><span class="sxs-lookup"><span data-stu-id="18ec5-140">If the schema of the DataSet object is unknown upon the first edit, the DataGrid is empty.</span></span> <span data-ttu-id="18ec5-141">您必須將具有相同結構描述的 DataSet 物件貼入 DataGrid 中的目前物件</span><span class="sxs-lookup"><span data-stu-id="18ec5-141">You have to paste a DataSet object with the same schema into the current object in the DataGrid.</span></span> <span data-ttu-id="18ec5-142">(請注意，您必須在貼上作業前從其他地方複製結構描述)。您也可以按一下 [**複製資料集**] 按鈕, 以複製資料集物件供未來使用。</span><span class="sxs-lookup"><span data-stu-id="18ec5-142">(Notice that you need to copy the schema from somewhere else before the paste operation.) You can also copy a Dataset object for future usage by clicking the **Copy DataSet** button.</span></span>

<span data-ttu-id="18ec5-143">服務的回應會出現在測試參數下方。</span><span class="sxs-lookup"><span data-stu-id="18ec5-143">The service's response appears below the test parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="18ec5-144">如果預期的傳回值是字串，則結果會顯示為引號括住的字串，即使提供的輸入並未以引號括住。</span><span class="sxs-lookup"><span data-stu-id="18ec5-144">If the expected return value is a string, the result will be displayed as a quoted string even though the input provided was not in quotes.</span></span>

<span data-ttu-id="18ec5-145">如果您在建立服務合約時將特定作業指定為單向，就不會顯示任何服務回應。</span><span class="sxs-lookup"><span data-stu-id="18ec5-145">If you specified a particular operation as one-way when you created the contract for the service, no service response is displayed.</span></span> <span data-ttu-id="18ec5-146">訊息一旦排入佇列中準備傳遞，快顯對話方塊就會出現，通知您已成功傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="18ec5-146">As soon as the message is queued for delivery, a dialog box pops up to notify you that the message was successfully sent.</span></span>

### <a name="session-support"></a><span data-ttu-id="18ec5-147">工作階段支援</span><span class="sxs-lookup"><span data-stu-id="18ec5-147">Session Support</span></span>

<span data-ttu-id="18ec5-148">服務作業的索引標籤中的 [**啟動新 proxy** ] 核取方塊, 可讓您切換會話支援。</span><span class="sxs-lookup"><span data-stu-id="18ec5-148">The **Start a new proxy** check box in a service operation's tab enables you to toggle session support.</span></span> <span data-ttu-id="18ec5-149">這個方塊預設為清除。</span><span class="sxs-lookup"><span data-stu-id="18ec5-149">This box is cleared by default.</span></span>

<span data-ttu-id="18ec5-150">當您針對特定作業 (或是相同服務端點中的其他作業) 輸入測試參數, 並按一下 [多次叫用] 核取方塊時, 這些作業會共用一個 proxy, 而服務狀態會保存在多個業務.</span><span class="sxs-lookup"><span data-stu-id="18ec5-150">When you enter test parameters for a specific operation (or another operation in the same service endpoint) and click **Invoke** multiple times with the check box cleared, these operations share one proxy and the service status is persisted across multiple operations.</span></span>

<span data-ttu-id="18ec5-151">如果已核取 [**啟動新 proxy** ] 核取方塊, 則會針對每個叫用新的 proxy, 先前的會話案例會結束, 且服務狀態會是 [重設]。</span><span class="sxs-lookup"><span data-stu-id="18ec5-151">If the **Start a new proxy** check box is checked, a new proxy is started for each **Invoke**, the previous session scenario is ended, and the service status is reset.</span></span>

### <a name="editing-client-configuration"></a><span data-ttu-id="18ec5-152">編輯用戶端組態</span><span class="sxs-lookup"><span data-stu-id="18ec5-152">Editing Client Configuration</span></span>

<span data-ttu-id="18ec5-153">[WCF 測試用戶端] 主視窗的左窗格會列出用戶端設定檔案。</span><span class="sxs-lookup"><span data-stu-id="18ec5-153">The left pane of the WCF Test Client main window lists client configuration files.</span></span> <span data-ttu-id="18ec5-154">按兩下任何項目，即可在右窗格中顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="18ec5-154">Double-click any of the items to display the contents of the file in the right pane.</span></span>

#### <a name="edit-with-service-configuration-editor"></a><span data-ttu-id="18ec5-155">使用服務組態編輯器進行編輯</span><span class="sxs-lookup"><span data-stu-id="18ec5-155">Edit with Service Configuration Editor</span></span>

<span data-ttu-id="18ec5-156">以滑鼠右鍵按一下左窗格中的 [**設定檔**], 然後選取內容功能表 [**以 svcconfigeditor.exe 編輯**]。</span><span class="sxs-lookup"><span data-stu-id="18ec5-156">Right-click **Config File** in the left pane and select the context menu **Edit with SvcConfigEditor**.</span></span> <span data-ttu-id="18ec5-157">服務組態編輯器隨即啟動，並顯示用戶端組態內容。</span><span class="sxs-lookup"><span data-stu-id="18ec5-157">Service Configuration Editor is launched with the client configuration content.</span></span> <span data-ttu-id="18ec5-158">您可以在該工具內編輯組態並進行儲存。</span><span class="sxs-lookup"><span data-stu-id="18ec5-158">You can edit the configuration and save it within the tool.</span></span>

<span data-ttu-id="18ec5-159">在 [服務設定編輯器] 中儲存檔案之後, WCF 測試用戶端會顯示一則警告訊息, 告知您檔案已在外部修改, 並詢問您是否要重載該檔案。</span><span class="sxs-lookup"><span data-stu-id="18ec5-159">After saving the file in Service Configuration Editor, WCF Test Client displays a warning message to inform you that the file has been modified outside and asks whether you would like to reload it.</span></span>

<span data-ttu-id="18ec5-160">如果您選取 [**是]** , [Client. .dll .config] 索引標籤中的設定內容就會反映您在編輯器中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="18ec5-160">If you select **Yes**, the configuration content in the "Client.dll.config" tab reflects the changes you made in the editor.</span></span>

<span data-ttu-id="18ec5-161">如果您選取 [**否**], 則 [Client .dll .config] 索引標籤中的設定內容會維持不變, 而且修改後的內容會自動儲存至來源檔案。</span><span class="sxs-lookup"><span data-stu-id="18ec5-161">If you select **No**, the configuration content in the "Client.dll.config" tab remains unchanged and the modified content is automatically saved to the source file.</span></span>

#### <a name="restore-to-default-configuration"></a><span data-ttu-id="18ec5-162">還原至預設組態</span><span class="sxs-lookup"><span data-stu-id="18ec5-162">Restore to Default Configuration</span></span>

<span data-ttu-id="18ec5-163">如果您想要取消所有變更並還原為預設用戶端設定, 請以滑鼠右鍵按一下左窗格中的 [**設定檔**], 然後選取內容功能表 [**還原為預設**設定]。預設的設定值已載入, 且會還原 [Client .dll .config] 索引標籤中的內容。</span><span class="sxs-lookup"><span data-stu-id="18ec5-163">If you want to cancel all the changes and restore to the default client configuration, right-click **Config File** in the left pane and select the context menu **Restore to Default Config**. The default configuration value is loaded and content in "Client.dll.config" tab is restored.</span></span>

#### <a name="validate-changes"></a><span data-ttu-id="18ec5-164">驗證變更</span><span class="sxs-lookup"><span data-stu-id="18ec5-164">Validate Changes</span></span>

<span data-ttu-id="18ec5-165">在 WCF 測試用戶端中載入儲存的變更時, 會檢查設定是否符合 WCF 架構的有效性。</span><span class="sxs-lookup"><span data-stu-id="18ec5-165">When saved changes are being loaded in WCF Test Client, the configuration is checked for validity against WCF schema.</span></span> <span data-ttu-id="18ec5-166">如果發現錯誤，會顯示對話方塊說明錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="18ec5-166">If errors are found, a dialog box is displayed to show error details.</span></span>

<span data-ttu-id="18ec5-167">在 proxy 產生、二進位編譯或服務叫用期間, 支援編輯的功能表項目 (也就是「編輯 ...」、「還原 ...」等等) 都會停用。</span><span class="sxs-lookup"><span data-stu-id="18ec5-167">During proxy generation, binary compiling, or service invoking, menu items that support editing (that is, "Edit …", "Restore …", and so on) are disabled.</span></span> <span data-ttu-id="18ec5-168">將更新的設定載入至 WCF 測試用戶端時, 也會停用服務調用。</span><span class="sxs-lookup"><span data-stu-id="18ec5-168">Service invocation is also disabled when loading updated configuration to WCF Test Client.</span></span>

#### <a name="persist-client-configuration"></a><span data-ttu-id="18ec5-169">保存用戶端組態</span><span class="sxs-lookup"><span data-stu-id="18ec5-169">Persist Client Configuration</span></span>

<span data-ttu-id="18ec5-170">[**工具**->] [**選項**->] [**用戶端**設定] 索引標籤包含 [**啟動服務時永遠重新**產生設定] 選項 (預設為啟用)。</span><span class="sxs-lookup"><span data-stu-id="18ec5-170">The **Tools**->**Options**->**Client Configuration** tab contains an **Always Regenerate Config When Launching Services** option, which is enabled by default.</span></span> <span data-ttu-id="18ec5-171">此選項指定每次 WCF 測試用戶端載入服務時, 它會根據最新的服務合約和服務 App.config 檔案重新產生設定檔。</span><span class="sxs-lookup"><span data-stu-id="18ec5-171">This option specifies that every time WCF Test Client loads a service, it regenerates a configuration file based on the latest service contract and service App.config files.</span></span>

<span data-ttu-id="18ec5-172">如果您已編輯 WCF 服務的用戶端設定, 而且想要一律使用這個更新過的檔案來進行服務的偵錯工具, 您可以取消選取 [**重新**產生] 選項。</span><span class="sxs-lookup"><span data-stu-id="18ec5-172">If you have edited the client configuration for your WCF service and want to always use this updated file to debug your service, you can uncheck the **Regenerate** option.</span></span> <span data-ttu-id="18ec5-173">如此一來, 即使您更新服務並重新開啟 WCF 測試用戶端, 也是您先前更新的檔案, 而不是根據更新的服務重新產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="18ec5-173">By doing so, even when you update the service and reopen WCF Test Client, the Client.dll.config file is the one you updated previously instead of a regenerated one based on the updated service.</span></span>

<span data-ttu-id="18ec5-174">但是，您可能需要編輯組態檔，讓其跟重新產生的 Proxy 一致。</span><span class="sxs-lookup"><span data-stu-id="18ec5-174">However, you might need to edit the configuration file to make it consistent with the regenerated proxy.</span></span> <span data-ttu-id="18ec5-175">如果重新產生的 Proxy 和組態檔因更新服務而不相符，則在叫用服務時將發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="18ec5-175">If the regenerated proxy and configuration file are mismatched due to an updated service, errors will occur when the service is invoked.</span></span>

> [!CAUTION]
> <span data-ttu-id="18ec5-176">如果您修改過用戶端組態檔並選擇供往後重複使用，則可以在下列位置找到該檔案：</span><span class="sxs-lookup"><span data-stu-id="18ec5-176">If you have modified the client configuration file and select to reuse it in the future, you can find the file in the following location:</span></span>
>
> <span data-ttu-id="18ec5-177">\Documents 和設定\\[使用者帳戶] \My Documents\Test 用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="18ec5-177">\Documents and Settings\\[User Account]\My Documents\Test Client Projects.</span></span>
>
> <span data-ttu-id="18ec5-178">任何儲存在用戶端組態檔中經過更新的認證資訊，皆受到這個資料夾的存取控制清單 (ACL) 所保護。</span><span class="sxs-lookup"><span data-stu-id="18ec5-178">Any updated credential information stored to the client configuration file is protected by the Access Control List (ACL) of this folder.</span></span>

### <a name="adding-removing-and-refreshing-services"></a><span data-ttu-id="18ec5-179">新增、移除和重新整理服務</span><span class="sxs-lookup"><span data-stu-id="18ec5-179">Adding, Removing and Refreshing Services</span></span>

#### <a name="add-service"></a><span data-ttu-id="18ec5-180">新增服務</span><span class="sxs-lookup"><span data-stu-id="18ec5-180">Add Service</span></span>

<span data-ttu-id="18ec5-181">按一下 [檔案] [**新增服務**], 將服務新增至 WCF 測試用戶端。 -></span><span class="sxs-lookup"><span data-stu-id="18ec5-181">Click **File**->**Add Service** to add a service to WCF Test Client.</span></span> <span data-ttu-id="18ec5-182">接著會要求您輸入要新增之服務的 URI (端點位址)。</span><span class="sxs-lookup"><span data-stu-id="18ec5-182">You are then required to type the URI (endpoint address) of the service to be added.</span></span> <span data-ttu-id="18ec5-183">服務位址可以是 Mex 位址或 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="18ec5-183">The service’s address can be a mex address or WSDL address.</span></span>

<span data-ttu-id="18ec5-184">您也可以在 [**最近使用的服務**] 子功能表中, 找到10個最近新增的服務端點清單。</span><span class="sxs-lookup"><span data-stu-id="18ec5-184">You can also find a list of 10 recently added services' endpoints in the **Recent Services** submenu.</span></span> <span data-ttu-id="18ec5-185">如果您選取其中一個, 則會將指定的服務加入至 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="18ec5-185">If you select one of them, the specified service is added to WCF Test Client.</span></span>

<span data-ttu-id="18ec5-186">您也可以用滑鼠右鍵按一下服務樹狀目錄 [**我的服務專案**] 的根, 然後選取 [**新增服務**] 來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="18ec5-186">You can also right-click the root of service tree **My Service Projects**, and select **Add Service** to achieve the same result.</span></span>

<span data-ttu-id="18ec5-187">在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援新增服務的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="18ec5-187">During proxy generation, binary compiling, or service invocation, menu items that support adding a service are disabled.</span></span> <span data-ttu-id="18ec5-188">同時也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="18ec5-188">Service invocation is also disabled.</span></span>

#### <a name="remove-service"></a><span data-ttu-id="18ec5-189">移除服務</span><span class="sxs-lookup"><span data-stu-id="18ec5-189">Remove Service</span></span>

<span data-ttu-id="18ec5-190">以滑鼠右鍵按一下要移除之服務的服務根目錄, 然後選取 [**移除服務**], 從 WCF 測試用戶端移除服務。</span><span class="sxs-lookup"><span data-stu-id="18ec5-190">Right-click the service root of the service to be removed, and select **Remove Service** to remove a service from WCF Test Client.</span></span>

<span data-ttu-id="18ec5-191">在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援移除服務的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="18ec5-191">During proxy generation, binary compiling, or service invocation, menu items that support removing a service are disabled.</span></span> <span data-ttu-id="18ec5-192">同時也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="18ec5-192">Service invocation is also disabled.</span></span>

#### <a name="refresh-service"></a><span data-ttu-id="18ec5-193">重新整理服務</span><span class="sxs-lookup"><span data-stu-id="18ec5-193">Refresh Service</span></span>

<span data-ttu-id="18ec5-194">如果在執行 WCF 測試用戶端時對服務進行變更, 而您想要確保該服務的 WCF 測試用戶端執行是最新的, 請以滑鼠右鍵按一下服務的服務根目錄, 然後選取 [重新整理**服務**]。</span><span class="sxs-lookup"><span data-stu-id="18ec5-194">If a change is made to the service while WCF Test Client is running and you want to ensure that the WCF Test Client implementation for that service is up-to-date, right-click the service root of the service, and select **Refresh Service**.</span></span> <span data-ttu-id="18ec5-195">請注意，重新整理後會重設服務狀態。</span><span class="sxs-lookup"><span data-stu-id="18ec5-195">Note that after refreshing, the service status is reset.</span></span>

<span data-ttu-id="18ec5-196">在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援重新整理服務的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="18ec5-196">During proxy generation, binary compiling, or service invocation, menu items that support refreshing a service are disabled.</span></span> <span data-ttu-id="18ec5-197">同時也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="18ec5-197">Service invocation is also disabled.</span></span>

## <a name="location-of-files-generated-by-the-test-client"></a><span data-ttu-id="18ec5-198">測試用戶端產生的檔案位置</span><span class="sxs-lookup"><span data-stu-id="18ec5-198">Location of Files Generated by the Test Client</span></span>

<span data-ttu-id="18ec5-199">根據預設, WCF 測試用戶端會將產生的用戶端程式代碼和設定檔儲存在 "%appdata%\Local\temp\Test Client Projects" 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="18ec5-199">By default, WCF Test Client stores generated client code and configuration files in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span> <span data-ttu-id="18ec5-200">在 WCF 測試用戶端結束之後, 會刪除這個資料夾。</span><span class="sxs-lookup"><span data-stu-id="18ec5-200">This folder is deleted after WCF Test Client exits.</span></span> <span data-ttu-id="18ec5-201">如果在 WCF 測試用戶端中修改設定檔, 而且停用 [**啟動服務時永遠重新**產生設定] 選項, 則會將修改過的檔案複製到 "My Documents\Test Client Projects" 下具有對應的 "CachedConfig" 資料夾中 (中繼資料-位址到檔案名稱) XML 檔案做為索引。</span><span class="sxs-lookup"><span data-stu-id="18ec5-201">If a configuration file is modified in WCF Test Client and the **Always Regenerate Config When Launching Services** option is disabled, the modified file is copied to the "CachedConfig" folder under "My Documents\Test Client Projects" with a mapping (metadata-address-to-file-name) XML file as an index.</span></span>

<span data-ttu-id="18ec5-202">您也可以在命令列中啟動 WCF 測試用戶端, 使用`/ProjectPath`參數指定新的所需路徑來儲存產生的檔案, 或`/RestoreProjectPath`使用參數來還原預設位置。</span><span class="sxs-lookup"><span data-stu-id="18ec5-202">You can also start WCF Test Client in a command line, use the `/ProjectPath` switch to specify a new desired path for storing generated files, or use the `/RestoreProjectPath` switch to restore the default location.</span></span> <span data-ttu-id="18ec5-203">語法如下：</span><span class="sxs-lookup"><span data-stu-id="18ec5-203">The syntax is as follows:</span></span>

`wcfTestClient.exe /ProjectPath [desired location]`

<span data-ttu-id="18ec5-204">執行此命令並不會開啟 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="18ec5-204">Running this command does not open WCF Test Client.</span></span> <span data-ttu-id="18ec5-205">只是會變更資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="18ec5-205">Only the folder location is changed.</span></span> <span data-ttu-id="18ec5-206">您可以執行此命令, 確定 WCF 測試用戶端是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="18ec5-206">You can run this command whether WCF Test Client is running or not.</span></span> <span data-ttu-id="18ec5-207">重新開機 WCF 測試用戶端時, 會套用新的位置。</span><span class="sxs-lookup"><span data-stu-id="18ec5-207">The new location is applied when WCF Test Client is restarted.</span></span> <span data-ttu-id="18ec5-208">位置資訊可以儲存在登錄中, 或在 [%appdata%\Local\temp\Test 用戶端專案] 資料夾的 WcfTestClient 檔案中。</span><span class="sxs-lookup"><span data-stu-id="18ec5-208">The location information can be saved in registry, or in the WcfTestClient.exe.option file in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span>

## <a name="features-supported-by-wcf-test-client"></a><span data-ttu-id="18ec5-209">WCF 測試用戶端支援的功能</span><span class="sxs-lookup"><span data-stu-id="18ec5-209">Features supported by WCF Test Client</span></span>

<span data-ttu-id="18ec5-210">以下是 WCF 測試用戶端支援的功能清單:</span><span class="sxs-lookup"><span data-stu-id="18ec5-210">The following is a list of features supported by WCF Test Client:</span></span>

- <span data-ttu-id="18ec5-211">服務引動過程：要求/回覆和單向訊息。</span><span class="sxs-lookup"><span data-stu-id="18ec5-211">Service Invocation: Request/Response and One-way message.</span></span>

- <span data-ttu-id="18ec5-212">繫結：Svcutil.exe 支援的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="18ec5-212">Bindings: all bindings supported by Svcutil.exe.</span></span>

- <span data-ttu-id="18ec5-213">控制工作階段。</span><span class="sxs-lookup"><span data-stu-id="18ec5-213">Controlling Session.</span></span>

- <span data-ttu-id="18ec5-214">訊息合約。</span><span class="sxs-lookup"><span data-stu-id="18ec5-214">Message Contract.</span></span>

- <span data-ttu-id="18ec5-215">XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="18ec5-215">XML serialization.</span></span>

<span data-ttu-id="18ec5-216">以下是 WCF 測試用戶端不支援的功能清單:</span><span class="sxs-lookup"><span data-stu-id="18ec5-216">The following is a list of features not supported by WCF Test Client:</span></span>

- <span data-ttu-id="18ec5-217">型別：<xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別，包括相關 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性、<xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 型別，以及 ADO.NET <xref:System.Data.DataTable> 型別。</span><span class="sxs-lookup"><span data-stu-id="18ec5-217">Types: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface, including the related <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute, and the <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> types and the ADO.NET <xref:System.Data.DataTable> type.</span></span>

- <span data-ttu-id="18ec5-218">雙工合約。</span><span class="sxs-lookup"><span data-stu-id="18ec5-218">Duplex contract.</span></span>

- <span data-ttu-id="18ec5-219">異動。</span><span class="sxs-lookup"><span data-stu-id="18ec5-219">Transaction.</span></span>

- <span data-ttu-id="18ec5-220">安全性：CardSpace、憑證和使用者名稱/密碼。</span><span class="sxs-lookup"><span data-stu-id="18ec5-220">Security: CardSpace , Certificate, and Username/Password.</span></span>

- <span data-ttu-id="18ec5-221">繫結：WSFederationbinding、任何內容系結和 Https 系結、WebHttpbinding (Json 回應訊息支援)。</span><span class="sxs-lookup"><span data-stu-id="18ec5-221">Bindings: WSFederationbinding, any Context bindings and Https binding, WebHttpbinding (Json response message support).</span></span>

## <a name="closing-wcf-test-client"></a><span data-ttu-id="18ec5-222">關閉 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="18ec5-222">Closing WCF Test Client</span></span>

<span data-ttu-id="18ec5-223">您可以透過下列方式關閉 WCF 測試用戶端:</span><span class="sxs-lookup"><span data-stu-id="18ec5-223">You can close WCF Test Client in the following ways:</span></span>

- <span data-ttu-id="18ec5-224">在 **[檔案]** 功能表上按一下 **[結束]** 。</span><span class="sxs-lookup"><span data-stu-id="18ec5-224">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="18ec5-225">或者, 在 [WCF 測試用戶端] 主視窗中, 按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="18ec5-225">Alternatively, in the WCF Test Client main window, click **Close**.</span></span> <span data-ttu-id="18ec5-226">這兩個動作也會關閉 WCF 服務自動裝載, 並在 Visual Studio 啟動 WCF 測試用戶端時, 停止 Visual Studio 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="18ec5-226">Both of these actions also shut down WCF Service Auto Host and stop the Visual Studio debugging process if WCF Test Client was launched by Visual Studio.</span></span>

- <span data-ttu-id="18ec5-227">以滑鼠右鍵按一下通知區域中的 [ **WCF 服務主機**] 圖示, 然後按一下 [結束] **。**</span><span class="sxs-lookup"><span data-stu-id="18ec5-227">Right-click the **WCF Service Host** icon in the notification area, and then click **Exit.**</span></span> <span data-ttu-id="18ec5-228">這會關閉 WCF 服務自動裝載和 WCF 測試用戶端, 並停止 Visual Studio 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="18ec5-228">This shuts down both WCF Service Auto Host and WCF Test Client and stops the Visual Studio debugging process.</span></span>

## <a name="see-also"></a><span data-ttu-id="18ec5-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18ec5-229">See also</span></span>

- [<span data-ttu-id="18ec5-230">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="18ec5-230">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
