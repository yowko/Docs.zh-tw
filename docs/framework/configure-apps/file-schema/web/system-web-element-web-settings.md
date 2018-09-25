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
ms.openlocfilehash: 39d305d429490380c76e15bdcdde434f0d75457b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083133"
---
# <a name="ltsystemwebgt-element-web-settings"></a>&lt;system.web&gt;項目 （Web 設定）
包含 ASP.NET 裝載層管理整個處理序行為的方式的相關資訊。  
  
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
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|指定在 aspnet.config 檔中的 IIS 應用程式集區的組態設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|指定通用語言執行平台和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
 `system.web`項目和其子系`applicationPool`項目已新增至[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]自[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。 當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的，此項目組合，可讓您設定 ASP.NET 如何管理執行緒，以及如何它排入佇列的要求 ASP.NET 裝載在 IIS 應用程式集區時。 如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本在傳統或 ISAPI 模式中，則會忽略這些設定。  
  
## <a name="example"></a>範例  
 下列範例示範如何在 aspnet.config 檔中設定 ASP.NET 全處理序行為，當 ASP.NET 裝載於 IIS 應用程式集區。 此範例假設 IIS 正在執行中整合式驗證模式和應用程式使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。 此行為的版本中不會發生[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]早於[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]。 在範例中的值是預設值。  
  
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
