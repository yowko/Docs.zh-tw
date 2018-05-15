---
title: WCF 測試用戶端 (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 78be40268b46c4c85ee034db67d67ee0fbf2158f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-test-client-wcftestclientexe"></a><span data-ttu-id="4c075-102">WCF 測試用戶端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="4c075-102">WCF Test Client (WcfTestClient.exe)</span></span>
<span data-ttu-id="4c075-103">Windows Communication Foundation (WCF) 測試用戶端 (WcfTestClient.exe) 是一種 GUI 工具，可讓使用者輸入測試參數，請送出該輸入至服務，並檢視服務傳回的回應。</span><span class="sxs-lookup"><span data-stu-id="4c075-103">Windows Communication Foundation (WCF) Test Client (WcfTestClient.exe) is a GUI tool that enables users to input test parameters, submit that input to the service, and view the response that the service sends back.</span></span> <span data-ttu-id="4c075-104">它提供了完善的服務測試經驗結合 WCF 服務主機時。</span><span class="sxs-lookup"><span data-stu-id="4c075-104">It provides a seamless service testing experience when combined with WCF Service Host.</span></span>  
  
 <span data-ttu-id="4c075-105">您通常可以找到 WCF 測試用戶端 (WcfTestClient.exe) 中的下列位置： C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE-社群可能是"Enterprise"、"專業 」 或 「 社群 」 取決於其中之一已安裝的 Visual Studio 層級。</span><span class="sxs-lookup"><span data-stu-id="4c075-105">You can typically find the WCF Test Client (WcfTestClient.exe) in the following location: C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE - Community may be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed.</span></span>
  
## <a name="scenarios-for-using-test-client"></a><span data-ttu-id="4c075-106">使用測試用戶端的案例</span><span class="sxs-lookup"><span data-stu-id="4c075-106">Scenarios for Using Test Client</span></span>  
 <span data-ttu-id="4c075-107">下列章節會討論最常見的案例，讓您可以使用 WCF 測試用戶端簡化開發程序。</span><span class="sxs-lookup"><span data-stu-id="4c075-107">The following sections discuss the most common scenarios in which you can use WCF Test Client to streamline your development process.</span></span>  
  
### <a name="inside-visual-studio"></a><span data-ttu-id="4c075-108">在 Visual Studio 內部</span><span class="sxs-lookup"><span data-stu-id="4c075-108">Inside Visual Studio</span></span>  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a><span data-ttu-id="4c075-109">WCF 服務主機啟動具有單一服務的 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="4c075-109">WCF Service Host Starts WCF Test Client with a Single Service</span></span>  
 <span data-ttu-id="4c075-110">建立新的 WCF 服務專案後，當您按 f5 鍵啟動偵錯工具時，WCF 服務主機會開始裝載您的專案中的服務。</span><span class="sxs-lookup"><span data-stu-id="4c075-110">After you create a new WCF service project and press F5 to start the debugger, the WCF Service Host begins to host the service in your project.</span></span> <span data-ttu-id="4c075-111">然後，WCF 測試用戶端開啟，並顯示組態檔中定義的服務端點的清單。</span><span class="sxs-lookup"><span data-stu-id="4c075-111">Then, WCF Test Client opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="4c075-112">您可以測試參數並叫用服務，然後重複這個程序以持續測試及驗證服務。</span><span class="sxs-lookup"><span data-stu-id="4c075-112">You can test the parameters and invoke the service, and repeat this process to continuously test and validate your service.</span></span>  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a><span data-ttu-id="4c075-113">WCF 服務主機啟動具有多個服務的 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="4c075-113">WCF Service Host Starts WCF Test Client with Multiple Services</span></span>  
 <span data-ttu-id="4c075-114">您也可以使用 WCF 測試用戶端協助偵錯包含多個服務的服務專案。</span><span class="sxs-lookup"><span data-stu-id="4c075-114">You can also use WCF Test Client to help debug a service project that contains multiple services.</span></span> <span data-ttu-id="4c075-115">WCF 測試用戶端開啟時，它會自動反覆運算的專案中的服務清單，並開啟這些測試。</span><span class="sxs-lookup"><span data-stu-id="4c075-115">When WCF Test Client opens, it automatically iterates the list of services in your project and opens them for testing.</span></span>  
  
### <a name="outside-visual-studio"></a><span data-ttu-id="4c075-116">在 Visual Studio 外部</span><span class="sxs-lookup"><span data-stu-id="4c075-116">Outside Visual Studio</span></span>  
 <span data-ttu-id="4c075-117">您也可以使用以測試網際網路上的任意服務的 Visual Studio 外部叫用 WCF 測試用戶端 (WcfTestClient.exe)。</span><span class="sxs-lookup"><span data-stu-id="4c075-117">You can also invoke the WCF Test Client (WcfTestClient.exe) outside Visual Studio to test an arbitrary service on the Internet.</span></span> <span data-ttu-id="4c075-118">若要找出該工具，請移至下列位置：</span><span class="sxs-lookup"><span data-stu-id="4c075-118">To locate the tool, go to the following location:</span></span>  
  
 <span data-ttu-id="4c075-119">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\\</span><span class="sxs-lookup"><span data-stu-id="4c075-119">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\\</span></span>  
  
 <span data-ttu-id="4c075-120">若要使用該工具，按兩下檔名即可從這個位置開啟，或者是從命令列進行啟動。</span><span class="sxs-lookup"><span data-stu-id="4c075-120">To use the tool, double-click the file name to open it from this location, or launch it from a command line.</span></span>  
  
 <span data-ttu-id="4c075-121">WCF 測試用戶端可以採用任意數目的 Uri 做為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="4c075-121">WCF Test Client takes an arbitrary number of URIs as command line arguments.</span></span>  <span data-ttu-id="4c075-122">這些引數是可以測試的服務 URI。</span><span class="sxs-lookup"><span data-stu-id="4c075-122">These are the URIs of services that can be tested.</span></span>  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 <span data-ttu-id="4c075-123">WCF 測試用戶端視窗開啟後，按一下**檔案**->**加入服務**，並輸入您想要開啟的服務的端點位址。</span><span class="sxs-lookup"><span data-stu-id="4c075-123">After the WCF Test Client window is opened, click **File**->**Add Service**, and enter the endpoint address of the service you want to open.</span></span>  
  
## <a name="wcf-test-client-user-interface"></a><span data-ttu-id="4c075-124">WCF 測試用戶端使用者介面</span><span class="sxs-lookup"><span data-stu-id="4c075-124">WCF Test Client User Interface</span></span>  
 <span data-ttu-id="4c075-125">您可以使用 WCF 測試用戶端使用單一的服務或多個服務。</span><span class="sxs-lookup"><span data-stu-id="4c075-125">You can use WCF Test Client with a single service or multiple services.</span></span>  
  
### <a name="service-operations"></a><span data-ttu-id="4c075-126">服務作業</span><span class="sxs-lookup"><span data-stu-id="4c075-126">Service Operations</span></span>  
 <span data-ttu-id="4c075-127">WCF 測試用戶端主視窗的左的窗格會列出所有可用的服務，以及它們各自的端點和作業。</span><span class="sxs-lookup"><span data-stu-id="4c075-127">The left pane of the WCF Test Client main window lists all the available services, along with their respective endpoints and operations.</span></span>  
  
 <span data-ttu-id="4c075-128">按兩下某項作業時，您可以在右窗格中具有該作業名稱的新索引標籤內，檢視其內容。</span><span class="sxs-lookup"><span data-stu-id="4c075-128">When you double-click an operation, you can view its content in the right pane inside a new tab with the operation's name.</span></span>  
  
 <span data-ttu-id="4c075-129">左窗格還會列出用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="4c075-129">The left pane also lists client configuration files.</span></span> <span data-ttu-id="4c075-130">按兩下任何項目，即可在右窗格中新出現的索引視窗上看見檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="4c075-130">Double-click any of the items to display the content of the file in a new tabbed window in the right pane.</span></span>  
  
### <a name="entering-test-parameters"></a><span data-ttu-id="4c075-131">輸入測試參數</span><span class="sxs-lookup"><span data-stu-id="4c075-131">Entering Test Parameters</span></span>  
 <span data-ttu-id="4c075-132">若要檢視測試參數，請按兩下作業，在右窗格中開啟它。</span><span class="sxs-lookup"><span data-stu-id="4c075-132">To view the test parameters, double-click an operation to open it in the right pane.</span></span> <span data-ttu-id="4c075-133">參數會顯示在**格式化**依預設，檢視，而且您可以輸入任意測試服務的參數值。</span><span class="sxs-lookup"><span data-stu-id="4c075-133">The parameters are showed in **Formatted** view by default, and you can enter arbitrary values for the parameters to test the service.</span></span>  
  
 <span data-ttu-id="4c075-134">若要檢視訊息的 XML，請按一下**XML**。</span><span class="sxs-lookup"><span data-stu-id="4c075-134">To view the message's XML, click **XML**.</span></span> <span data-ttu-id="4c075-135">若要將它們傳送至服務，按一下**Invoke**。</span><span class="sxs-lookup"><span data-stu-id="4c075-135">To send them to the service, click **Invoke**.</span></span>  
  
 <span data-ttu-id="4c075-136">資料集參數，按一下  **...**</span><span class="sxs-lookup"><span data-stu-id="4c075-136">For a DataSet parameter, click the **…**</span></span> <span data-ttu-id="4c075-137">下一步按鈕**編輯...**</span><span class="sxs-lookup"><span data-stu-id="4c075-137">button next to **Edit…**</span></span> <span data-ttu-id="4c075-138">若要在新視窗顯示 DataGrid 中進行編輯。</span><span class="sxs-lookup"><span data-stu-id="4c075-138">to edit it in a new window showing the DataGrid.</span></span> <span data-ttu-id="4c075-139">請注意，出現**複製資料集**和**貼上資料集**按鈕。</span><span class="sxs-lookup"><span data-stu-id="4c075-139">Notice the appearance of the **Copy DataSet** and **Paste DataSet** buttons.</span></span> <span data-ttu-id="4c075-140">如果在第一次編輯時 DataSet 物件的結構描述為未知，DataGrid 為空白。</span><span class="sxs-lookup"><span data-stu-id="4c075-140">If the schema of the DataSet object is unknown upon the first edit, the DataGrid is empty.</span></span> <span data-ttu-id="4c075-141">您必須將具有相同結構描述的 DataSet 物件貼入 DataGrid 中的目前物件 </span><span class="sxs-lookup"><span data-stu-id="4c075-141">You have to paste a DataSet object with the same schema into the current object in the DataGrid.</span></span> <span data-ttu-id="4c075-142">(請注意，您必須在貼上作業前從其他地方複製結構描述)。您也可以按一下 [複製 Dataset 物件供未來使用**複製資料集**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4c075-142">(Notice that you need to copy the schema from somewhere else before the paste operation.) You can also copy a Dataset object for future usage by clicking the **Copy DataSet** button.</span></span>  
  
 <span data-ttu-id="4c075-143">服務的回應會出現在測試參數下方。</span><span class="sxs-lookup"><span data-stu-id="4c075-143">The service's response appears below the test parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c075-144">如果預期的傳回值是字串，則結果會顯示為引號括住的字串，即使提供的輸入並未以引號括住。</span><span class="sxs-lookup"><span data-stu-id="4c075-144">If the expected return value is a string, the result will be displayed as a quoted string even though the input provided was not in quotes.</span></span>  
  
 <span data-ttu-id="4c075-145">如果您在建立服務合約時將特定作業指定為單向，就不會顯示任何服務回應。</span><span class="sxs-lookup"><span data-stu-id="4c075-145">If you specified a particular operation as one-way when you created the contract for the service, no service response is displayed.</span></span> <span data-ttu-id="4c075-146">訊息一旦排入佇列中準備傳遞，快顯對話方塊就會出現，通知您已成功傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="4c075-146">As soon as the message is queued for delivery, a dialog box pops up to notify you that the message was successfully sent.</span></span>  
  
### <a name="session-support"></a><span data-ttu-id="4c075-147">工作階段支援</span><span class="sxs-lookup"><span data-stu-id="4c075-147">Session Support</span></span>  
 <span data-ttu-id="4c075-148">**啟動新 proxy**服務作業的索引標籤中的核取方塊可讓您切換工作階段支援。</span><span class="sxs-lookup"><span data-stu-id="4c075-148">The **Start a new proxy** check box in a service operation's tab enables you to toggle session support.</span></span> <span data-ttu-id="4c075-149">這個方塊預設為清除。</span><span class="sxs-lookup"><span data-stu-id="4c075-149">This box is cleared by default.</span></span>  
  
 <span data-ttu-id="4c075-150">當您輸入的特定作業 （或另一個作業中相同的服務端點） 的測試參數，並按一下**Invoke**多次清除該核取方塊，這些作業會共用一個 proxy，而服務狀態為保留跨多個作業。</span><span class="sxs-lookup"><span data-stu-id="4c075-150">When you enter test parameters for a specific operation (or another operation in the same service endpoint) and click **Invoke** multiple times with the check box cleared, these operations share one proxy and the service status is persisted across multiple operations.</span></span>  
  
 <span data-ttu-id="4c075-151">如果**啟動新 proxy**核取方塊已核取，新的 proxy 啟動每個**Invoke**早的工作階段就會結束，且會重設服務狀態。</span><span class="sxs-lookup"><span data-stu-id="4c075-151">If the **Start a new proxy** check box is checked, a new proxy is started for each **Invoke**, the previous session scenario is ended, and the service status is reset.</span></span>  
  
### <a name="editing-client-configuration"></a><span data-ttu-id="4c075-152">編輯用戶端組態</span><span class="sxs-lookup"><span data-stu-id="4c075-152">Editing Client Configuration</span></span>  
 <span data-ttu-id="4c075-153">WCF 測試用戶端主視窗的左的窗格會列出用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="4c075-153">The left pane of the WCF Test Client main window lists client configuration files.</span></span> <span data-ttu-id="4c075-154">按兩下任何項目，即可在右窗格中顯示檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="4c075-154">Double-click any of the items to display the contents of the file in the right pane.</span></span>  
  
#### <a name="edit-with-service-configuration-editor"></a><span data-ttu-id="4c075-155">使用服務組態編輯器進行編輯</span><span class="sxs-lookup"><span data-stu-id="4c075-155">Edit with Service Configuration Editor</span></span>  
 <span data-ttu-id="4c075-156">以滑鼠右鍵按一下**組態檔**在左的窗格中選取內容功能表**使用 SvcConfigEditor 編輯**。</span><span class="sxs-lookup"><span data-stu-id="4c075-156">Right-click **Config File** in the left pane and select the context menu **Edit with SvcConfigEditor**.</span></span> <span data-ttu-id="4c075-157">服務組態編輯器隨即啟動，並顯示用戶端組態內容。</span><span class="sxs-lookup"><span data-stu-id="4c075-157">Service Configuration Editor is launched with the client configuration content.</span></span> <span data-ttu-id="4c075-158">您可以在該工具內編輯組態並進行儲存。</span><span class="sxs-lookup"><span data-stu-id="4c075-158">You can edit the configuration and save it within the tool.</span></span>  
  
 <span data-ttu-id="4c075-159">之後將檔案儲存在服務組態編輯器，WCF 測試用戶端會顯示警告訊息，通知您檔案已在外部經過修改，並詢問您是否要重新載入。</span><span class="sxs-lookup"><span data-stu-id="4c075-159">After saving the file in Service Configuration Editor, WCF Test Client displays a warning message to inform you that the file has been modified outside and asks whether you would like to reload it.</span></span>  
  
 <span data-ttu-id="4c075-160">如果您選取**是**，[Client.dll.config] 索引標籤中的組態內容會反映您在編輯器中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="4c075-160">If you select **Yes**, the configuration content in the "Client.dll.config" tab reflects the changes you made in the editor.</span></span>  
  
 <span data-ttu-id="4c075-161">如果您選取**否**，[Client.dll.config] 索引標籤中的組態內容會維持不變，和原始程式檔都會自動儲存修改過的內容。</span><span class="sxs-lookup"><span data-stu-id="4c075-161">If you select **No**, the configuration content in the "Client.dll.config" tab remains unchanged and the modified content is automatically saved to the source file.</span></span>  
  
#### <a name="restore-to-default-configuration"></a><span data-ttu-id="4c075-162">還原至預設組態</span><span class="sxs-lookup"><span data-stu-id="4c075-162">Restore to Default Configuration</span></span>  
 <span data-ttu-id="4c075-163">如果您想要取消所有變更並還原為預設用戶端設定，以滑鼠右鍵按一下**組態檔**在左的窗格中選取內容功能表**還原至預設組態**。載入預設組態值，並還原 Client.dll.config 索引標籤中的內容。</span><span class="sxs-lookup"><span data-stu-id="4c075-163">If you want to cancel all the changes and restore to the default client configuration, right-click **Config File** in the left pane and select the context menu **Restore to Default Config**. The default configuration value is loaded and content in "Client.dll.config" tab is restored.</span></span>  
  
#### <a name="validate-changes"></a><span data-ttu-id="4c075-164">驗證變更</span><span class="sxs-lookup"><span data-stu-id="4c075-164">Validate Changes</span></span>  
 <span data-ttu-id="4c075-165">當在 WCF 測試用戶端正在載入儲存的變更時，組態會檢查針對 WCF 結構描述的有效性。</span><span class="sxs-lookup"><span data-stu-id="4c075-165">When saved changes are being loaded in WCF Test Client, the configuration is checked for validity against WCF schema.</span></span> <span data-ttu-id="4c075-166">如果發現錯誤，會顯示對話方塊說明錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4c075-166">If errors are found, a dialog box is displayed to show error details.</span></span>  
  
 <span data-ttu-id="4c075-167">在 proxy 產生、 二進位編譯或服務叫用，已停用支援編輯 （亦即，[編輯]、 [還原]，等等） 的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="4c075-167">During proxy generation, binary compiling, or service invoking, menu items that support editing (that is, "Edit …", "Restore …", and so on) are disabled.</span></span> <span data-ttu-id="4c075-168">載入 WCF 測試用戶端更新組態時，也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="4c075-168">Service invocation is also disabled when loading updated configuration to WCF Test Client.</span></span>  
  
#### <a name="persist-client-configuration"></a><span data-ttu-id="4c075-169">保存用戶端組態</span><span class="sxs-lookup"><span data-stu-id="4c075-169">Persist Client Configuration</span></span>  
 <span data-ttu-id="4c075-170">**工具**->**選項**->**用戶端設定** 索引標籤包含**永遠重新產生組態時啟動服務**選項，預設會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="4c075-170">The **Tools**->**Options**->**Client Configuration** tab contains an **Always Regenerate Config When Launching Services** option, which is enabled by default.</span></span> <span data-ttu-id="4c075-171">這個選項會指定，每次 WCF 測試用戶端載入服務時，它會重新產生組態檔的最新的服務合約和服務 App.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4c075-171">This option specifies that every time WCF Test Client loads a service, it regenerates a configuration file based on the latest service contract and service App.config files.</span></span>  
  
 <span data-ttu-id="4c075-172">如果您編輯用戶端設定 WCF 服務，並想要一律使用這個更新的檔案進行偵錯您的服務，您可以取消核取**重新產生**選項。</span><span class="sxs-lookup"><span data-stu-id="4c075-172">If you have edited the client configuration for your WCF service and want to always use this updated file to debug your service, you can uncheck the **Regenerate** option.</span></span> <span data-ttu-id="4c075-173">如此一來，即使當您更新服務並重新開啟 WCF 測試用戶端，Client.dll.config 檔案是您先前更新而不是重新產生其中根據更新的服務。</span><span class="sxs-lookup"><span data-stu-id="4c075-173">By doing so, even when you update the service and reopen WCF Test Client, the Client.dll.config file is the one you updated previously instead of a regenerated one based on the updated service.</span></span>  
  
 <span data-ttu-id="4c075-174">但是，您可能需要編輯組態檔，讓其跟重新產生的 Proxy 一致。</span><span class="sxs-lookup"><span data-stu-id="4c075-174">However, you might need to edit the configuration file to make it consistent with the regenerated proxy.</span></span> <span data-ttu-id="4c075-175">如果重新產生的 Proxy 和組態檔因更新服務而不相符，則在叫用服務時將發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c075-175">If the regenerated proxy and configuration file are mismatched due to an updated service, errors will occur when the service is invoked.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="4c075-176">如果您修改過用戶端組態檔並選擇供往後重複使用，則可以在下列位置找到該檔案：</span><span class="sxs-lookup"><span data-stu-id="4c075-176">If you have modified the client configuration file and select to reuse it in the future, you can find the file in the following location:</span></span>  
>   
>  <span data-ttu-id="4c075-177">\Documents and 設定\\[使用者帳戶] \My Documents\Test 用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="4c075-177">\Documents and Settings\\[User Account]\My Documents\Test Client Projects.</span></span>  
>   
>  <span data-ttu-id="4c075-178">任何儲存在用戶端組態檔中經過更新的認證資訊，皆受到這個資料夾的存取控制清單 (ACL) 所保護。</span><span class="sxs-lookup"><span data-stu-id="4c075-178">Any updated credential information stored to the client configuration file is protected by the Access Control List (ACL) of this folder.</span></span>  
  
### <a name="adding-removing-and-refreshing-services"></a><span data-ttu-id="4c075-179">新增、移除和重新整理服務</span><span class="sxs-lookup"><span data-stu-id="4c075-179">Adding, Removing and Refreshing Services</span></span>  
  
#### <a name="add-service"></a><span data-ttu-id="4c075-180">新增服務</span><span class="sxs-lookup"><span data-stu-id="4c075-180">Add Service</span></span>  
 <span data-ttu-id="4c075-181">按一下**檔案**->**加入服務**將服務加入至 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="4c075-181">Click **File**->**Add Service** to add a service to WCF Test Client.</span></span> <span data-ttu-id="4c075-182">接著會要求您輸入要新增之服務的 URI (端點位址)。</span><span class="sxs-lookup"><span data-stu-id="4c075-182">You are then required to type the URI (endpoint address) of the service to be added.</span></span> <span data-ttu-id="4c075-183">服務位址可以是 Mex 位址或 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="4c075-183">The service’s address can be a mex address or WSDL address.</span></span>  
  
 <span data-ttu-id="4c075-184">您也可以尋找清單中的 10 個最近新增的服務端點的**最近使用的服務**子功能表。</span><span class="sxs-lookup"><span data-stu-id="4c075-184">You can also find a list of 10 recently added services' endpoints in the **Recent Services** submenu.</span></span> <span data-ttu-id="4c075-185">如果您選取其中一個，指定的服務便會加入 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="4c075-185">If you select one of them, the specified service is added to WCF Test Client.</span></span>  
  
 <span data-ttu-id="4c075-186">您也可以以滑鼠右鍵按一下服務樹狀目錄的根目錄**我的服務專案**，然後選取**加入服務**以達成相同結果。</span><span class="sxs-lookup"><span data-stu-id="4c075-186">You can also right-click the root of service tree **My Service Projects**, and select **Add Service** to achieve the same result.</span></span>  
  
 <span data-ttu-id="4c075-187">在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援新增服務的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="4c075-187">During proxy generation, binary compiling, or service invocation, menu items that support adding a service are disabled.</span></span> <span data-ttu-id="4c075-188">同時也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="4c075-188">Service invocation is also disabled.</span></span>  
  
#### <a name="remove-service"></a><span data-ttu-id="4c075-189">移除服務</span><span class="sxs-lookup"><span data-stu-id="4c075-189">Remove Service</span></span>  
 <span data-ttu-id="4c075-190">以滑鼠右鍵按一下要移除，然後選取服務的服務根目錄**移除服務**從 WCF 測試用戶端移除服務。</span><span class="sxs-lookup"><span data-stu-id="4c075-190">Right-click the service root of the service to be removed, and select **Remove Service** to remove a service from WCF Test Client.</span></span>  
  
 <span data-ttu-id="4c075-191">在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援移除服務的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="4c075-191">During proxy generation, binary compiling, or service invocation, menu items that support removing a service are disabled.</span></span> <span data-ttu-id="4c075-192">同時也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="4c075-192">Service invocation is also disabled.</span></span>  
  
#### <a name="refresh-service"></a><span data-ttu-id="4c075-193">重新整理服務</span><span class="sxs-lookup"><span data-stu-id="4c075-193">Refresh Service</span></span>  
 <span data-ttu-id="4c075-194">如果服務進行變更，而 WCF 測試用戶端正在執行，而且您想要確保是最新的 WCF 測試用戶端實作，該服務，以滑鼠右鍵按一下服務，然後選取的服務根目錄**重新整理服務**。</span><span class="sxs-lookup"><span data-stu-id="4c075-194">If a change is made to the service while WCF Test Client is running and you want to ensure that the WCF Test Client implementation for that service is up-to-date, right-click the service root of the service, and select **Refresh Service**.</span></span> <span data-ttu-id="4c075-195">請注意，重新整理後會重設服務狀態。</span><span class="sxs-lookup"><span data-stu-id="4c075-195">Note that after refreshing, the service status is reset.</span></span>  
  
 <span data-ttu-id="4c075-196">在 Proxy 產生、二進位編譯或服務叫用期間，會停用支援重新整理服務的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="4c075-196">During proxy generation, binary compiling, or service invocation, menu items that support refreshing a service are disabled.</span></span> <span data-ttu-id="4c075-197">同時也會停用服務叫用。</span><span class="sxs-lookup"><span data-stu-id="4c075-197">Service invocation is also disabled.</span></span>  
  
## <a name="location-of-files-generated-by-the-test-client"></a><span data-ttu-id="4c075-198">測試用戶端產生的檔案位置</span><span class="sxs-lookup"><span data-stu-id="4c075-198">Location of Files Generated by the Test Client</span></span>  
 <span data-ttu-id="4c075-199">根據預設，WCF 測試用戶端會將產生的用戶端程式碼和組態檔在"%appdata%\Local\temp\Test Client Projects"資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4c075-199">By default, WCF Test Client stores generated client code and configuration files in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span> <span data-ttu-id="4c075-200">WCF 測試用戶端結束後，會刪除此資料夾。</span><span class="sxs-lookup"><span data-stu-id="4c075-200">This folder is deleted after WCF Test Client exits.</span></span> <span data-ttu-id="4c075-201">如果在 WCF 測試用戶端修改設定檔和**重新產生組態啟動服務時永遠**選項已停用，已修改的檔案會複製到"My Documents\Test Client Projects 下的"Cached Config"資料夾Documents\Test Client Projects"並做為索引的對應 （中繼資料-位址-到-檔名） XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4c075-201">If a configuration file is modified in WCF Test Client and the **Always Regenerate Config When Launching Services** option is disabled, the modified file is copied to the "Cached Config" folder under "My Documents\Test Client Projects Documents\Test Client Projects" with a mapping (metadata-address-to-file-name) XML file as an index.</span></span>  
  
 <span data-ttu-id="4c075-202">您也可以在 命令列使用啟動 WCF 測試用戶端`/ProjectPath`參數指定新的目標的路徑，用於儲存產生的檔案，或是使用`/RestoreProjectPath`參數還原預設位置。</span><span class="sxs-lookup"><span data-stu-id="4c075-202">You can also start WCF Test Client in a command line, use the `/ProjectPath` switch to specify a new desired path for storing generated files, or use the `/RestoreProjectPath` switch to restore the default location.</span></span> <span data-ttu-id="4c075-203">語法如下：</span><span class="sxs-lookup"><span data-stu-id="4c075-203">The syntax is as follows:</span></span>  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 <span data-ttu-id="4c075-204">執行此命令不會開啟 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="4c075-204">Running this command does not open WCF Test Client.</span></span> <span data-ttu-id="4c075-205">只是會變更資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="4c075-205">Only the folder location is changed.</span></span> <span data-ttu-id="4c075-206">您可以執行此命令是否正在執行 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="4c075-206">You can run this command whether WCF Test Client is running or not.</span></span> <span data-ttu-id="4c075-207">重新啟動 WCF 測試用戶端時，會套用新的位置。</span><span class="sxs-lookup"><span data-stu-id="4c075-207">The new location is applied when WCF Test Client is restarted.</span></span> <span data-ttu-id="4c075-208">在登錄中，或在"%appdata%\Local\temp\Test Client Projects"資料夾中的 wcftestclient.exe.option 檔案中，可以儲存的位置資訊。</span><span class="sxs-lookup"><span data-stu-id="4c075-208">The location information can be saved in registry, or in the WcfTestClient.exe.option file in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span>  
  
## <a name="features-supported-by-wcf-test-client"></a><span data-ttu-id="4c075-209">WCF 測試用戶端支援的功能</span><span class="sxs-lookup"><span data-stu-id="4c075-209">Features supported by WCF Test Client</span></span>  
 <span data-ttu-id="4c075-210">下列是 WCF 測試用戶端支援的功能清單：</span><span class="sxs-lookup"><span data-stu-id="4c075-210">The following is a list of features supported by WCF Test Client:</span></span>  
  
-   <span data-ttu-id="4c075-211">服務叫用：要求/回應和單向訊息。</span><span class="sxs-lookup"><span data-stu-id="4c075-211">Service Invocation: Request/Response and One-way message.</span></span>  
  
-   <span data-ttu-id="4c075-212">繫結：Svcutil.exe 支援的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="4c075-212">Bindings: all bindings supported by Svcutil.exe.</span></span>  
  
-   <span data-ttu-id="4c075-213">控制工作階段。</span><span class="sxs-lookup"><span data-stu-id="4c075-213">Controlling Session.</span></span>  
  
-   <span data-ttu-id="4c075-214">訊息合約。</span><span class="sxs-lookup"><span data-stu-id="4c075-214">Message Contract.</span></span>  
  
-   <span data-ttu-id="4c075-215">XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="4c075-215">XML serialization.</span></span>  
  
 <span data-ttu-id="4c075-216">下列是 WCF 測試用戶端不支援的功能清單：</span><span class="sxs-lookup"><span data-stu-id="4c075-216">The following is a list of features not supported by WCF Test Client:</span></span>  
  
-   <span data-ttu-id="4c075-217">型別：<xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別，包括相關 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性、<xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 型別，以及 ADO.NET <xref:System.Data.DataTable> 型別。</span><span class="sxs-lookup"><span data-stu-id="4c075-217">Types: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface, including the related <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute, and the <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> types and the ADO.NET <xref:System.Data.DataTable> type.</span></span>  
  
-   <span data-ttu-id="4c075-218">雙工合約。</span><span class="sxs-lookup"><span data-stu-id="4c075-218">Duplex contract.</span></span>  
  
-   <span data-ttu-id="4c075-219">交易。</span><span class="sxs-lookup"><span data-stu-id="4c075-219">Transaction.</span></span>  
  
-   <span data-ttu-id="4c075-220">安全性：[!INCLUDE[infocard](../../../includes/infocard-md.md)]、憑證和使用者名稱/密碼。</span><span class="sxs-lookup"><span data-stu-id="4c075-220">Security: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , Certificate, and Username/Password.</span></span>  
  
-   <span data-ttu-id="4c075-221">繫結：WSFederationbinding、任何 Context 繫結和 Https 繫結、WebHttpbinding (Json 回應訊息支援)。</span><span class="sxs-lookup"><span data-stu-id="4c075-221">Bindings: WSFederationbinding, any Context bindings and Https binding, WebHttpbinding (Json response message support).</span></span>  
  
## <a name="closing-wcf-test-client"></a><span data-ttu-id="4c075-222">關閉 WCF 測試用戶端</span><span class="sxs-lookup"><span data-stu-id="4c075-222">Closing WCF Test Client</span></span>  
 <span data-ttu-id="4c075-223">您可以下列方式來關閉 WCF 測試用戶端：</span><span class="sxs-lookup"><span data-stu-id="4c075-223">You can close WCF Test Client in the following ways:</span></span>  
  
-   <span data-ttu-id="4c075-224">在**檔案**功能表上，按一下 **結束**。</span><span class="sxs-lookup"><span data-stu-id="4c075-224">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="4c075-225">或者，在 WCF 測試用戶端主視窗中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="4c075-225">Alternatively, in the WCF Test Client main window, click **Close**.</span></span> <span data-ttu-id="4c075-226">這些動作也關閉 WCF 服務自動主機和停止 Visual Studio 偵錯程序，如果由 Visual Studio 啟動 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="4c075-226">Both of these actions also shut down WCF Service Auto Host and stop the Visual Studio debugging process if WCF Test Client was launched by Visual Studio.</span></span>  
  
-   <span data-ttu-id="4c075-227">以滑鼠右鍵按一下**WCF 服務主機**圖示在通知區域中，然後按一下**結束。**</span><span class="sxs-lookup"><span data-stu-id="4c075-227">Right-click the **WCF Service Host** icon in the notification area, and then click **Exit.**</span></span> <span data-ttu-id="4c075-228">這會關閉 WCF 服務自動主機和 WCF 測試用戶端，並停止 Visual Studio 偵錯處理序。</span><span class="sxs-lookup"><span data-stu-id="4c075-228">This shuts down both WCF Service Auto Host and WCF Test Client and stops the Visual Studio debugging process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c075-229">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c075-229">See Also</span></span>  
 [<span data-ttu-id="4c075-230">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="4c075-230">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
