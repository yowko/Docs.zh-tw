---
title: <forcePerformanceCounterUniqueSharedMemoryReads> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154136"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<強制效能計數器唯一共用記憶體讀取>元素
指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<強制效能計數器唯一共用記憶體讀取>**  
  
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
|`enabled`|必要屬性。<br /><br /> 指示 PerfCounter.dll 是否使用"類別選項"註冊表設置來確定是從特定于類別的共用記憶體或全域記憶體載入效能計數器資料。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|PerfCounter.dll 不使用類別選項註冊表設置這是預設值。|  
|`true`|PerfCounter.dll 確實使用類別選項註冊表設置。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在 .NET 框架 4 之前的 .NET 框架版本中，載入的 PerfCounter.dll 版本對應于進程中載入的運行時。 如果電腦同時安裝了 .NET 框架版本 1.1 和 .NET Framework 2.0，則 .NET 框架 1.1 應用程式將載入 PerfCounter.dll 的 .NET 框架 1.1 版本。 從 .NET 框架 4 開始，將載入最新的已安裝版本的 PerfCounter.dll。 這意味著.NET 框架 1.1 應用程式將載入 .NET 框架 4 版本的 PerfCounter.dll，如果 .NET 框架 4 安裝在電腦上。  
  
 從 .NET 框架 4 開始，使用效能計數器時，PerfCounter.dll 會檢查每個提供程式的類別選項登錄機碼，以確定是否應從特定于類別的共用記憶體或全域共用記憶體讀取該條目。 .NET 框架 1.1 PerfCounter.dll 不讀取該登錄機碼，因為它不知道特定于類別的共用記憶體;它總是從全域共用記憶體讀取。  
  
 對於向後相容性，.NET 框架 4 PerfCounter.dll 在 .NET 框架 1.1 應用程式中運行時不檢查類別選項登錄機碼。 它只使用全域共用記憶體，就像 .NET 框架 1.1 PerfCounter.dll 一樣。 但是，您可以指示 .NET 框架 4 PerfCounter.dll 通過啟用`<forcePerformanceCounterUniqueSharedMemoryReads>`該元素來檢查註冊表設置。  
  
> [!NOTE]
> 啟用該`<forcePerformanceCounterUniqueSharedMemoryReads>`元素並不保證將使用特定于類別的共用記憶體。 設置為僅啟用`true`PerfCounter.dll 以引用類別選項註冊表設置。 "類別選項"的預設設置是使用特定于類別的共用記憶體;但是，您可以更改類別選項以指示應使用全域共用記憶體。  
  
 包含"類別選項"設置的登錄機碼HKEY_LOCAL_MACHINE_System_CurrentControlSet_服務\\<類別名稱\>\性能。 預設情況下，類別選項設置為 3，指示 PerfCounter.dll 使用特定于類別的共用記憶體。 如果類別選項設置為 0，PerfCounter.dll 將使用全域共用記憶體。 僅當要創建的實例的名稱與正在重用的實例相同時，才會重用實例資料。 所有版本將能夠寫入類別。 如果"類別選項"設置為 1，則使用全域共用記憶體，但如果類別名稱的長度與正在重用的類別長度相同，則可以重複使用實例資料。  
  
 設置 0 和 1 可能導致記憶體洩漏和效能計數器記憶體填滿。  
  
## <a name="example"></a>範例  
 下面的示例演示如何指定 PerfCounter.dll 應引用類別選項登錄機碼以確定是否應使用特定于類別的共用記憶體。  
  
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
