---
title: '&lt;system.web&gt;項目 （Web 設定）'
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7527ee9e7528a0da47529bae93e8112705e03a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755158"
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;system.web&gt;項目 （Web 設定）
包含 ASP.NET 裝載層如何管理整個處理序行為的詳細資訊。  
  
 \<configuration>  
\<system.web > 項目 （Web 設定）  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|指定 aspnet.config 檔案中的 IIS 應用程式集區的組態設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
 `system.web`項目和其子系`applicationPool`項目已加入至[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]從[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。 當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的，這個項目組合可以可讓您設定 ASP.NET 如何管理執行緒，以及如何它要求加入佇列時，ASP.NET 裝載於 IIS 應用程式集區。 如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本在傳統 」 或 「 ISAPI 模式中，則會忽略這些設定。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定 ASP.NET 整個處理序行為 aspnet.config 檔案中，當 ASP.NET 裝載於 IIS 應用程式集區。 這個範例假設 IIS 正在執行到整合式模式和應用程式正在使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。 版本中不會發生這種行為[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]早於[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。 此範例中的值是預設值。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|命名空間||  
|結構描述名稱||  
|驗證檔||  
|可以是空白||  
  
## <a name="see-also"></a>另請參閱  
 [\<applicationPool> 項目 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
