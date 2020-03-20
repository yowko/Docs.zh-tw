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
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152837"
---
# <a name="systemweb-element-web-settings"></a>\<系統.web>元素（Web 設置）
包含有關託管層如何管理進程範圍行為ASP.NET的資訊。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;**\<系統.web>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  

無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<應用程式池>](applicationpool-element-web-settings.md)|在 aspnet.config 檔中指定 IIS 應用程式池的配置設置。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>](../configuration-element.md)|指定通用語言運行時和 .NET Framework 應用程式使用的每個設定檔中的根項目。|  
  
## <a name="remarks"></a>備註  

該`system.web`元素及其子`applicationPool`元素從 .NET 框架 3.5 SP1 開始添加到 .NET 框架中。 在整合模式下運行 IIS 7.0 或更高版本時，此元素組合允許您配置ASP.NET如何管理執行緒以及ASP.NET託管在 IIS 應用程式池中時如何排隊請求。 如果在經典或 ISAPI 模式下運行 IIS 7.0 或更高版本，則忽略這些設置。  
  
## <a name="example"></a>範例  

下面的示例演示如何在 iIS 應用程式池中託管ASP.NET時，如何在 aspnet.config 檔中配置ASP.NET進程範圍的行為。 該示例假定 IIS 在整合模式下運行，並且應用程式正在使用 .NET 框架 3.5 SP1 或更高版本。 此行為不會在 .NET 框架 3.5 SP1 之前的版本中發生。 示例中的值是預設值。  
  
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
|可以為空||  
  
## <a name="see-also"></a>另請參閱

- [\<應用程式池>元素（Web 設置）](applicationpool-element-web-settings.md)
