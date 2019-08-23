---
title: WS-AtomicTransaction 組態 MMC 嵌入式管理單元
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 1fa0548e2d63562ddcb85fc6392bf5c99d67d6c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916810"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>WS-AtomicTransaction 組態 MMC 嵌入式管理單元
WS-AtomicTransaction 組態 MMC 嵌入式管理單元用於設定本機電腦和遠端電腦上的部分 WS-AtomicTransaction 設定。  
  
## <a name="remarks"></a>備註  
 如果您執行的[!INCLUDE[wxp](../../../includes/wxp-md.md)]是[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]或, 請流覽至 [控制台]/[系統**管理工具]/[元件服務/** ], 以滑鼠右鍵按一下 [**我的電腦**],然後選取 [內容], 即可找到 MMC 嵌入式管理單元。 這個位置與您設定 MSDTC 的位置相同。 適用于設定的選項會群組在 [ **ws-at** ] 索引標籤底下。  
  
 如果您執行的是 Windows Vista [!INCLUDE[lserver](../../../includes/lserver-md.md)]或, 請按一下 [**開始**] 按鈕`dcomcnfg.exe` , 然後在 [**搜尋**] 方塊中輸入, 即可找到 MMC 嵌入式管理單元。 開啟 MMC 時, 流覽至**My 電腦 \ 分散式 Transaction COORDINATOR\LOCAL DTC**節點, 按一下滑鼠右鍵並選取 [**屬性**]。 適用于設定的選項會群組在 [ **ws-at** ] 索引標籤底下。  
  
 上述的步驟用於啟動設定本機電腦的嵌入式管理單元。 如果您想要設定遠端電腦, 您應該在 [ [!INCLUDE[wxp](../../../includes/wxp-md.md)] **控制台/系統管理工具/元件服務/** ] 中找出遠端電腦的名稱, 並在執行或[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]時執行類似的步驟。 如果您執行的是 Windows Vista [!INCLUDE[lserver](../../../includes/lserver-md.md)]或, 請遵循先前針對 Vista 和[!INCLUDE[lserver](../../../includes/lserver-md.md)]的步驟, 但在遠端電腦的節點下使用**Distributed Transaction Coordinator\Local DTC**節點。  
  
 若要使用此工具提供的使用者介面，您必須註冊 WsatUI.dll 檔，此檔位於以下路徑，  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 下列命令可完成註冊。  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 您可以使用這個工具修改基本 WS-AtomicTransaction 設定。 例如，您可以啟用或停用 WS-AtomicTransaction 通訊協定支援、設定 WS-AT 的 HTTP 連接埠、將 SSL 憑證繫結至 HTTP 連接埠、透過指定憑證主體名稱來設定憑證、選取追蹤模式，以及設定預設逾時與最大逾時。  
  
 如果您必須只在本機電腦上設定 WS-AtomicTransaction 支援，可使用這個工具的命令列版本。 如需命令列工具的詳細資訊, 請參閱[ws-atomictransaction 設定公用程式 (wsatconfig.exe .exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)主題。  
  
 請注意，MMC 嵌入式管理單元和命令列工具都不支援設定所有 WS-AT 設定。 這些設定只能透過直接修改登錄來編輯。 如需這些登錄設定的詳細資訊, 請參閱設定 WS-不可部分完成的[交易支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)。  
  
### <a name="user-interface-description"></a>使用者介面說明  
 **啟用 WS-不可部分完成的交易網路支援**:  
  
 切換這個核取方塊可啟用或停用此嵌入式管理單元的所有 GUI 元件。  
  
 在核取此方塊前，您應該先確認已啟用網路 DTC 存取和傳入或傳出通訊 (或兩者)。 此值可以在 MSDTC 嵌入式管理單元的 [**安全性**] 索引標籤中進行驗證。  
  
#### <a name="network-group-box"></a>網路群組方塊  
 您可以在 [網路] 群組中指定 HTTPS 連接埠和其他安全性設定，如 SSL 加密。 如果 [DTC 網路交易] 未啟用，則這個群組為停用 (呈現淡灰色)。  
  
 **HTTPS 埠**  
  
 這是用於 WS-AT 之 HTTPS 連接埠的值。 這個值必須在 1-65535 的範圍內 (用於表示有效連接埠)。 變更 HTTP 連接埠會修改 HTTP 服務組態，意指先前使用的 WS-AT Service Address 已釋放，並根據新的連接埠註冊新的 WS-AT Service Address。 此外，新選取的連接埠會使用目前選取的 SSL 加密憑證進行加密。  
  
> [!NOTE]
> 如果在執行此工具之前，您已啟用防火牆，則會自動在例外狀況清單中註冊該連接埠。 如果在執行此工具之前，您已停用防火牆，則不必為該防火牆進行任何額外的設定。  
  
 如果您在設定 WS-AT 後啟用了防火牆，您必須再次執行這個工具，並使用這個參數提供連接埠號碼。 如果您在設定後停用防火牆，WS-AT 會繼續運作，而不必進行額外的輸入。  
  
 **端點憑證**  
  
 按一下 [**選取**] 按鈕會顯示本機電腦上目前可用憑證的清單, 讓使用者選取可用於 SSL 加密的憑證。 憑證必須包含私密金鑰。 否則，您會收到錯誤訊息。  
  
> [!NOTE]
> 為選取的連接埠設定 SSL 憑證時，如果與該連接埠關聯的原始 SSL 憑證存在的話，將會覆寫該憑證。  
  
 **授權的帳戶**  
  
 按一下 [**選取**] 按鈕可叫用 [Windows 存取控制清單編輯器], 您可以在其中藉由核取 [**參與**] 中的 [**允許**] 或 [**拒絕**] 方塊, 來指定可參與 ws-trust 非原子交易的使用者或群組許可權群組。  
  
 **授權的憑證**  
  
 按一下 [**選取**] 按鈕會顯示 LocalMachine 上目前可用憑證的清單。 您可以選取允許哪些憑證識別參與 WS-Atomic 異動。  
  
#### <a name="timeout-group-box"></a>逾時群組方塊  
 [**超時**] 群組方塊可讓您指定 ws-trust 交易的預設和最大超時。 傳出逾時的有效值介於 1 和 3600。 傳入逾時的有效值介於 0 和 3600。  
  
#### <a name="tracing-and-logging-group-box"></a>追蹤和記錄群組方塊  
 [**追蹤和記錄**] 群組方塊可讓您設定所需的追蹤和記錄層級。  
  
 按一下 [**選項**] 按鈕會叫用一個頁面, 您可以在其中指定其他設定。  
  
 [**追蹤層級**] 下拉式列示方塊可讓您選擇任何有效的<xref:System.Diagnostics.TraceLevel>列舉值。 您也可以使用核取方塊來指定您是否要執行活動追蹤、活動傳播，或收集個人可識別資訊。  
  
 您也可以在 [**記錄會話**] 群組方塊中指定記錄會話。  
  
> [!NOTE]
> 當有其他追蹤消費者正在使用 WS-AT 追蹤提供者時，您無法為追蹤事件建立新的記錄工作階段。 在此時任何設定記錄的嘗試，都會導致產生「無法啟用提供者。 錯誤碼:1".  
  
 如需追蹤和記錄的詳細資訊, 請參閱系統[管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)。  
  
## <a name="see-also"></a>另請參閱

- [設定 WS-Atomic 異動支援](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)
