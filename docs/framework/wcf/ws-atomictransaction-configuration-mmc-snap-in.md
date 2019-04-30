---
title: WS-AtomicTransaction 組態 MMC 嵌入式管理單元
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: b1d86fa57b31d1f9be12f76c28f9d042e7e28e24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052556"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a><span data-ttu-id="afb1b-102">WS-AtomicTransaction 組態 MMC 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="afb1b-102">WS-AtomicTransaction Configuration MMC Snap-in</span></span>
<span data-ttu-id="afb1b-103">WS-AtomicTransaction 組態 MMC 嵌入式管理單元用於設定本機電腦和遠端電腦上的部分 WS-AtomicTransaction 設定。</span><span class="sxs-lookup"><span data-stu-id="afb1b-103">The WS-AtomicTransaction Configuration MMC Snap-in is used to configure a portion of the WS-AtomicTransaction settings on both local and remote machines.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afb1b-104">備註</span><span class="sxs-lookup"><span data-stu-id="afb1b-104">Remarks</span></span>  
 <span data-ttu-id="afb1b-105">如果您正在[!INCLUDE[wxp](../../../includes/wxp-md.md)]或是[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]，MMC 嵌入式管理單元可瀏覽至**控制控制台/系統管理工具/元件服務 /**，以滑鼠右鍵按一下**我的電腦**，和選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="afb1b-105">If you are running [!INCLUDE[wxp](../../../includes/wxp-md.md)] or [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], the MMC snap-in can be found by navigating to **Control Panel/Administrative Tools/Component Services/**, right-clicking **My Computer**, and selecting **Properties**.</span></span> <span data-ttu-id="afb1b-106">這個位置與您設定 MSDTC 的位置相同。</span><span class="sxs-lookup"><span data-stu-id="afb1b-106">This is the same location where you can configure the MSDTC.</span></span> <span data-ttu-id="afb1b-107">組態的可用選項之下**WS-AT**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="afb1b-107">Options available for configuration are grouped under the **WS-AT** tab.</span></span>  
  
 <span data-ttu-id="afb1b-108">如果您執行 Windows Vista 或[!INCLUDE[lserver](../../../includes/lserver-md.md)]，MMC 嵌入式管理單元可依序按一下**開始**按鈕，並輸入`dcomcnfg.exe`中**搜尋** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="afb1b-108">If you are running Windows Vista or [!INCLUDE[lserver](../../../includes/lserver-md.md)], MMC snap-in can be found by clicking the **Start** button, and typing in `dcomcnfg.exe` in the **Search** box.</span></span> <span data-ttu-id="afb1b-109">當 MMC 開啟時，瀏覽至**我的電腦 \ 分散式交易協調器 \ 本機 DTC**節點、 以滑鼠右鍵按一下，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="afb1b-109">When the MMC is opened, navigate to the **My Computer\Distributed Transaction Coordinator\Local DTC** node, right click and select **Properties**.</span></span> <span data-ttu-id="afb1b-110">組態的可用選項之下**WS-AT**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="afb1b-110">Options available for configuration are grouped under the **WS-AT** tab.</span></span>  
  
 <span data-ttu-id="afb1b-111">上述的步驟用於啟動設定本機電腦的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="afb1b-111">The previous steps are used to launch the snap-in for configuring a local machine.</span></span> <span data-ttu-id="afb1b-112">如果您想要設定遠端電腦，您必須找出在遠端電腦的名稱**控制控制台/系統管理工具/元件服務 /**，並執行類似的步驟，如果您正在[!INCLUDE[wxp](../../../includes/wxp-md.md)]或[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="afb1b-112">If you want to configure a remote machine, you should locate the remote machine's name in **Control Panel/Administrative Tools/Component Services/**, and perform similar steps if you are running [!INCLUDE[wxp](../../../includes/wxp-md.md)] or [!INCLUDE[ws2003](../../../includes/ws2003-md.md)].</span></span> <span data-ttu-id="afb1b-113">如果您執行 Windows Vista 或[!INCLUDE[lserver](../../../includes/lserver-md.md)]，按照先前的步驟適用於 Vista 並[!INCLUDE[lserver](../../../includes/lserver-md.md)]，但使用**分散式交易協調器 \ 本機 DTC**遠端電腦的節點下的節點。</span><span class="sxs-lookup"><span data-stu-id="afb1b-113">If you are running Windows Vista or [!INCLUDE[lserver](../../../includes/lserver-md.md)], follow the previous steps for Vista and [!INCLUDE[lserver](../../../includes/lserver-md.md)], but use the **Distributed Transaction Coordinator\Local DTC** node under the remote computer's node.</span></span>  
  
 <span data-ttu-id="afb1b-114">若要使用此工具提供的使用者介面，您必須註冊 WsatUI.dll 檔，此檔位於以下路徑，</span><span class="sxs-lookup"><span data-stu-id="afb1b-114">To use the user interface provided by the tool, you have to register the WsatUI.dll file, which is located at the following path,</span></span>  
  
 <span data-ttu-id="afb1b-115">**%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**</span><span class="sxs-lookup"><span data-stu-id="afb1b-115">**%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**</span></span>  
  
 <span data-ttu-id="afb1b-116">下列命令可完成註冊。</span><span class="sxs-lookup"><span data-stu-id="afb1b-116">The registration can be done by the following command.</span></span>  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 <span data-ttu-id="afb1b-117">您可以使用這個工具修改基本 WS-AtomicTransaction 設定。</span><span class="sxs-lookup"><span data-stu-id="afb1b-117">You can use this tool to modify the basic WS-AtomicTransaction settings.</span></span> <span data-ttu-id="afb1b-118">例如，您可以啟用或停用 WS-AtomicTransaction 通訊協定支援、設定 WS-AT 的 HTTP 連接埠、將 SSL 憑證繫結至 HTTP 連接埠、透過指定憑證主體名稱來設定憑證、選取追蹤模式，以及設定預設逾時與最大逾時。</span><span class="sxs-lookup"><span data-stu-id="afb1b-118">For example, you can enable and disable the WS-AtomicTransaction protocol support, configure the HTTP ports for WS-AT, bind an SSL Certificate to the HTTP port, configure certificates by specifying certificate subject names, select the Tracing mode and set default and maximum timeouts.</span></span>  
  
 <span data-ttu-id="afb1b-119">如果您必須只在本機電腦上設定 WS-AtomicTransaction 支援，可使用這個工具的命令列版本。</span><span class="sxs-lookup"><span data-stu-id="afb1b-119">If you must configure WS-AtomicTransaction support on the local machine only, you can use the command line version of this tool.</span></span> <span data-ttu-id="afb1b-120">如需有關命令列工具的詳細資訊，請參閱 < [WS-AtomicTransaction 組態公用程式 (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)主題。</span><span class="sxs-lookup"><span data-stu-id="afb1b-120">For more information about the command line tool, see the [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) topic.</span></span>  
  
 <span data-ttu-id="afb1b-121">請注意，MMC 嵌入式管理單元和命令列工具都不支援設定所有 WS-AT 設定。</span><span class="sxs-lookup"><span data-stu-id="afb1b-121">You should be aware that both the MMC Snap-in and the command-line tool do not support configuring all WS-AT settings.</span></span> <span data-ttu-id="afb1b-122">這些設定只能透過直接修改登錄來編輯。</span><span class="sxs-lookup"><span data-stu-id="afb1b-122">These settings can be edited only by modifying the registry directly.</span></span> <span data-ttu-id="afb1b-123">如需有關這些登錄設定的詳細資訊，請參閱 <<c0> [ 設定 Ws-atomic 交易支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="afb1b-123">For more information about these registry settings, see [Configuring WS-Atomic Transaction Support](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
### <a name="user-interface-description"></a><span data-ttu-id="afb1b-124">使用者介面說明</span><span class="sxs-lookup"><span data-stu-id="afb1b-124">User Interface Description</span></span>  
 <span data-ttu-id="afb1b-125">**啟用 Ws-atomic 異動網路支援**:</span><span class="sxs-lookup"><span data-stu-id="afb1b-125">**Enable WS-Atomic Transaction Network Support**:</span></span>  
  
 <span data-ttu-id="afb1b-126">切換這個核取方塊可啟用或停用此嵌入式管理單元的所有 GUI 元件。</span><span class="sxs-lookup"><span data-stu-id="afb1b-126">Toggling this checkbox enables or disables all the GUI components of this snap-in.</span></span>  
  
 <span data-ttu-id="afb1b-127">在核取此方塊前，您應該先確認已啟用網路 DTC 存取和傳入或傳出通訊 (或兩者)。</span><span class="sxs-lookup"><span data-stu-id="afb1b-127">Before you check this box, you should make sure that Network DTC Access is enabled with inbound or outbound communication, or both.</span></span> <span data-ttu-id="afb1b-128">這個值可以在中進行驗證**安全性**MSDTC 嵌入式管理單元 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="afb1b-128">This value can be verified in the **Security** Tab of the MSDTC snap-in.</span></span>  
  
#### <a name="network-group-box"></a><span data-ttu-id="afb1b-129">網路群組方塊</span><span class="sxs-lookup"><span data-stu-id="afb1b-129">Network Group Box</span></span>  
 <span data-ttu-id="afb1b-130">您可以在 [網路] 群組中指定 HTTPS 連接埠和其他安全性設定，如 SSL 加密。</span><span class="sxs-lookup"><span data-stu-id="afb1b-130">You can specify the HTTPS port and additional security settings such as SSL encryption in the Network group.</span></span> <span data-ttu-id="afb1b-131">如果 [DTC 網路交易] 未啟用，則這個群組為停用 (呈現淡灰色)。</span><span class="sxs-lookup"><span data-stu-id="afb1b-131">This group is disabled (grayed out) if DTC Network Transactions are not enabled.</span></span>  
  
 <span data-ttu-id="afb1b-132">**HTTPS 連接埠**</span><span class="sxs-lookup"><span data-stu-id="afb1b-132">**HTTPS Port**</span></span>  
  
 <span data-ttu-id="afb1b-133">這是用於 WS-AT 之 HTTPS 連接埠的值。</span><span class="sxs-lookup"><span data-stu-id="afb1b-133">This is the value of the HTTPS port used for WS-AT.</span></span> <span data-ttu-id="afb1b-134">這個值必須在 1-65535 的範圍內 (用於表示有效連接埠)。</span><span class="sxs-lookup"><span data-stu-id="afb1b-134">The value must be a number in the range 1-65535 (as to represent a valid port).</span></span> <span data-ttu-id="afb1b-135">變更 HTTP 連接埠會修改 HTTP 服務組態，意指先前使用的 WS-AT Service Address 已釋放，並根據新的連接埠註冊新的 WS-AT Service Address。</span><span class="sxs-lookup"><span data-stu-id="afb1b-135">Changing the HTTP Port modifies the HTTP Service Configuration, which means that the previously used WS-AT Service Address is released, and a new WS-AT Service Address is registered based on the new port.</span></span> <span data-ttu-id="afb1b-136">此外，新選取的連接埠會使用目前選取的 SSL 加密憑證進行加密。</span><span class="sxs-lookup"><span data-stu-id="afb1b-136">In addition, the newly selected port is encrypted with the currently selected certificate for SSL Encryption.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afb1b-137">如果在執行此工具之前，您已啟用防火牆，則會自動在例外狀況清單中註冊該連接埠。</span><span class="sxs-lookup"><span data-stu-id="afb1b-137">If you have already enabled the firewall before running this tool, the port is automatically registered in the exception list.</span></span> <span data-ttu-id="afb1b-138">如果在執行此工具之前，您已停用防火牆，則不必為該防火牆進行任何額外的設定。</span><span class="sxs-lookup"><span data-stu-id="afb1b-138">If the firewall is disabled before running this tool, nothing additional is configured regarding the firewall.</span></span>  
  
 <span data-ttu-id="afb1b-139">如果您在設定 WS-AT 後啟用了防火牆，您必須再次執行這個工具，並使用這個參數提供連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="afb1b-139">If you enable the firewall after configuring WS-AT, you must run this tool again and supply the port number using this parameter.</span></span> <span data-ttu-id="afb1b-140">如果您在設定後停用防火牆，WS-AT 會繼續運作，而不必進行額外的輸入。</span><span class="sxs-lookup"><span data-stu-id="afb1b-140">If you disable the firewall after configuring, WS-AT continues to work without additional input.</span></span>  
  
 <span data-ttu-id="afb1b-141">**端點憑證**</span><span class="sxs-lookup"><span data-stu-id="afb1b-141">**Endpoint Certificate**</span></span>  
  
 <span data-ttu-id="afb1b-142">按一下 **選取**按鈕會顯示本機電腦，讓使用者能夠選取可以用於 SSL 加密的憑證上的目前可用憑證清單。</span><span class="sxs-lookup"><span data-stu-id="afb1b-142">Clicking the **Select** button displays a list with the currently available certificates on the Local Machine, allowing the user to select the certificate that can be used for SSL encryption.</span></span> <span data-ttu-id="afb1b-143">憑證必須包含私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="afb1b-143">The certificates must have a private key.</span></span> <span data-ttu-id="afb1b-144">否則，您會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="afb1b-144">Otherwise, you receive an error message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afb1b-145">為選取的連接埠設定 SSL 憑證時，如果與該連接埠關聯的原始 SSL 憑證存在的話，將會覆寫該憑證。</span><span class="sxs-lookup"><span data-stu-id="afb1b-145">When you set an SSL certificate for a selected port, you overwrite the original SSL certificate associated with that port if one exists.</span></span>  
  
 <span data-ttu-id="afb1b-146">**授權的帳戶**</span><span class="sxs-lookup"><span data-stu-id="afb1b-146">**Authorized Accounts**</span></span>  
  
 <span data-ttu-id="afb1b-147">按一下**選取 [** ] 按鈕會叫用的 Windows 存取控制清單編輯器中，其中您可以指定使用者或群組可以參與 Ws-atomic 異動中藉由檢查**允許**或**Deny**方塊中**Participate**權限群組。</span><span class="sxs-lookup"><span data-stu-id="afb1b-147">Clicking the **Select** button invokes the Windows Access Control List editor, where you can specify the user or group that can participate in WS-Atomic transactions by checking the **Allow** or **Deny** box in the **Participate** permission group.</span></span>  
  
 <span data-ttu-id="afb1b-148">**授權的憑證**</span><span class="sxs-lookup"><span data-stu-id="afb1b-148">**Authorized Certificates**</span></span>  
  
 <span data-ttu-id="afb1b-149">按一下 **選取**按鈕會顯示一份目前可用憑證上的 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="afb1b-149">Clicking the **Select** button displays a list of currently available certificates on the LocalMachine.</span></span> <span data-ttu-id="afb1b-150">您可以選取允許哪些憑證識別參與 WS-Atomic 異動。</span><span class="sxs-lookup"><span data-stu-id="afb1b-150">You can then select which certificate identities are allowed to participate in WS-Atomic transactions.</span></span>  
  
#### <a name="timeout-group-box"></a><span data-ttu-id="afb1b-151">逾時群組方塊</span><span class="sxs-lookup"><span data-stu-id="afb1b-151">Timeout Group Box</span></span>  
 <span data-ttu-id="afb1b-152">**逾時**群組方塊可讓您指定 Ws-atomic 異動的預設和最大逾時。</span><span class="sxs-lookup"><span data-stu-id="afb1b-152">The **Timeout** group box allows you to specify the default and maximum timeout for a WS-Atomic transaction.</span></span> <span data-ttu-id="afb1b-153">傳出逾時的有效值介於 1 和 3600。</span><span class="sxs-lookup"><span data-stu-id="afb1b-153">A valid value for outgoing timeout is between 1 and 3600.</span></span> <span data-ttu-id="afb1b-154">傳入逾時的有效值介於 0 和 3600。</span><span class="sxs-lookup"><span data-stu-id="afb1b-154">A valid value for incoming timeout is between 0 and 3600.</span></span>  
  
#### <a name="tracing-and-logging-group-box"></a><span data-ttu-id="afb1b-155">追蹤和記錄群組方塊</span><span class="sxs-lookup"><span data-stu-id="afb1b-155">Tracing and Logging Group Box</span></span>  
 <span data-ttu-id="afb1b-156">**追蹤和記錄**群組方塊可讓您設定所需的追蹤和記錄層級。</span><span class="sxs-lookup"><span data-stu-id="afb1b-156">The **Tracing and Logging** group Box allows you to configure the desired tracing and logging level.</span></span>  
  
 <span data-ttu-id="afb1b-157">按一下 **選項**按鈕會叫用的頁面，您可以在其中指定其他設定。</span><span class="sxs-lookup"><span data-stu-id="afb1b-157">Clicking the **Options** button invokes a page where you can specify additional settings.</span></span>  
  
 <span data-ttu-id="afb1b-158">**追蹤層級**組合方塊可讓您選擇的任何有效的值從<xref:System.Diagnostics.TraceLevel>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="afb1b-158">The **Trace Level** combination box allows you to choose from any valid value of the <xref:System.Diagnostics.TraceLevel> enumeration.</span></span> <span data-ttu-id="afb1b-159">您也可以使用核取方塊來指定您是否要執行活動追蹤、活動傳播，或收集個人可識別資訊。</span><span class="sxs-lookup"><span data-stu-id="afb1b-159">You can also use the checkboxes to specify if you want to perform activity tracing, activity propagation or collect personal identifiable information.</span></span>  
  
 <span data-ttu-id="afb1b-160">您也可以指定記錄工作階段**記錄工作階段**群組方塊。</span><span class="sxs-lookup"><span data-stu-id="afb1b-160">You can also specify logging sessions in the **Logging Session** group box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afb1b-161">當有其他追蹤消費者正在使用 WS-AT 追蹤提供者時，您無法為追蹤事件建立新的記錄工作階段。</span><span class="sxs-lookup"><span data-stu-id="afb1b-161">When another trace consumer is using the WS-AT trace provider, you cannot create a new logging session for trace events.</span></span> <span data-ttu-id="afb1b-162">在此時任何設定記錄的嘗試，都會導致產生「無法啟用提供者。</span><span class="sxs-lookup"><span data-stu-id="afb1b-162">Any attempt to configure logging during this time results in the error message "Failed to enable provider.</span></span> <span data-ttu-id="afb1b-163">錯誤碼：1".</span><span class="sxs-lookup"><span data-stu-id="afb1b-163">Error code: 1".</span></span>  
  
 <span data-ttu-id="afb1b-164">如需有關追蹤和記錄的詳細資訊，請參閱 <<c0> [ 管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="afb1b-164">For more information about tracing and logging, see [Administration and Diagnostics](../../../docs/framework/wcf/diagnostics/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb1b-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb1b-165">See also</span></span>

- [<span data-ttu-id="afb1b-166">設定 WS-Atomic 異動支援</span><span class="sxs-lookup"><span data-stu-id="afb1b-166">Configuring WS-Atomic Transaction Support</span></span>](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [<span data-ttu-id="afb1b-167">WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="afb1b-167">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [<span data-ttu-id="afb1b-168">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="afb1b-168">Administration and Diagnostics</span></span>](../../../docs/framework/wcf/diagnostics/index.md)
