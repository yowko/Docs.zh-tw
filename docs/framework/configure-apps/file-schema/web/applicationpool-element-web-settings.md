---
title: <applicationPool> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152850"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> 項目 (Web 設定)
指定ASP.NET在 IIS 7.0 或更高版本中以整合模式運行ASP.NET應用程式時用於管理進程範圍行為的配置設置。  
  
> [!IMPORTANT]
> 僅當ASP.NET應用程式託管在 IIS 7.0 或更高版本上時，此元素及其支援的功能才起作用。  
  
[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<系統.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<應用程式池>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|指定每個 CPU ASP.NET允許的同聲請求數。|  
|`maxConcurrentThreadsPerCPU`|指定每個 CPU 的應用程式池可以同時運行多少個執行緒。 這提供了一種控制ASP.NET併發的替代方法，因為您可以限制每個 CPU 可用於服務請求的託管執行緒數。 預設情況下，此設置為 0，這意味著ASP.NET不會限制每個 CPU 可以創建的執行緒數，儘管 CLR 執行緒池也限制可創建的執行緒數。|  
|`requestQueueLimit`|指定可在單個進程中排隊等待ASP.NET的最大請求數。 當兩個或兩個ASP.NET多個應用程式在單個應用程式池中運行時，向應用程式池中的任何應用程式發出的請求的累積集受此設置的約束。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<系統.web>](system-web-element-web-settings.md)|包含有關ASP.NET如何與主機應用程式交互的資訊。|  
  
## <a name="remarks"></a>備註  

在整合模式下運行 IIS 7.0 或更高版本時，此元素組合允許您配置在應用程式託管在 IIS 應用程式池中時ASP.NET如何管理執行緒和佇列請求。 如果您運行 IIS 6 或在傳統模式或 ISAPI 模式下運行 IIS 7.0，則忽略這些設置。  
  
這些`applicationPool`設置適用于在 .NET 框架的特定版本上運行的所有應用程式池。 這些設置包含在 aspnet.config 檔中。 對於 .NET Framework 的版本 2.0 和 4.0，有此檔的版本。 （.NET 框架的版本 3.0 和 3.5 與版本 2.0 共用 aspnet.config 檔。  
  
> [!IMPORTANT]
> 如果在 Windows 7 上運行 IIS 7.0，則可以為每個應用程式池配置單獨的 aspnet.config 檔。 這允許您為每個應用程式池定制執行緒的性能。  
  
對於`maxConcurrentRequestsPerCPU`此設置，.NET Framework 4 中的預設設置"5000"可有效關閉由ASP.NET控制的請求限制，除非您每個 CPU 實際上有 5000 個或更多的請求。 預設設置取決於 CLR 執行緒池，以自動管理每個 CPU 的併發性。 大量使用非同步請求處理或網路 I/O 上有許多長時間運行的請求的應用程式將受益于 .NET 框架 4 中增加的預設限制。 設置為`maxConcurrentRequestsPerCPU`零將關閉使用託管執行緒來處理ASP.NET請求。 當應用程式在 IIS 應用程式池中運行時，請求將停留在 IIS I/O 執行緒上，因此 IIS 執行緒設置會限制併發。  
  
該`requestQueueLimit`設置的工作方式與[processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) `requestQueueLimit`元素的屬性相同，該屬性在 Web.config 檔中設置為ASP.NET應用程式。 但是，aspnet.config`requestQueueLimit`檔中的設置將覆蓋 Web.config 檔中的`requestQueueLimit`設置。 換句話說，如果兩個屬性都設置了（預設情況下，這是 true），則`requestQueueLimit`aspnet.config 檔中的設置優先。  
  
## <a name="example"></a>範例  

下面的示例演示如何在以下情況下配置 aspnet.config 檔中ASP.NET進程範圍的行為：  
  
- 應用程式託管在 IIS 7.0 應用程式池中。  
  
- IIS 7.0 以整合模式運行。  
  
- 應用程式正在使用 .NET 框架 3.5 SP1 或更高版本。  
  
示例中的值是預設值。  
  
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

- [\<系統.web>元素（Web 設置）](system-web-element-web-settings.md)
