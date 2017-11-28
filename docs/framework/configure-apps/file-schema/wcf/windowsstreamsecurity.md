---
title: "&lt;windowsstreamsecurity 正在&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a>&lt;windowsstreamsecurity 正在&gt;
指定自訂繫結的 Windows 資料流安全性設定。  
  
 \<system.serviceModel >  
\<繫結 >  
\<customBinding >  
\<繫結 >  
\<windowsstreamsecurity 正在 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|protectionLevel|定義訊息層級安全性。 簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。 加密會提供傳輸期間的資料層級隱私權。 有效值包括以下的值：<br /><br /> -None： 無保護。<br />-Sign： 簽署訊息。<br />-EncryptAndSign： 訊息已簽署和加密。<br /><br /> 預設為 EncryptAndSign。<br /><br /> 此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。 具體來說，WCF 會提供安全性升級。 此傳輸安全性的組態由此此組態項目以及[ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)，其中可以設定並新增至自訂繫結  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
