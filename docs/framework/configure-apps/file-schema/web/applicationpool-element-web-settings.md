---
title: '&lt;applicationPool&gt;項目 （Web 設定）'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8700d58ff9b07c286c713544777205e043da40a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643113"
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt;項目 （Web 設定）
指定 asp.net 用於 ASP.NET 應用程式上執行整合模式中時，管理整個處理序行為的組態設定[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本。  
  
> [!IMPORTANT]
>  這個項目和功能如果您的 ASP.NET 應用程式裝載在支援僅能[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本。  
  
 \<configuration>  
\<system.web > 項目 （Web 設定）  
\<applicationPool > 項目 （Web 設定）  
  
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
|`maxConcurrentRequestsPerCPU`|指定 ASP.NET 允許每一 CPU 的同時要求數。|  
|`maxConcurrentThreadsPerCPU`|指定多少個同時執行緒可以執行應用程式集區，每個 CPU。 這會提供替代方法來控制 ASP.NET 的並行存取，因為您可以限制每一 CPU 可以用來處理要求的 managed 執行緒的數目。 依預設這個設定會是 0，這表示，ASP.NET 不會限制每個 CPU，您可以建立的執行緒數目雖然 CLR 執行緒集區也會限制可以建立的執行緒數目。|  
|`requestQueueLimit`|指定可以在單一處理序中的 適用於 ASP.NET 佇列的要求的數目上限。 當兩個或多個 ASP.NET 應用程式執行單一應用程式集區中時，對應用程式集區中的任何應用程式提出的要求的累計集受限於這項設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|包含 ASP.NET 與主應用程式之間的互動方式的相關資訊。|  
  
## <a name="remarks"></a>備註  
 當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本，在整合模式下，此項目組合，可讓您設定 ASP.NET 如何管理執行緒和佇列要求，當應用程式裝載於 IIS 應用程式集區。 如果您執行 IIS 6，或您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以傳統模式，或以 ISAPI 模式，則會忽略這些設定。  
  
 `applicationPool`設定會套用至特定版本的.NET Framework 執行的所有應用程式集區。 設定包含在 aspnet.config 檔中。 沒有這個檔案 2.0 和.NET framework 4.0 版的版本。 （3.0 與.NET framework 3.5 版會共用 aspnet.config 檔案與 2.0 版）。  
  
> [!IMPORTANT]
>  如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]上[!INCLUDE[win7](../../../../../includes/win7-md.md)]，您可以設定每個應用程式集區的個別 aspnet.config 檔案。 這可讓您量身訂做的每個應用程式集區執行緒的效能。  
  
 針對`maxConcurrentRequestsPerCPU`，預設設定為"5000 」 中設定[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]實際上會關閉要求節流也就控制 asp.net，除非您真的有 5000 個以上的要求，每個 CPU。 預設設定而定來自動管理每一 CPU 的並行存取 CLR 執行緒集區。 應用程式，讓使用大量的非同步要求處理，或已封鎖 I/O、 網路上的許多長時間執行要求將受益於提高的預設限制在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。 設定`maxConcurrentRequestsPerCPU`為零會關閉使用的 managed 執行緒來處理 ASP.NET 要求。 應用程式執行時的 IIS 應用程式集區中，要求停留在 IIS I/O 執行緒，因此並行由進行節流處理執行緒的 IIS 設定。  
  
 `requestQueueLimit`設定的運作方式一樣`requestQueueLimit`屬性[processModel](https://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d)項目，在 ASP.NET 應用程式的 Web.config 檔案中設定。 不過， `requestQueueLimit` aspnet.config 檔案中的設定會覆寫`requestQueueLimit`Web.config 檔中設定。 換句話說，如果設定了這兩個屬性 （根據預設，這是，則為 true）、 `requestQueueLimit` aspnet.config 檔中的設定的優先順序。  
  
## <a name="example"></a>範例  
 下列範例會示範如何在下列情況中 aspnet.config 檔案設定 ASP.NET 全處理序行為：  
  
-   應用程式裝載於[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]應用程式集區。  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以整合模式執行。  
  
-   應用程式使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。  
  
 在範例中的值是預設值。  
  
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
- [\<system.web> 項目 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
