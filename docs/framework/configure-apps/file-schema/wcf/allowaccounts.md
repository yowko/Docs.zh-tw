---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 61310d530cfec2862fb64155777cd0e88132f748
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145935"
---
# <a name="ltallowaccountsgt"></a>&lt;allowAccounts&gt;
包含指定使用者帳戶的處理序裝載 Windows Communication Foundation (WCF) 服務和已授權可連線共用服務的組態項目的集合。  
  
 \<system.serviceModel.activation>  
  
## <a name="syntax"></a>語法  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|屬性|描述|  
|---------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|加入的使用者帳戶，以便裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<net.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md)或是[ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)|指定 Net Pipe 或 TCP 共用服務的組態設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
