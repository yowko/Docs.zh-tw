---
title: 執行階段分析
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d50ece4b800b77ac0447d1f22f1929f5a38a7d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306387"
---
# <a name="runtime-profiling"></a>執行階段分析
分析是在任何開發或部署案例中蒐集效能資料的一種方法。 本節適用對象為想要蒐集應用程式效能資訊的開發人員和系統管理員。  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>使用效能監視器 (Perfmon.exe) 追蹤效能  
 效能監視器是用來分析 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 應用程式的最簡單工具。 效能監視器會以圖形方式表示在 Common Language Runtime 和 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]隨附之 .NET Framework 效能計數器中找到的資料。 這些計數器可用來監視從記憶體管理到 Just-In-Time (JIT) 編譯器效能的一切內容。 它會告訴您應用程式使用的資源，這是間接測量應用程式效能的方法。 使用這些計數器可了解應用程式內部運作的方式。  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>在 Windows Vista 和更新版本上執行 Perfmon.exe  
  
1. 在命令提示字元處，輸入 **perfmon**。 [效能監視器]  主控台隨即出現。  
  
2. 在 [監視工具]  資料夾中，按一下 [效能監視器] 。  
  
3. 在 [效能監視器] 工具列中，按一下出現的 **加入** 圖示 (加號)。 如果未出現，請以滑鼠右鍵按一下監視器視窗，然後選取 [加入計數器]  選項。  
  
     這會開啟 [加入計數器]  對話方塊。 [可用的計數器]  清單方塊顯示可用的效能物件。 .NET Framework 應用程式有一些預先定義的物件，包括用於記憶體管理 (**.NET CLR 記憶體**)、互通性 (**.NET CLR Interop**)、例外狀況處理 (**.NET CLR 例外狀況**) 和多執行緒 (**.NET CLR LocksAndThreads**) 的物件。 每個效能物件都包含一些個別的效能計數器。 如需效能監視器中可用的效能計數器清單，請參閱 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)隨附之 .NET Framework 效能計數器中找到的資料。  
  
4. 選取效能物件名稱旁的核取方塊，以檢視所支援的個別效能計數器清單。  
  
5. 按一下您要檢視的效能計數器。  
  
6. 在 [所選取物件的例項] 清單方塊中，按一下 [\<所有例項>]，指定您要全域 (也就是針對整個系統) 監視 Common Language Runtime 的效能計數器。  
  
     -或-  
  
     在 [所選取物件的例項]  清單方塊中，按一下要監視該應用程式之效能計數器的應用程式名稱。  
  
     若要區別多個執行階段版本，或釐清多個同名的應用程式，您也必須修改登錄機碼。 如需詳細資訊，請參閱 [效能計數器與同處理序並存應用程式](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md)。  
  
> [!NOTE]
>  如果在執行 [效能] 主控台時安裝新的效能計數器，請停止並重新啟動 [效能] 主控台，以顯示新的計數器。  
  
 如果您想要分析某個區域或遠端共用中的組件，請確定該遠端組件在執行效能計數器的電腦上受到完全信任。 如果沒有充分信任該組件，則效能計數器將無法運作。 如需將信任授與不同區域的資訊，請參閱 [Caspol.exe (程式碼存取安全性原則工具)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)。  
  
> [!NOTE]
>  在安裝 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 的系統上，效能監視器可能不會顯示某些類別的效能計數器資料，例如「.NET CLR 資料」  和「.NET CLR 網路」 ，因為應用程式是使用 [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]所開發。 如果出現這種情況，只要將 [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) 項目新增至應用程式組態檔，就可以設定效能監視器來顯示此資料。  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>以程式設計方式讀取及建立效能計數器  
 您可以使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 所提供的類別，以程式設計方式存取 [效能] 主控台中可用的相同效能資訊。 您也可以使用這些類別，建立自訂效能計數器。 下表描述 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]中所提供的一些效能監視類別。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|代表 Windows NT 效能計數器元件。 使用這個類別可讀取現有的預先定義或自訂計數器，並將效能資料發佈 (寫入) 至自訂計數器。|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|提供與電腦上的計數器和計數器類別互動的幾種方法。|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|指定 `PerformanceCounter` 元件的安裝程式。|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|指定用以計算 `NextValue` 之 `PerformanceCounter`方法的公式。|  
  
## <a name="see-also"></a>另請參閱

- [效能計數器](../../../docs/framework/debug-trace-profile/performance-counters.md)
