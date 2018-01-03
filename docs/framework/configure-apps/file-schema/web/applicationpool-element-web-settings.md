---
title: "&lt;應用程式集區&gt;項目 （Web 設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 70119b3067342dc9bc93e0fb8a43a3242f2dacc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;應用程式集區&gt;項目 （Web 設定）
指定用來管理整個處理序的行為，以整合模式上執行 ASP.NET 應用程式時由 ASP.NET 組態設定[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本。  
  
> [!IMPORTANT]
>  這個項目和功能它支援唯一的工作如果 ASP.NET 應用程式裝載於[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本。  
  
 \<configuration>  
\<system.web > 項目 （Web 設定）  
\<應用程式集區 > 項目 （Web 設定）  
  
## <a name="syntax"></a>語法  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|指定 ASP.NET 允許每一 CPU 的同時要求數。|  
|`maxConcurrentThreadsPerCPU`|指定多少同時執行緒可以執行應用程式集區的每一個 CPU。 這會提供替代方法來控制 ASP.NET 的並行存取，因為您可以限制可用於每個 CPU 處理要求的 managed 執行緒的數目。 此設定預設值為 0，這表示，ASP.NET 不會限制每個 CPU，可以建立的執行緒數目雖然 CLR 執行緒集區也會限制可以建立的執行緒數目。|  
|`requestQueueLimit`|指定可以在單一處理序中加入佇列的 ASP.NET 的要求數目上限。 當兩個或多個 ASP.NET 應用程式執行單一應用程式集區中時，應用程式集區中的任何應用程式所提出之要求的累計集受限於這項設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|包含 ASP.NET 裝載應用程式的互動方式的相關資訊。|  
  
## <a name="remarks"></a>備註  
 當您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]或更新版本整合模式中的時，這個項目組合可以可讓您設定 ASP.NET 如何管理執行緒和佇列的要求，當應用程式裝載於 IIS 應用程式集區。 如果您執行 IIS 6 或您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以傳統模式，或以 ISAPI 模式，會忽略這些設定。  
  
 `applicationPool`設定會套用到特定的.NET framework 版本執行的所有應用程式集區。 設定包含在 aspnet.config 檔案。 沒有這個檔案針對 2.0 和.NET framework 4.0 版的版本。 （3.0 版和.NET framework 3.5 會共用 aspnet.config 檔案 2.0 版）。  
  
> [!IMPORTANT]
>  如果您執行[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]上[!INCLUDE[win7](../../../../../includes/win7-md.md)]，您可以設定每個應用程式集區的個別 aspnet.config 檔案。 這可讓您調整對流程投入的每個應用程式集區執行緒的效能。  
  
 如`maxConcurrentRequestsPerCPU`，預設值為"5000 」 中設定[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]有效地將關閉要求節流也就由 ASP.NET，除非您真的有 5000 個以上每一 CPU 的要求。 預設值改為取決於以自動管理每一 CPU 的並行存取 CLR 執行緒集區。 應用程式，讓使用大量的非同步要求處理，或有多長時間執行要求被封鎖於網路 I/O，將受益於在增加的預設限制[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。 設定`maxConcurrentRequestsPerCPU`為零會關閉使用的 managed 執行緒處理 ASP.NET 要求。 當應用程式 IIS 集區中，執行應用程式時，要求停留在 IIS I/O 執行緒，然後因此並行執行緒的 IIS 設定的。  
  
 `requestQueueLimit`設定的運作方式相同`requestQueueLimit`屬性[processModel](http://msdn.microsoft.com/en-us/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d)項目，它會設定 ASP.NET 應用程式的 Web.config 檔中。 不過， `requestQueueLimit` aspnet.config 檔案中的設定會覆寫`requestQueueLimit`Web.config 檔中設定。 換句話說，如果已設定這兩個屬性 （根據預設，這是 true）， `requestQueueLimit` aspnet.config 檔案中的設定的優先順序。  
  
## <a name="example"></a>範例  
 下列範例會示範如何在下列情況下 aspnet.config 檔案中設定 ASP.NET 整個處理序的行為：  
  
-   應用程式裝載於[!INCLUDE[iisver](../../../../../includes/iisver-md.md)]應用程式集區。  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]以整合模式執行。  
  
-   應用程式使用[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)]或更新版本。  
  
 此範例中的值是預設值。  
  
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
  
## <a name="see-also"></a>請參閱  
 [\<system.web> 項目 (Web 設定)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
