---
title: "Performance Counters and In-Process Side-By-Side Applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "performance counters"
  - "performance counters,and in-process side-by-side applications"
  - "performance,.NET Framework applications"
  - "performance monitoring,counters"
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
caps.latest.revision: 26
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 26
---
# Performance Counters and In-Process Side-By-Side Applications
使用效能監視器 \(Perfmon.exe\) 時，針對個別執行階段區分效能計數器是可行的。  本主題說明啟用此功能時所需進行的登錄變更。  
  
## 預設行為  
 根據預設，效能監視器會分別顯示每一個應用程式的效能計數器。  不過，下列兩個案例卻會因此產生問題：  
  
-   當您監視兩個名稱相同的應用程式時：  例如，如果兩個應用程式的名稱都是 myapp.exe，在 \[**執行個體**\] 欄內，其中一個顯示會為 **myapp**，而另一個顯示為 **myapp\#1**。  這種情況下，很難將效能計數器對應到特定的應用程式，  因為無法釐清為 **myapp\#1** 收集的資料是第一個 myapp.exe 還是第二個 myapp.exe 的資料。  
  
-   當應用程式使用多個 Common Language Runtime 的執行個體時：  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 支援同處理序並存裝載案例。也就是說，單一處理序或應用程式可以載入多個 Common Language Runtime 的執行個體。  如果名為 myapp.exe 的單一應用程式載入兩個執行階段執行個體，則在 \[**執行個體**\] 欄中，這個兩個執行個體預設會指定為 **myapp** 和 **myapp\#1**。  這種情況下，無法釐清 **myapp** 和 **myapp\#1** 指的是相同名稱的兩個應用程式，還是具有兩個執行階段的同一個應用程式。  如果多個名稱都相同的應用程式載入多個執行階段，模稜兩可的情況會更嚴重。  
  
 您可以設定登錄機碼來消除這種模稜兩可的情況。  對使用 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開發的應用程式來說，這個登錄變更會將後面緊接執行階段執行個體識別項的處理序識別項加入至 \[**執行個體**\] 欄中的應用程式名稱。  而不是 *application* 或 *application*\#1，應用程式現在於 **執行個體** 資料行會識別為*application*\_`p`*processID*\_`r`*runtimeID* 。  如果應用程式是使用舊版 Common Language Runtime 所開發，並假設已安裝[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，則這個執行個體會表示為 *application\_*`p`*processID*。  
  
## 同處理序並存應用程式的效能計數器  
 若要處理裝載於單一應用程式之多個 Common Language Runtime 版本的效能計數器，您必須變更單一登錄機碼設定，如下表所示。  
  
|||  
|-|-|  
|機碼名稱|HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Services\\.NETFramework\\Performance|  
|數值名稱|ProcessNameFormat|  
|實值型別|REG\_DWORD|  
|值|1 \(0x00000001\)|  
  
 `ProcessNameFormat` 值為 0 表示啟用預設行為，也就是說，Perfmon.exe 會以個別應用程式為基礎顯示效能計數器。  當您將此值設為 1 時，Perfmon.exe 會使多個應用程式版本意義清楚，並且以個別執行階段為基礎提供效能計數器。  `ProcessNameFormat` 登錄機碼不支援設定為其他任何值，其他任何值都保留供未來使用。  
  
 更新 `ProcessNameFormat` 登錄機碼設定之後，您必須重新啟動 Perfmon.exe 或效能計數器的任何其他取用者，新執行個體命名功能才能正確運作。  
  
 下列範例示範如何以程式設計方式變更 `ProcessNameFormat` 值。  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 當您進行這個登錄變更時，Perfmon.exe 會將目標為 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的應用程式名稱顯示為 *application*\_`p`*processID*\_`r`*runtimeID*，其中 *application* 是應用程式的名稱，*processID* 是應用程式的處理序識別項，而 *runtimeID* 則是 Common Language Runtime 識別項。  例如，如果名為 myapp.exe 的應用程式載入兩個 Common Language Runtime 的執行個體，Perfmon.exe 可能會將其中一個執行個體識別為 myapp\_p1416\_r10，並將第二個識別為 myapp\_p3160\_r10。  執行階段識別項只能釐清處理序中的執行階段，無法提供執行階段的其他任何資訊 \(例如，執行階段 ID 與執行階段的版本或 SKU 沒有任何關聯\)。  
  
 如果已安裝 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，登錄變更也會影響使用舊版 .NET Framework 所開發的應用程式。  這些應用程式會在 Perfmon.exe 中顯示為 *application\_*`p`*processID*，其中 *application* 是應用程式名稱，而 *processID* 是處理序識別項。  例如，如果監視兩個同名應用程式 \(myapp.exe\) 的效能計數器，其中一個應用程式可能顯示為 myapp\_p23900，而另一個則顯示為 myapp\_p24908。  
  
> [!NOTE]
>  透過處理序識別項，即可消除解析兩個同名應用程式使用舊版執行階段所造成的模稜兩可情況。  舊版執行階段並不需要執行階段識別項，因為舊版 Common Language Runtime 不支援並存案例。  
  
 如果 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 不存在或已經解除安裝，則設定登錄機碼沒有任何效果。  這表示兩個同名應用程式將會繼續在 Perfmon.exe 中顯示為 *application* 和 *application\#1* \(例如，**myapp** 和 **myapp\#1**\)。