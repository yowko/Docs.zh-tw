---
title: <applicationPool> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 786f667bcba7959ac485b4abe667239b05059c45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941450"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool > 元素 (Web 設定)
指定當 ASP.NET 應用程式在 IIS 7.0 或更新版本上以整合模式執行時, ASP.NET 用來管理整個進程行為的設定。  
  
> [!IMPORTANT]
> 此元素和其支援的功能只有在您的 ASP.NET 應用程式裝載于 IIS 7.0 或更新版本時才能使用。  
  
 \<configuration>  
\<system.web > 元素 (Web 設定)  
\<applicationPool > 元素 (Web 設定)  
  
## <a name="syntax"></a>語法  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|指定 ASP.NET 允許每個 CPU 有多少個同時要求。|  
|`maxConcurrentThreadsPerCPU`|指定每個 CPU 的應用程式集區可以執行的同時執行緒數目。 這提供了另一種控制 ASP.NET 並行的方式, 因為您可以限制每個 CPU 可用來處理要求的受控執行緒數目。 根據預設, 此設定為 0, 這表示 ASP.NET 不會限制可針對每個 CPU 建立的執行緒數目, 不過, CLR 執行緒集區也會限制可以建立的執行緒數目。|  
|`requestQueueLimit`|指定在單一進程中可排入佇列以進行 ASP.NET 的最大要求數目。 當兩個或多個 ASP.NET 應用程式在單一應用程式集區中執行時, 對應用程式集區中的任何應用程式所做的累計要求集會受到這項設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|包含 ASP.NET 如何與主應用程式互動的相關資訊。|  
  
## <a name="remarks"></a>備註  
 當您在整合模式中執行 IIS 7.0 或更新版本時, 此元素組合可讓您設定當應用程式裝載于 IIS 應用程式集區時, ASP.NET 管理執行緒和佇列要求的方式。 如果您執行 IIS 6, 或以傳統模式或在 ISAPI 模式中執行 IIS 7.0, 則會忽略這些設定。  
  
 這些`applicationPool`設定適用于在特定版本的 .NET Framework 上執行的所有應用程式集區。 這些設定包含在 aspnet .config 檔案中。 此檔案有版本2.0 和4.0 的 .NET Framework。 (版本3.0 和3.5 的 .NET Framework 會與版本2.0 共用 aspnet .config 檔案)。  
  
> [!IMPORTANT]
> 如果您在上[!INCLUDE[win7](../../../../../includes/win7-md.md)]執行 IIS 7.0, 您可以為每個應用程式集區設定個別的 aspnet .config 檔案。 這可讓您針對每個應用程式集區量身訂做執行緒的效能。  
  
 針對此`maxConcurrentRequestsPerCPU`設定, .NET Framework 4 中預設的 "5000" 設定會有效關閉由 ASP.NET 控制的要求節流, 除非您的每個 CPU 實際上有5000個或更多的要求。 預設設定會改為依賴 CLR 執行緒集區, 以自動管理每個 CPU 的平行存取。 大量使用非同步要求處理的應用程式, 或是在網路 i/o 上封鎖了許多長時間執行的要求, 將受益于 .NET Framework 4 中增加的預設限制。 將`maxConcurrentRequestsPerCPU`設定為零會關閉使用受控執行緒來處理 ASP.NET 要求。 當應用程式在 IIS 應用程式集區中執行時, 要求會停留在 IIS i/o 執行緒上, 因此並行處理會受到 IIS 執行緒設定的節流。  
  
 此`requestQueueLimit`設定的運作方式與[processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100))元素`requestQueueLimit`的屬性相同, 此專案是在 ASP.NET 應用程式的 web.config 檔案中設定。 不過, aspnet `requestQueueLimit` .config 檔案中的設定會覆寫 web.config `requestQueueLimit`檔案中的設定。 換句話說, 如果同時設定這兩個屬性 (預設為 true), 則會優先使用`requestQueueLimit` aspnet .config 檔案中的設定。  
  
## <a name="example"></a>範例  
 下列範例示範如何在下列情況下, 在 aspnet .config 檔案中設定 ASP.NET 整個進程的行為:  
  
- 應用程式裝載于 IIS 7.0 應用程式集區中。  
  
- IIS 7.0 正在整合模式下執行。  
  
- 應用程式使用 .NET Framework 3.5 SP1 或更新版本。  
  
 範例中的值為預設值。  
  
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

- [\<system.web> 項目 (Web 設定)](system-web-element-web-settings.md)
