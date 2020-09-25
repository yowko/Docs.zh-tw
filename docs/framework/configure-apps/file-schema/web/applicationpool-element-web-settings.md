---
title: <applicationPool> 項目 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 963b25e57ae8c2cc59dcc3e50ae2a52cc04f54a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185635"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> 項目 (Web 設定)

指定當 ASP.NET 應用程式在 IIS 7.0 或更新版本上以整合模式執行時，ASP.NET 用來管理整個進程行為的設定。  
  
> [!IMPORTANT]
> 只有當您的 ASP.NET 應用程式裝載于 IIS 7.0 或更新版本時，此專案和它所支援的功能才會運作。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`maxConcurrentRequestsPerCPU`|指定 ASP.NET 允許每個 CPU 的同時要求數。|  
|`maxConcurrentThreadsPerCPU`|指定每個 CPU 的應用程式集區可以同時執行的執行緒數目。 這提供了控制 ASP.NET 並行的另一種方式，因為您可以限制每個 CPU 可以用來處理要求的 managed 執行緒數目。 依預設，此設定為0，這表示 ASP.NET 不會限制每個 CPU 可以建立的執行緒數目，但 CLR 執行緒集區也會限制可以建立的執行緒數目。|  
|`requestQueueLimit`|指定可在單一進程中將 ASP.NET 排入佇列的要求數目上限。 當兩個或多個 ASP.NET 應用程式在單一應用程式集區中執行時，對應用程式集區中的任何應用程式進行的累計要求集會受限於這項設定。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|包含 ASP.NET 如何與主應用程式互動的相關資訊。|  
  
## <a name="remarks"></a>備註  

當您在整合模式中執行 IIS 7.0 或更新版本時，此元素組合可讓您設定當應用程式裝載于 IIS 應用程式集區時，ASP.NET 管理執行緒和佇列要求的方式。 如果您執行的是 IIS 6，或是以傳統模式或在 ISAPI 模式中執行 IIS 7.0，則會忽略這些設定。  
  
這些 `applicationPool` 設定會套用至在特定版本的 .NET Framework 上執行的所有應用程式集區。 這些設定包含在 aspnet.config 檔案中。 此檔案的版本為2.0 和4.0 版的 .NET Framework。 .NET Framework 的 (版本3.0 和3.5 會共用版本為2.0 的 aspnet.config 檔案 )   
  
> [!IMPORTANT]
> 如果您在 Windows 7 上執行 IIS 7.0，您可以為每個應用程式集區設定個別的 aspnet.config 檔案。 這可讓您針對每個應用程式集區量身打造執行緒的效能。  
  
針對此 `maxConcurrentRequestsPerCPU` 設定，.NET Framework 4 中 "5000" 的預設設定會有效地關閉由 ASP.NET 控制的要求節流，除非您實際上有每個 CPU 的5000或更多要求。 預設設定會改為依賴 CLR 執行緒集區，以自動管理每個 CPU 的並行。 大量使用非同步要求處理的應用程式，或在網路 i/o 上封鎖許多長時間執行要求的應用程式，將會受益于 .NET Framework 4 中增加的預設限制。 將設定 `maxConcurrentRequestsPerCPU` 為零會關閉使用 managed 執行緒 ASP.NET 要求。 當應用程式在 IIS 應用程式集區中執行時，要求會保留在 IIS i/o 執行緒上，因此會由 IIS 執行緒設定來節流平行存取。  
  
`requestQueueLimit`設定的運作方式與 processModel 專案的 `requestQueueLimit` 屬性相同， [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100))它是在 ASP.NET 應用程式的 Web.config 檔案中設定。 不過， `requestQueueLimit` aspnet.config 檔案中的設定會覆寫 `requestQueueLimit` Web.config 檔案中的設定。 換句話說，如果兩個屬性都設定 (預設為) ，則 `requestQueueLimit` aspnet.config 檔中的設定優先。  
  
## <a name="example"></a>範例  

下列範例示範如何在下列情況下，在 aspnet.config 檔案中設定 ASP.NET 全進程的行為：  
  
- 應用程式裝載于 IIS 7.0 應用程式集區中。  
  
- IIS 7.0 以整合模式執行。  
  
- 應用程式使用 .NET Framework 3.5 SP1 或更新版本。  
  
範例中的值是預設值。  
  
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

- [\<system.web> (Web 設定的元素) ](system-web-element-web-settings.md)
