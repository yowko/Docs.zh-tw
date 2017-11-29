---
title: "解譯 wsatConfig.exe 傳回的錯誤碼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8bd70d22b7088a936d3243f050a4ee077d0f5c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>解譯 wsatConfig.exe 傳回的錯誤碼
本主題列出 WS-AtomicTransaction 組態公用程式 (wsatConfig.exe) 產生的錯誤碼，以及建議採取的動作。  
  
## <a name="list-of-error-codes"></a>錯誤碼清單  
  
|錯誤碼|描述|建議採取的動作|  
|----------------|-----------------|------------------------------------|  
|0|作業成功|無|  
|1|未預期的錯誤|請連絡 Microsoft|  
|2|嘗試與 MSDTC 聯繫以擷取其安全性設定時，發生未預期的錯誤。|確定 MSDTC 服務並未停用，並處理傳回之例外狀況中列示的所有問題。|  
|3|執行 WsatConfig.exe 的帳戶權限不足，無法讀取網路安全性設定。|使用系統管理員使用者帳戶執行 WsatConfig.exe。|  
|4|先啟用 MSDTC 的「網路 DTC 存取」，再嘗試啟用 WS-AT 支援。|啟用 MSDTC 的「網路 DTC 存取」，再重新執行該公用程式。|  
|5|輸入的連接埠超出範圍。 這個值必須在 1-65535 的範圍內。|更正 `-port:<portNum>`<br /><br /> 在錯誤訊息中指示的命令列選項。|  
|6|在命令列上指定了無效的端點憑證。  找不到憑證，或憑證未通過驗證。|更正 `-endpointCert` 命令列選項。 確定憑證有私密金鑰，可用於 ClientAuthentication 和 ServerAuthentication，並已安裝在 LocalMachine\MY 憑證存放區，且可完全信任。|  
|7|在命令列上指定了無效的帳戶憑證。|更正 `-accountsCerts` 命令列選項。 指定的憑證未適當指定，或找不到憑證。|  
|8|指定的預設逾時超出 1 到 3600 秒的範圍。|按照指示輸入正確的預設逾時。|  
|10|嘗試存取登錄時發生非預期的錯誤。|檢查錯誤訊息和錯誤碼有無可執行動作的項目|  
|11|無法寫入登錄。|確定錯誤訊息中所列出的金鑰能夠支援從執行 WsatConfig.exe 的帳戶存取登錄。|  
|12|嘗試存取憑證存放區時發生非預期的錯誤。|使用傳回的錯誤碼來對應至適當的系統錯誤。|  
|13|http.sys 的組態失敗。 無法為 MSDTC 建立新的 HTTPS 保留連接埠。|使用傳回的錯誤碼來對應至適當的系統錯誤。|  
|14|http.sys 的組態失敗。 無法為 MSDTC 移除先前的 HTTPS 保留連接埠。|使用傳回的錯誤碼來對應至適當的系統錯誤。|  
|15|http.sys 的組態失敗。 指定的連接埠先前已有 HTTPS 保留連接埠。|其他應用程式已取得特定連接埠的擁有權。 變更為不同的連接埠，或解除安裝或重新設定目前的應用程式。|  
|16|http.sys 的組態失敗。 無法將指定的憑證繫結至連接埠。|使用錯誤訊息中傳回的錯誤碼來對應至適當的系統錯誤。|  
|17|http.sys 的組態失敗。 無法從先前的連接埠將 SSL 憑證解除繫結。|使用錯誤訊息中傳回的錯誤碼來對應至適當的系統錯誤。 若有需要，請使用 httpcfg.exe 或 netsh.exe 移除錯誤的保留連接埠。|  
|18|http.sys 的組態失敗。 無法將指定的憑證繫結至連接埠，因為已有先前的 SSL 繫結。|其他應用程式已取得特定連接埠的擁有權。 變更為不同的連接埠，或解除安裝或重新設定目前的應用程式。|  
|19|重新啟動 MSDTC 失敗。|若有需要，請手動重新啟動 MSDTC。 如果問題持續存在，請連絡 Microsoft。|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 未安裝在遠端電腦上，或未正確安裝。|將 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 安裝在電腦上。|  
|21|遠端組態失敗，因為作業逾時。|對在遠端電腦上設定 WS-AT 的呼叫可能需要超過 90 秒的時間。|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 未安裝在遠端電腦上，或未正確安裝。|將 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 安裝在電腦上。|  
|23|遠端組態失敗，因為遠端電腦上有例外狀況。|檢查錯誤訊息有無可執行動作的項目|  
|26|傳遞至 WsatConfig.exe 的引數無效。|檢查命令列有無錯誤。|  
|27|`-accounts` 命令列選項無效。|更正 -`accounts` 命令列選項，以正確指定使用者帳戶。|  
|28|`-network` 命令列選項無效。|更正 `-network` 命令列選項，以正確指定 "enable" 或 "disable"。|  
|29|`-maxTimeout` 命令列選項無效。|依指示更正 `-maxTimeout` 命令列選項。|  
|30|`-timeout` 命令列選項無效。|依指示更正 `-timeout` 命令列選項。|  
|31|`-traceLevel` 命令列選項無效。|更正 `-traceLevel` 命令列選項，以指定下列的有效值，<br /><br /> 關閉<br />-錯誤<br />-   Critical<br />-警告<br />資訊<br />-Verbose<br />-所有|  
|32|`-traceActivity` 命令列選項無效。|透過指定 "enable" 或 "disable" 來更正 `-traceActivity` 命令列選項。|  
|33|`-traceProp` 命令列選項無效。|透過指定 "enable" 或 "disable" 來更正 `-traceProp` 命令列選項。|  
|34|`-tracePII` 命令列選項無效。|透過指定 "enable" 或 "disable" 來更正 `-tracePII` 命令列選項。|  
|37|WsatConfig.exe 無法判斷確切的電腦憑證。 這會在有多個候選項，或沒有候選項時發生。|指定憑證指紋或 Issuer\SubjectName 配對來正確識別要設定的確切憑證。|  
|38|處理序或使用者權限不足，無法變更防火牆組態。|使用系統管理員使用者帳戶執行 WsatConfig.exe。|  
|39|更新防火繬組態時，WsatConfig.exe 發生錯誤。|檢查錯誤訊息有無可執行動作的項目。|  
|40|WsatConfig.exe 無法提供 MSDTC 讀取權給憑證的私密金鑰|使用系統管理員使用者帳戶執行 WsatConfig.exe。|  
|41|找不到 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 的安裝，或是找到的版本不符合工具能夠設定的版本。|確定 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 已正確安裝，且僅使用該版本 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 隨附的 WsatConfig.exe 工具設定 WS-AT。|  
|42|命令列上有重複指定的引數。|執行 WsatConfig.exe 時，每個引數只指定一次。|  
|43|如果未啟用 WS-AT，則 WsatConfig.exe 無法更新 WS-AT 設定。|指定 `-network:enable` 做為額外的命令列引數。|  
|44|遺失必要的 Hotfix，必須先安裝該 Hotfix 才能設定 WS-AT。|如需安裝必要 Hotfix 的指示，請參閱 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 版本資訊。|  
|45|`-virtualServer` 命令列選項無效。|指定要設定之叢集資源的網路名稱，來更正 `-virtualServer` 命令列選項。|  
|46|在嘗試啟動 ETW 追蹤工作階段時發生非預期的錯誤|使用傳回的錯誤碼來對應至適當的系統錯誤。|  
|47|處理序或使用者權限不足，無法啟用 ETW 追蹤工作階段。|使用系統管理員使用者帳戶執行 WsatConfig.exe。|  
|48|在嘗試啟動 ETW 追蹤工作階段時發生非預期的錯誤。|請連絡 Microsoft。|  
|49|因為 %systemdrive% 空間不足，無法建立新記錄檔|確定 %systemdrive% 有足夠的空間供記錄檔使用。|  
|51|在嘗試啟動 ETW 追蹤工作階段時發生非預期的錯誤。|請連絡 Microsoft。|  
|52|在嘗試啟動 ETW 追蹤工作階段時發生非預期的錯誤。|請連絡 Microsoft。|  
|53|先前的 ETW 工作階段記錄檔備份失敗。|確定 %systemdrive% 有足夠的空間供記錄檔和先前的記錄檔備份 (如果有的話) 使用。 若有需要，請手動移除先前的記錄檔。|  
|55|在嘗試啟動 ETW 追蹤工作階段時發生非預期的錯誤。|請連絡 Microsoft。|  
|56|在嘗試啟動 ETW 追蹤工作階段時發生非預期的錯誤。|請連絡 Microsoft。|  
  
## <a name="see-also"></a>另請參閱  
 [WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
