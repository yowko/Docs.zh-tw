---
title: WS-AtomicTransaction 組態 MMC 嵌入式管理單元
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: b1d86fa57b31d1f9be12f76c28f9d042e7e28e24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138200"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>WS-AtomicTransaction 組態 MMC 嵌入式管理單元
WS-AtomicTransaction 組態 MMC 嵌入式管理單元用於設定本機電腦和遠端電腦上的部分 WS-AtomicTransaction 設定。  
  
## <a name="remarks"></a>備註  
 如果您正在[!INCLUDE[wxp](../../../includes/wxp-md.md)]或是[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]，MMC 嵌入式管理單元可瀏覽至**控制控制台/系統管理工具/元件服務 /**，以滑鼠右鍵按一下**我的電腦**，和選取**屬性**。 這個位置與您設定 MSDTC 的位置相同。 組態的可用選項之下**WS-AT**  索引標籤。  
  
 如果您執行 Windows Vista 或[!INCLUDE[lserver](../../../includes/lserver-md.md)]，MMC 嵌入式管理單元可依序按一下**開始**按鈕，並輸入`dcomcnfg.exe`中**搜尋** 方塊中。 當 MMC 開啟時，瀏覽至**我的電腦 \ 分散式交易協調器 \ 本機 DTC**節點、 以滑鼠右鍵按一下，然後選取**屬性**。 組態的可用選項之下**WS-AT**  索引標籤。  
  
 上述的步驟用於啟動設定本機電腦的嵌入式管理單元。 如果您想要設定遠端電腦，您必須找出在遠端電腦的名稱**控制控制台/系統管理工具/元件服務 /**，並執行類似的步驟，如果您正在[!INCLUDE[wxp](../../../includes/wxp-md.md)]或[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]。 如果您執行 Windows Vista 或[!INCLUDE[lserver](../../../includes/lserver-md.md)]，按照先前的步驟適用於 Vista 並[!INCLUDE[lserver](../../../includes/lserver-md.md)]，但使用**分散式交易協調器 \ 本機 DTC**遠端電腦的節點下的節點。  
  
 若要使用此工具提供的使用者介面，您必須註冊 WsatUI.dll 檔，此檔位於以下路徑，  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 下列命令可完成註冊。  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 您可以使用這個工具修改基本 WS-AtomicTransaction 設定。 例如，您可以啟用或停用 WS-AtomicTransaction 通訊協定支援、設定 WS-AT 的 HTTP 連接埠、將 SSL 憑證繫結至 HTTP 連接埠、透過指定憑證主體名稱來設定憑證、選取追蹤模式，以及設定預設逾時與最大逾時。  
  
 如果您必須只在本機電腦上設定 WS-AtomicTransaction 支援，可使用這個工具的命令列版本。 如需有關命令列工具的詳細資訊，請參閱 < [WS-AtomicTransaction 組態公用程式 (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)主題。  
  
 請注意，MMC 嵌入式管理單元和命令列工具都不支援設定所有 WS-AT 設定。 這些設定只能透過直接修改登錄來編輯。 如需有關這些登錄設定的詳細資訊，請參閱 <<c0> [ 設定 Ws-atomic 交易支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)。  
  
### <a name="user-interface-description"></a>使用者介面說明  
 **啟用 Ws-atomic 異動網路支援**:  
  
 切換這個核取方塊可啟用或停用此嵌入式管理單元的所有 GUI 元件。  
  
 在核取此方塊前，您應該先確認已啟用網路 DTC 存取和傳入或傳出通訊 (或兩者)。 這個值可以在中進行驗證**安全性**MSDTC 嵌入式管理單元 索引標籤。  
  
#### <a name="network-group-box"></a>網路群組方塊  
 您可以在 [網路] 群組中指定 HTTPS 連接埠和其他安全性設定，如 SSL 加密。 如果 [DTC 網路交易] 未啟用，則這個群組為停用 (呈現淡灰色)。  
  
 **HTTPS 連接埠**  
  
 這是用於 WS-AT 之 HTTPS 連接埠的值。 這個值必須在 1-65535 的範圍內 (用於表示有效連接埠)。 變更 HTTP 連接埠會修改 HTTP 服務組態，意指先前使用的 WS-AT Service Address 已釋放，並根據新的連接埠註冊新的 WS-AT Service Address。 此外，新選取的連接埠會使用目前選取的 SSL 加密憑證進行加密。  
  
> [!NOTE]
>  如果在執行此工具之前，您已啟用防火牆，則會自動在例外狀況清單中註冊該連接埠。 如果在執行此工具之前，您已停用防火牆，則不必為該防火牆進行任何額外的設定。  
  
 如果您在設定 WS-AT 後啟用了防火牆，您必須再次執行這個工具，並使用這個參數提供連接埠號碼。 如果您在設定後停用防火牆，WS-AT 會繼續運作，而不必進行額外的輸入。  
  
 **端點憑證**  
  
 按一下 **選取**按鈕會顯示本機電腦，讓使用者能夠選取可以用於 SSL 加密的憑證上的目前可用憑證清單。 憑證必須包含私密金鑰。 否則，您會收到錯誤訊息。  
  
> [!NOTE]
>  為選取的連接埠設定 SSL 憑證時，如果與該連接埠關聯的原始 SSL 憑證存在的話，將會覆寫該憑證。  
  
 **授權的帳戶**  
  
 按一下**選取 [** ] 按鈕會叫用的 Windows 存取控制清單編輯器中，其中您可以指定使用者或群組可以參與 Ws-atomic 異動中藉由檢查**允許**或**Deny**方塊中**Participate**權限群組。  
  
 **授權的憑證**  
  
 按一下 **選取**按鈕會顯示一份目前可用憑證上的 LocalMachine。 您可以選取允許哪些憑證識別參與 WS-Atomic 異動。  
  
#### <a name="timeout-group-box"></a>逾時群組方塊  
 **逾時**群組方塊可讓您指定 Ws-atomic 異動的預設和最大逾時。 傳出逾時的有效值介於 1 和 3600。 傳入逾時的有效值介於 0 和 3600。  
  
#### <a name="tracing-and-logging-group-box"></a>追蹤和記錄群組方塊  
 **追蹤和記錄**群組方塊可讓您設定所需的追蹤和記錄層級。  
  
 按一下 **選項**按鈕會叫用的頁面，您可以在其中指定其他設定。  
  
 **追蹤層級**組合方塊可讓您選擇的任何有效的值從<xref:System.Diagnostics.TraceLevel>列舉型別。 您也可以使用核取方塊來指定您是否要執行活動追蹤、活動傳播，或收集個人可識別資訊。  
  
 您也可以指定記錄工作階段**記錄工作階段**群組方塊。  
  
> [!NOTE]
>  當有其他追蹤消費者正在使用 WS-AT 追蹤提供者時，您無法為追蹤事件建立新的記錄工作階段。 在此時任何設定記錄的嘗試，都會導致產生「無法啟用提供者。 錯誤碼：1".  
  
 如需有關追蹤和記錄的詳細資訊，請參閱 <<c0> [ 管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [設定 WS-Atomic 異動支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)
