---
title: "&lt;system.web&gt;項目 （Web 設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 44a978eae9ae85e1ba12f117288a3c9ce4db75b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<applicationPool>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|指定 aspnet.config 檔案中的 IIS 應用程式集區的組態設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
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
