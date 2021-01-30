---
title: 效能計數器與同處理序並存應用程式
description: 查看 .NET 中的效能計數器和同進程並存應用程式。 使用 Perfmon.exe，以每個執行時間為基礎來區分效能計數器。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
ms.openlocfilehash: 5cc3951c65a0be37294324c767a00bc7a35634b8
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065034"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>效能計數器與同處理序並存應用程式

使用效能監視器 (Perfmon.exe)，可以區分個別執行階段的效能計數器。 本主題描述啟用這項功能所需的登錄變更。  
  
## <a name="the-default-behavior"></a>預設行為  

 根據預設，效能監視器會顯示個別應用程式的效能計數器。 不過，這在兩種案例下會發生問題：  
  
- 當您監視兩個同名的應用程式時。 例如，如果兩個應用程式的名稱都是 myapp.exe，則在 [執行個體] 資料行中，一個會顯示為 **myapp**，另一個則會顯示為 **myapp#1**。 在此情況下，很難符合特定應用程式的效能計數器。 不確定針對 **myapp#1** 所收集的資料指的是第一個 myapp.exe 還是第二個 myapp.exe。  
  
- 應用程式使用多個 Common Language Runtime 執行個體時。 .NET Framework 4 支援同進程並存裝載案例;也就是說，單一進程或應用程式可以載入多個 common language runtime 實例。 如果名為 myapp.exe 的單一應用程式載入兩個執行階段執行個體，則會根據預設在 [執行個體] 資料行中將它們指定為 **myapp** 和 **myapp#1**。 在此情況下，不確定 **myapp** 和 **myapp#1** 指的是兩個同名的應用程式，還是含有兩個執行階段的相同應用程式。 如果多個同名的應用程式載入多個執行階段，則模稜兩可甚至會更高。  
  
 您可以設定登錄機碼，以消除這項模稜兩可。 針對使用 .NET Framework 4 開發的應用程式，此登錄變更會在 **實例** 資料行中，將一個進程識別碼加上執行時間實例識別碼加上應用程式名稱。 應用程式現在會  `p`  \_ `r` 在 **實例** 資料行中識別為應用程式 _ processID runtimeID，而不是應用程式或應用程式 #1。 如果應用程式是使用舊版 common language runtime 開發的，則該實例會表示為 *應用程式 \_* `p` *processID* ，前提是已安裝 .NET Framework 4。  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>同處理序並存應用程式的效能計數器  

 若要處理單一應用程式中裝載之多個 Common Language Runtime 版本的效能計數器，您必須變更單一登錄機碼設定，如下表所示。  
  
|||  
|-|-|  
|索引鍵名稱|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|值名稱|ProcessNameFormat|  
|值類型|REG_DWORD|  
|值|2 (0x00000002) |
  
 `ProcessNameFormat` 值 0 指出已啟用預設行為；也就是說，Perfmon.exe 會顯示個別應用程式的效能計數器。 當您將此值設定為2時，Perfmon.exe 會厘清應用程式的多個版本，並以每個執行時間為基礎提供效能計數器。 `ProcessNameFormat` 登錄機碼設定的任何其他值都不受支援，並保留供未來使用。
  
 在您更新 `ProcessNameFormat` 登錄機碼設定之後，必須重新啟動 Perfmon.exe 或效能計數器的任何其他消費者，讓新執行個體命名功能正確地運作。  
  
 下列範例示範如何以程式設計方式變更 `ProcessNameFormat` 值。  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 當您進行這項登錄變更時，如果已安裝 .NET Framework 4 或更新版本，Perfmon.exe 會將應用程式的名稱顯示為 *應用* 程式 _ `p` *processID*，其中 *應用* 程式是應用程式的名稱，而 *processID* 是應用程式的處理序識別碼。 例如，如果名為 myapp.exe 的應用程式載入 common language runtime 的兩個實例，Perfmon.exe 可能會將一個實例識別為 myapp_1416，而第二個則為 myapp_3160。
  
> [!NOTE]
> 如果兩個應用程式同名且使用舊版執行階段，則處理序識別碼可消除解析它們的模稜兩可。 舊版本不需要執行階段識別碼，因為舊版 Common Language Runtime 不支援並存案例。  
  
 如果 .NET Framework 4 或更新版本不存在或已卸載，則設定登錄機碼沒有任何作用。 這表示，兩個同名的應用程式將會繼續在 Perfmon.exe 中顯示為 *application* 和 *application#1* (例如，**myapp** 和 **myapp#1**)。
