---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 2a75a33eac61d85a0dab4732cb3b0de7f4703fa7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145779"
---
# <a name="ltnettcpgt"></a>&lt;net.tcp&gt;
指定 NET.TCP Port Sharing Service 的組態設定，此服務允許多個處理序共用相同的 TCP 連接埠。  
  
 \<system.serviceModel.activation>  
\<net.tcp>  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`listenBacklog`|整數，指定由共用連線所接受但是尚未分派到 Windows Communication Foundation (WCF) 服務的最大未完成連線。 預設值為 10。|  
|`maxPendingAccepts`|整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。 預設值為 2。|  
|`MaxPendingConnections`|接聽項上等待應用程式接受連線的最大數目。 當超過這個配額值時，新的傳入連線會被捨棄，而不是等待被接受。 如訊息安全性等連線功能，可能會導致用戶端開啟一個以上的連線。 在設定這個配額值時，服務系統管理員應該考量到其他連線。 預設值為 10。|  
|`receiveTimeout`|`TimeSpan`，指定讀取框架資料以及從基礎連線執行連線分派的逾時。 預設為 "00:00:10"。|  
|`teredoEnabled`|布林值，指出是否連接埠共用服務會使用 Microsoft Teredo 服務代表 WCF 服務的 TCP 連接埠上接聽。 預設為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|包含的組態項目的集合`securityIdentifier`屬性來指定裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序的使用者帳戶。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|包含 SMSvcHost.exe 接聽程式處理序的組態設定。|  
  
## <a name="remarks"></a>備註  
 如需有關連接埠共用的詳細資訊，請參閱[Net.TCP 連接埠共用](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)。 若要了解如何設定連接埠共用服務，請參閱[設定 Net.TCP Port Sharing Service](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [Net.TCP 連接埠共用](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [設定 Net.TCP 連接埠共用服務](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
