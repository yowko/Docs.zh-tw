---
title: "效能計數器與同處理序並存應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16c43545b24f8c0290bfe993d91b7e4203ac11fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>效能計數器與同處理序並存應用程式
使用效能監視器 (Perfmon.exe)，可以區分個別執行階段的效能計數器。 本主題描述啟用這項功能所需的登錄變更。  
  
## <a name="the-default-behavior"></a>預設行為  
 根據預設，效能監視器會顯示個別應用程式的效能計數器。 不過，這在兩種案例下會發生問題：  
  
-   當您監視兩個同名的應用程式時。 例如，如果兩個應用程式的名稱都是 myapp.exe，則在 [執行個體] 資料行中，一個會顯示為 **myapp**，另一個則會顯示為 **myapp#1**。 在此情況下，很難符合特定應用程式的效能計數器。 不確定針對 **myapp#1** 所收集的資料指的是第一個 myapp.exe 還是第二個 myapp.exe。  
  
-   應用程式使用多個 Common Language Runtime 執行個體時。 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 支援同處理序並存裝載案例；亦即，單一處理序或應用程式可以載入多個 Common Language Runtime 執行個體。 如果名為 myapp.exe 的單一應用程式載入兩個執行階段執行個體，則會根據預設在 [執行個體] 資料行中將它們指定為 **myapp** 和 **myapp#1**。 在此情況下，不確定 **myapp** 和 **myapp#1** 指的是兩個同名的應用程式，還是含有兩個執行階段的相同應用程式。 如果多個同名的應用程式載入多個執行階段，則模稜兩可甚至會更高。  
  
 您可以設定登錄機碼，以消除這項模稜兩可。 針對使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 所開發的應用程式，這項登錄變更會將後接執行階段執行個體識別碼的處理序識別碼新增至 [執行個體] 資料行中的應用程式名稱。 在 [執行個體] 資料行中，現在會將應用程式識別為 *application*_`p`*processID*\_`r`*runtimeID*，而不是 *application* 或 *application*#1。 如果應用程式是使用舊版 Common Language Runtime 所開發，則在已安裝 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的情況下，該執行個體會表示為 *application\_*`p`*processID*。  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>同處理序並存應用程式的效能計數器  
 若要處理單一應用程式中裝載之多個 Common Language Runtime 版本的效能計數器，您必須變更單一登錄機碼設定，如下表所示。  
  
|||  
|-|-|  
|機碼名稱|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|值名稱|ProcessNameFormat|  
|值類型|REG_DWORD|  
|值|1 (0x00000001)|  
  
 `ProcessNameFormat` 值 0 指出已啟用預設行為；也就是說，Perfmon.exe 會顯示個別應用程式的效能計數器。 當您將此值設為 1 時，Perfmon.exe 會釐清多個版本的應用程式，並提供個別執行階段的效能計數器。 `ProcessNameFormat` 登錄機碼設定的任何其他值都不受支援，並保留供未來使用。  
  
 在您更新 `ProcessNameFormat` 登錄機碼設定之後，必須重新啟動 Perfmon.exe 或效能計數器的任何其他消費者，讓新執行個體命名功能正確地運作。  
  
 下列範例示範如何以程式設計方式變更 `ProcessNameFormat` 值。  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 當您對這個登錄進行變更時，Perfmon.exe 會將目標為 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的應用程式名稱顯示為 *application*_`p`*processID*\_`r`*runtimeID*，其中 *application* 是應用程式的名稱、*processID* 是應用程式的處理序識別碼，*runtimeID* 則是 Common Language Runtime 識別碼。 例如，如果名為 myapp.exe 的應用程式載入兩個 Common Language Runtime 執行個體，則 Perfmon.exe 可能會將其中一個執行個體識別為 myapp_p1416_r10，並將另一個執行個體識別為 myapp_p3160_r10。 執行階段識別碼只是用來釐清處理序內的執行階段；它未提供執行階段的任何其他資訊 (例如，執行階段識別碼與執行階段的版本或 SKU 無關)。  
  
 如果已安裝 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，則登錄變更也會影響使用舊版 .NET Framework 所開發的應用程式。 這些會以 *application_*`p`*processID* 形式出現在 Perfmon.exe 中，其中 *application* 是應用程式名稱，而 *processID* 是處理序識別碼。 例如，如果監視名為 myapp.exe 之兩個應用程式的效能計數器，則一個可能會顯示為 myapp_p23900，另一個則可能會顯示為 myapp_p24908。  
  
> [!NOTE]
>  如果兩個應用程式同名且使用舊版執行階段，則處理序識別碼可消除解析它們的模稜兩可。 舊版本不需要執行階段識別碼，因為舊版 Common Language Runtime 不支援並存案例。  
  
 如果 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 不存在或尚未安裝，則設定登錄機碼不受影響。 這表示，兩個同名的應用程式將會繼續在 Perfmon.exe 中顯示為 *application* 和 *application#1* (例如，**myapp** 和 **myapp#1**)。
