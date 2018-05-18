---
title: Proxy 組態
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 41e1dcee90531de605b6bddc1eedc1c44235d8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="proxy-configuration"></a>Proxy 組態
Proxy 伺服器可處理資源的用戶端要求。 Proxy 可從其快取傳回要求的資源，或將要求轉送至資源所在的伺服器。 Proxy 可透過減少傳送至遠端伺服器的要求數目，來提升網路效能。 Proxy 也可用來限制對資源的存取。  
  
## <a name="adaptive-proxies"></a>調適型 Proxy  
 .NET Framework 提供兩種 Proxy：調適型和靜態。 調適型 Proxy 會在網路設定變更時調整其設定。 例如，如果膝上型電腦使用者啟動撥接網路連線，調適型 Proxy 會認可這項變更、探索及執行其新的組態指令碼，然後適當地調整其設定。  
  
 調適型 Proxy 是由組態指令碼所設定 (請參閱[自動 Proxy 偵測](../../../docs/framework/network-programming/automatic-proxy-detection.md))。 這個指令碼會產生一組應用程式通訊協定，並為每個通訊協定產生一個 Proxy。  
  
 您有數個選項可控制組態指令碼的執行方式。 您可以指定下列各項：  
  
-   下載及執行組態指令碼的頻率。  
  
-   等候指令碼下載的時間。  
  
-   系統應該用來存取 Proxy 的認證。  
  
-   系統應該用來下載組態指令碼的認證。  
  
 網路環境的變更可能會要求系統使用一組新的 Proxy。 如果網路連線中斷或已初始化新的網路連線，系統必須在新環境中找出組態指令碼的適當來源，並執行新的指令碼。  
  
 下表顯示調適型 Proxy 的組態選項。  
  
|屬性 (Attribute)、屬性 (Property) 或組態檔設定|描述|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|每次下載指令碼的經過間隔時間 (秒)。|  
|`scriptDownloadTimeout`|等候指令碼下載的時間 (秒)。|  
|`useDefaultCredentials` 或 <xref:System.Net.WebProxy.UseDefaultCredentials>|控制系統是否使用預設網路認證來存取 Proxy。|  
|`useDefaultCredentialForScriptDownload`|控制系統是否使用預設網路認證來下載組態指令碼。|  
|`usesystemdefaults`|控制是否應該從使用者的 Internet Explorer Proxy 設定讀取靜態 Proxy 設定 (Proxy 位址、略過清單和在本機上略過)。 如果這個值設定為 "true"，則會使用來自 Internet Explorer 的靜態 Proxy 設定。<br /><br /> 如果這個值為 "false" 或未設定，則可以在組態中指定靜態 Proxy 設定，並且這個設定將覆寫 Internet Explorer Proxy 設定。 若要啟用調適型 Proxy，也必須將這個值設定為 "false" 或不設定。|  
  
 下列範例示範一般調適型 Proxy 組態。  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>靜態 Proxy  
 靜態 Proxy 通常會由應用程式明確設定，或在應用程式或系統叫用組態檔時明確設定。 靜態 proxy 可用於拓撲不常變更的網路中，例如連線至公司網路的桌面電腦。  
  
 您有數個選項可控制靜態 Proxy 的運作方式。 您可以指定下列各項：  
  
-   Proxy 的位址。  
  
-   是否應該讓本機位址略過 Proxy。  
  
-   是否應該讓一組位址略過 Proxy。  
  
 下表顯示靜態 Proxy 的組態選項。  
  
|屬性 (Attribute)、屬性 (Property) 或組態檔設定|描述|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` 或 <xref:System.Net.WebProxy.Address>|所要使用的 Proxy 位址。|  
|`bypassonlocal` 或 <xref:System.Net.WebProxy.BypassProxyOnLocal>|控制本機位址是否要略過 Proxy。|  
|`bypasslist` 或 <xref:System.Net.WebProxy.BypassArrayList>|使用規則運算式描述一組略過 Proxy 的位址。|  
|`usesystemdefaults`|控制是否應該從使用者的 Internet Explorer Proxy 設定讀取靜態 Proxy 設定 (Proxy 位址、略過清單和在本機上略過)。 如果這個值設定為 "true"，則會使用來自 Internet Explorer 的靜態 Proxy 設定。 在 .NET Framework 2.0 上，當這個值設定為 "true" 時，Internet Explorer Proxy 設定不會由組態檔中的其他 Proxy 設定覆寫。 在 .NET Framework 1.1 上，Internet Explorer Proxy 設定可能會由組態檔中的其他 Proxy 設定覆寫。<br /><br /> 如果這個值為 "false" 或未設定，則可以在組態中指定靜態 Proxy 設定，並且這個設定將覆寫 Internet Explorer Proxy 設定。 若要啟用調適型 Proxy，也必須將這個值設定為 "false" 或不設定。|  
  
 下列範例示範一般靜態 Proxy 組態。  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [自動 Proxy 偵測](../../../docs/framework/network-programming/automatic-proxy-detection.md)
