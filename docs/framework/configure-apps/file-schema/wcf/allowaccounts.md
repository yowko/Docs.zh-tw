---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 3432d33c0cd65af03d2b1ac1302ca2c8ff3e0f43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201638"
---
# \<allowAccounts>

包含設定專案的集合，這些專案會為裝載 Windows Communication Foundation (WCF) 服務的進程指定使用者帳戶，並授與共享服務的連線存取權。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

 無。  
  
### <a name="child-elements"></a>子元素  
  
|屬性|描述|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|為裝載 WCF 服務的進程加入使用者帳戶，並授與共享服務的連線存取權。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<net.pipe>](net-pipe.md) 或 [\<net.tcp>](net-tcp.md)|指定 Net Pipe 或 TCP 共用服務的組態設定。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
