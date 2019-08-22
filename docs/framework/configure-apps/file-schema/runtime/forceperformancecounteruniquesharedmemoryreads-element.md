---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96d38abad37f9460230164de784a1258e7e937a4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663715"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<Q s > 元素
指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。  
  
 \<configuration>  
\<執行時間 >  
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
|`enabled`|必要屬性。<br /><br /> 指出 PerfCounter 是否使用 CategoryOptions 登錄設定來判斷是否要從類別特定的共用記憶體或全域記憶體載入效能計數器資料。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|PerfCounter 不會使用 CategoryOptions 登錄設定, 這是預設值。|  
|`true`|PerfCounter 會使用 CategoryOptions 登錄設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 4 之前的 .NET Framework 版本中, 載入的 PerfCounter 版本會雖然該值至在進程中載入的執行時間。 如果電腦已安裝 .NET Framework 版本1.1 和 .NET Framework 2.0, 則 .NET Framework 1.1 應用程式會載入 .NET Framework 1.1 版本的 PerfCounter。 從 .NET Framework 4 開始, 會載入最新安裝的 PerfCounter 版本。 這表示如果電腦上已安裝 .NET Framework 4, .NET Framework 1.1 應用程式將會載入 .NET Framework 4 版的 PerfCounter。  
  
 從 .NET Framework 4 開始, 使用效能計數器時, PerfCounter 會檢查每個提供者的 CategoryOptions 登錄專案, 以判斷它是否應該從類別特定的共用記憶體或全域共用記憶體中讀取。 .NET Framework 1.1 PerfCounter 不會讀取該登錄專案, 因為它並不知道類別特定的共用記憶體;它一律會從全域共用記憶體讀取。  
  
 為了與舊版相容, .NET Framework 4 PerfCounter 在 .NET Framework 1.1 應用程式中執行時, 不會檢查 CategoryOptions 登錄專案。 它只會使用全域共用記憶體, 如同 .NET Framework 1.1 PerfCounter。 不過, 您可以藉由啟用`<forcePerformanceCounterUniqueSharedMemoryReads>`元素, 指示 .NET Framework 4 PerfCounter 檢查登錄設定。  
  
> [!NOTE]
>  `<forcePerformanceCounterUniqueSharedMemoryReads>`啟用元素並不保證會使用類別特定的共用記憶體。 將 [已`true`啟用] 設定為 [僅] 會導致 PerfCounter 參考 CategoryOptions 登錄設定。 CategoryOptions 的預設設定是使用類別特定的共用記憶體;不過, 您可以變更 CategoryOptions, 以指出應該使用全域共用記憶體。  
  
 包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< 類別名稱 \Performance.\> 根據預設, CategoryOptions 會設為 3, 指示 PerfCounter 使用類別特定的共用記憶體。 如果 CategoryOptions 設定為 0, 則 PerfCounter 會使用全域共用記憶體。 只有當所建立之實例的名稱與要重複使用的實例相同時, 才會重複使用實例資料。 所有版本都可以寫入類別目錄。 如果 CategoryOptions 設為 1, 則會使用全域共用記憶體, 但是如果類別目錄名稱的長度與要重複使用的類別相同, 就可以重複使用實例資料。  
  
 設定0和1可能會導致記憶體流失, 並填滿效能計數器記憶體。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定 PerfCounter 應該參考 CategoryOptions 登錄專案, 以判斷它是否應該使用類別特定的共用記憶體。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
