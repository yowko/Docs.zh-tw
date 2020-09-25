---
title: <system.web> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: c8b01ec217fc1b6b91ccf36c8667922b57f26852
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185583"
---
# <a name="systemweb-element-web-settings"></a>\<system.web> 項目 (Web 設定)

包含 ASP.NET 裝載層如何管理整個進程行為的相關資訊。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|在 aspnet.config 檔案中指定 IIS 應用程式集區的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|指定 common language runtime 和 .NET Framework 應用程式所使用之每個設定檔中的根項目。|  
  
## <a name="remarks"></a>備註  

從 `system.web` `applicationPool` .NET FRAMEWORK 3.5 SP1 以來，元素和其子項目已新增至 .NET Framework。 當您在整合模式中執行 IIS 7.0 或更新版本時，此元素組合可讓您設定 ASP.NET 管理執行緒的方式，以及在 ASP.NET 裝載于 IIS 應用程式集區時，它如何將要求排入佇列。 如果您在傳統或 ISAPI 模式中執行 IIS 7.0 或更新版本，則會忽略這些設定。  
  
## <a name="example"></a>範例  

下列範例示範如何在 ASP.NET 裝載于 IIS 應用程式集區時，在 aspnet.config 檔案中設定 ASP.NET 全進程的行為。 此範例假設 IIS 是以整合模式執行，且應用程式使用 .NET Framework 3.5 SP1 或更新版本。 在 .NET Framework 3.5 SP1 之前的 .NET Framework 版本中，不會發生此行為。 範例中的值是預設值。  
  
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
|可以是空的||  
  
## <a name="see-also"></a>另請參閱

- [\<applicationPool> (Web 設定的元素) ](applicationpool-element-web-settings.md)
