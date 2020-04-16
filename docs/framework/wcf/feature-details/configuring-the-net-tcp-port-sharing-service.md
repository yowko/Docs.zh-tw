---
title: 設定 Net.TCP Port Sharing Service
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: fea2e734099c4c623dcde2a37f4c164cf9ce61ac
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464201"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>設定 Net.TCP Port Sharing Service
使用 Net.TCP 傳輸的自我裝載服務可以控制好幾項進階設定，例如 `ListenBacklog` 和 `MaxPendingAccepts`，這些設定掌管網路通訊時使用的基礎 TCP 通訊端行為。 但是，如果傳輸繫結已經停用連接埠共用 (預設為啟用)，則每個通訊端的這些設定只能套用在繫結層級中。  
  
 當 net.tcp 繫結啟用了連接埠共用 (在傳輸繫結項目上設定 `portSharingEnabled =true`)，就會隱含地允許外部處理序 (亦即 SMSvcHost.exe，可裝載 Net.TCP Port Sharing Service) 為自己管理 TCP 通訊端。 例如，使用 TCP 時請指定：  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 以這種方式進行設定時，任何在服務的傳輸繫結項目上指定的通訊端設定都會被忽略，且會優先使用 SMSvcHost.exe 所指定的通訊端設定。  
  
 若要設定 SMSvcHost.exe，請建立名為 SmSvcHost.exe.config 的 XML 組態檔並將其置放在與 SMSvcHost.exe 可執行檔相同的實體目錄中 (例如，C:\Windows\Microsoft.NET\Framework\v4.5)。  
  
 下列範例示範針對所有明確陳述之可設定值使用預設值的 SMSvcHost.exe.config 範例。  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a>需要修改 SMSvcHost.exe.config 時  
 一般來說，修改 SMSvcHost.exe.config 檔時需要特別小心，因為此檔中指定的任何組態設定都會影響電腦上使用 Net.TCP Port Sharing Service 的所有服務。 這包括 Windows Vista 上使用 Windows 進程啟動服務 (WAS) 的 TCP 啟動功能的應用程式。  
  
 但是，有時候您可能需要變更 Net.TCP Port Sharing Service 的預設組態。 例如，`maxPendingAccepts` 的預設值為 4 * 處理器數量。 裝載大量使用連接埠共用服務的伺服器，可以增加此值來達到最大的輸送量。 `maxPendingConnections` 的預設值為 100。 如果有多個並行用戶端都在呼叫服務，而服務正在卸除用戶端連接時，您也應該考慮增加這個值。  
  
 SMSvcHost.exe.config 同時包含一些可能會用到連接埠共用服務的處理序身分識別資訊。 當處理序連接至連接埠共用服務以運用共用的 TCP 連接埠時，會將正在連接的處理序之處理序身分識別與允許使用連接埠共用服務的身分識別清單進行比對。 這些標識在 SMSvcHost.exe.config\<檔案的允許帳戶>部分中指定為安全識別碼 (SID)。 根據預設，系統帳戶 (LocalService、LocalSystem 和 NetworkService) 以及 Administrators 群組的成員會被授予使用連接埠共用服務的權限。 允許處理序以其他身分識別 (例如，使用者身分識別) 來執行以連接至連接埠共用服務的應用程式，必須明確地將適當的 SID 新增至 SMSvcHost.exe.config (這些變更會等到重新啟動 SMSvc.exe 處理序之後才套用)。  
  
> [!NOTE]
> 在啟用了使用者帳戶控制 (UAC) 的 Windows Vista 系統上,本地使用者需要提升許可權,即使他們的帳戶是管理員組的成員。 為了允許這些使用者在不加升的情況下使用埠共用服務,必須顯式將使用者的 SID(或使用者是成員的組的 SID)顯式添加到 SMSvcHost.exe.config 的\<允許帳戶>部分。  
  
> [!WARNING]
> 預設的 SMSvcHost.exe.config 檔案會指定自訂 `etwProviderId` 來防止 SMSvcHost.exe 追蹤干擾服務追蹤。  
  
## <a name="see-also"></a>另請參閱

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
