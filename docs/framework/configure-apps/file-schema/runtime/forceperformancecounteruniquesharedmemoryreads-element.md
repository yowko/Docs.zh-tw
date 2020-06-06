---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154136"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> 項目
指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出 PerfCounter 是否使用 CategoryOptions 登錄設定來判斷是否要從類別特定的共用記憶體或全域記憶體載入效能計數器資料。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|PerfCounter 不會使用 CategoryOptions 登錄設定，這是預設值。|  
|`true`|PerfCounter 會使用 CategoryOptions 登錄設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework 4 之前的 .NET Framework 版本中，載入的 PerfCounter 版本會雖然該值至在進程中載入的執行時間。 如果電腦已安裝 .NET Framework 版本1.1 和 .NET Framework 2.0，則 .NET Framework 1.1 應用程式會載入 .NET Framework 1.1 版本的 PerfCounter。 從 .NET Framework 4 開始，會載入最新安裝的 PerfCounter 版本。 這表示如果電腦上已安裝 .NET Framework 4，.NET Framework 1.1 應用程式將會載入 .NET Framework 4 版的 PerfCounter。  
  
 從 .NET Framework 4 開始，使用效能計數器時，PerfCounter 會檢查每個提供者的 CategoryOptions 登錄專案，以判斷它是否應該從類別特定的共用記憶體或全域共用記憶體中讀取。 .NET Framework 1.1 PerfCounter 不會讀取該登錄專案，因為它並不知道類別特定的共用記憶體;它一律會從全域共用記憶體讀取。  
  
 為了與舊版相容，.NET Framework 4 PerfCounter 在 .NET Framework 1.1 應用程式中執行時，不會檢查 CategoryOptions 登錄專案。 它只會使用全域共用記憶體，如同 .NET Framework 1.1 PerfCounter。 不過，您可以藉由啟用元素，指示 .NET Framework 4 PerfCounter 檢查登錄設定 `<forcePerformanceCounterUniqueSharedMemoryReads>` 。  
  
> [!NOTE]
> 啟用 `<forcePerformanceCounterUniqueSharedMemoryReads>` 元素並不保證會使用類別特定的共用記憶體。 將 [已啟用] 設定為 [ `true` 僅] 會導致 PerfCounter 參考 CategoryOptions 登錄設定。 CategoryOptions 的預設設定是使用類別特定的共用記憶體;不過，您可以變更 CategoryOptions，以指出應該使用全域共用記憶體。  
  
 包含 CategoryOptions 設定的登錄機碼是 HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<類別名稱 \> \Performance。 根據預設，CategoryOptions 會設為3，指示 PerfCounter 使用類別特定的共用記憶體。 如果 CategoryOptions 設定為0，則 PerfCounter 會使用全域共用記憶體。 只有當所建立之實例的名稱與要重複使用的實例相同時，才會重複使用實例資料。 所有版本都可以寫入類別目錄。 如果 CategoryOptions 設為1，則會使用全域共用記憶體，但是如果類別目錄名稱的長度與要重複使用的類別相同，就可以重複使用實例資料。  
  
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
  
## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
