---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 12709d58d9192825598b15a50baa10a54450226e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178069"
---
# \<net.tcp>

指定 NET.TCP Port Sharing Service 的組態設定，此服務允許多個處理序共用相同的 TCP 連接埠。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a>Syntax  
  
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

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`listenBacklog`|整數，指定從共用連接接受但尚未分派至 Windows Communication Foundation (WCF) 服務的最大未處理連接。 預設值為 10。|  
|`maxPendingAccepts`|整數，指定共用服務之接聽端點上、未完成之並行接收執行緒的數目上限。 預設值為 2。|  
|`MaxPendingConnections`|接聽項上等待應用程式接受連線的最大數目。 當超過這個配額值時，新的傳入連線會被捨棄，而不是等待被接受。 如訊息安全性等連線功能，可能會導致用戶端開啟一個以上的連線。 在設定這個配額值時，服務系統管理員應該考量到其他連線。 預設值為 10。|  
|`receiveTimeout`|<xref:System.TimeSpan>，指定讀取框架資料以及從基礎連線執行連線分派的逾時。 預設為 "00:00:10"。|  
|`teredoEnabled`|布林值，指出埠共用服務是否使用 Microsoft Teredo 服務代表 WCF 服務接聽 TCP 埠。 預設值為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|設定專案的集合，其中包含 `securityIdentifier` 屬性，可指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|包含 SMSvcHost.exe 接聽程式處理序的組態設定。|  
  
## <a name="remarks"></a>備註  

 如需埠共用的詳細資訊，請參閱 [Net.tcp 埠共用](../../../wcf/feature-details/net-tcp-port-sharing.md)。 若要瞭解如何設定埠共用服務，請參閱設定 [Net.tcp 埠共用服務](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [設定 Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
