---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00af9cf60d0bd2bac60950617b1315579d1a5a4d
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347344"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads > 項目
指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。  
  
 \<configuration>  
\<執行階段 >  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
## <a name="syntax"></a>語法  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出 PerfCounter.dll 是否使用 CategoryOptions 登錄設定，以判斷是否要從類別特定共用的記憶體或從全域記憶體載入效能計數器資料。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|PerfCounter.dll 不會使用 CategoryOptions 登錄設定，這是預設值。|  
|`true`|PerfCounter.dll 會使用 CategoryOptions 登錄設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET Framework 4 之前的.NET Framework 版本中，PerfCounter.dll 載入的版本會對應至執行階段載入處理序中。 如果電腦已安裝.NET Framework 2.0 和.NET Framework 1.1 版，.NET Framework 1.1 應用程式會載入 PerfCounter.dll.NET Framework 1.1 版。 從.NET Framework 4 開始，載入 PerfCounter.dll 已安裝最新版本。 這表示如果在電腦上安裝.NET Framework 4 的.NET Framework 1.1 應用程式會載入 PerfCounter.dll 的.NET Framework 4 版本。  
  
 從.NET Framework 4 中，使用效能計數器時，PerfCounter.dll 會檢查每個提供者，以判斷它是否應該從類別特定共用的記憶體或全域共用的記憶體讀取的 CategoryOptions 登錄項目。 .NET Framework 1.1 PerfCounter.dll 不會讀取該登錄項目，因為它並不知道特定類別的共用記憶體中;它一律會從全域共用記憶體讀取。  
  
 .NET Framework 4 PerfCounter.dll 回溯相容性，它不會檢查 CategoryOptions 登錄項目中的.NET Framework 1.1 應用程式執行時。 它會直接使用全域共用的記憶體的詳細資訊，就像.NET Framework 1.1 PerfCounter.dll 一樣。 不過，您可以指示檢查登錄設定，藉由啟用.NET Framework 4 PerfCounter.dll`<forcePerformanceCounterUniqueSharedMemoryReads>`項目。  
  
> [!NOTE]
>  啟用`<forcePerformanceCounterUniqueSharedMemoryReads>`項目並不保證就會使用該特定類別的共用的記憶體。 若要啟用設定`true`只會導致 PerfCounter.dll 參考 CategoryOptions 登錄設定。 CategoryOptions 的預設設定為使用特定類別的共用的記憶體中;不過，您可以變更 CategoryOptions 以指出應該使用全域共用的記憶體。  
  
 包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance。 根據預設，CategoryOptions 設為 3，這個值會指示 PerfCounter.dll 使用特定類別的共用的記憶體。 如果 CategoryOptions 設定為 0，PerfCounter.dll 會使用全域共用的記憶體。 正在建立的執行個體的名稱是與重複使用執行個體相同時，才會重複使用執行個體資料。 所有版本都都能夠寫入該類別。 如果 CategoryOptions 設定為 1 時，使用全域共用的記憶體時，但類別目錄名稱是否為重複使用的類別相同的長度，可以重複使用執行個體資料。  
  
 0 和 1 的設定可能會導致記憶體流失和效能計數器記憶體填滿。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定 PerfCounter.dll 應該參考 CategoryOptions 登錄項目，以判斷是否應該使用特定類別的共用的記憶體。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
