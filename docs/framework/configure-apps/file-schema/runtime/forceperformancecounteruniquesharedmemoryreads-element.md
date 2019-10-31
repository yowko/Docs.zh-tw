---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: efa6dce1035f7d2cf63b74c6a03d911b5dede722
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116958"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
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
|`enabled`|必要屬性。<br /><br /> Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|PerfCounter.dll does not use the CategoryOptions registry setting This is the default.|  
|`true`|PerfCounter.dll does use the CategoryOptions registry setting.|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process. If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll. Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded. This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.  
  
 Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory. The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.  
  
 For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application. 它只會使用全域共用記憶體，如同 .NET Framework 1.1 PerfCounter。 不過，您可以藉由啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 元素，指示 .NET Framework 4 PerfCounter 檢查登錄設定。  
  
> [!NOTE]
> 啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 元素並不保證會使用類別特定的共用記憶體。 將 [已啟用] 設定為 `true` 只會導致 PerfCounter 參考 CategoryOptions 登錄設定。 CategoryOptions 的預設設定是使用類別特定的共用記憶體;不過，您可以變更 CategoryOptions，以指出應該使用全域共用記憶體。  
  
 包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< 類別名稱\>\Performance。 根據預設，CategoryOptions 會設為3，指示 PerfCounter 使用類別特定的共用記憶體。 如果 CategoryOptions 設定為0，則 PerfCounter 會使用全域共用記憶體。 只有當所建立之實例的名稱與要重複使用的實例相同時，才會重複使用實例資料。 所有版本都可以寫入類別目錄。 如果 CategoryOptions 設為1，則會使用全域共用記憶體，但是如果類別目錄名稱的長度與要重複使用的類別相同，就可以重複使用實例資料。  
  
 設定0和1可能會導致記憶體流失，並填滿效能計數器記憶體。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定 PerfCounter 應該參考 CategoryOptions 登錄專案，以判斷它是否應該使用類別特定的共用記憶體。  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
