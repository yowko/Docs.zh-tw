---
title: .NET Framework 效能
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59f8ceaf7981aebf3ae64e10d253004780f47e50
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518109"
---
# <a name="net-framework-performance"></a>.NET Framework 效能
如果您想建立高效能的應用程式，您應該以設計應用程式之其他任何功能的相同方式，來設計及規劃效能。 您可以使用 Microsoft 提供的工具來測量應用程式的效能，並在必要時改進記憶體使用量、程式碼輸送量和回應性。 本主題列出 Microsoft 提供的效能分析工具，並提供涵蓋應用程式開發之特定區域效能的其他主題連結。  
  
## <a name="designing-and-planning-for-performance"></a>設計及規劃效能  
 如果您需要高效能的應用程式，您必須以設計其他任何功能的相同方式，將效能設計到應用程式中。 您應該判斷應用程式的效能關鍵案例、設定效能目標，並及早且經常地測量這些應用程式案例的效能。 由於每個應用程式都不同，並有不同的效能關鍵執行路徑，因此及早判斷這些路徑並集中工作，可讓您提升生產力。  
  
 您不需要完全熟悉您的目標平台，即可建立高效能的應用程式。 不過，您應該了解目標平台中的哪些組件會嚴重降低效能。 您可以在開發流程初期測量效能，來達成此目的。  
  
 若要判斷哪些區域對效能很重要，以及建立您的效能目標，請一律考量使用者體驗。 啟動時間和回應性是影響使用者對應用程式觀感的兩個主要區域。 如果您的應用程式使用大量記憶體，可能對使用者顯得遲緩或影響在系統上執行的其他應用程式，或者在某些情況下，造成 Windows 市集或 Windows Phone 市集提交流程失敗。 此外，如果您判斷程式碼中有哪些部分較常執行，則可以確保程式碼中的這些部分經過適當的最佳化。  
  
## <a name="analyzing-performance"></a>分析效能  
 在您的整體開發計劃中，於開發時設定應用程式效能的測量點，並將結果與您之前設定的目標進行比較。 在您預期使用者會有的環境和硬體中測量您的應用程式。 及早分析應用程式的效能，通常可以變更日後在開發週期中修復時可能所費不貲的架構決策。 下列各節說明您可用來分析應用程式的效能工具，並討論這些工具使用的事件追蹤。  
  
### <a name="performance-tools"></a>效能工具  
 以下是您可以搭配 .NET Framework 應用程式使用的一些效能工具。  
  
|工具|描述|  
|----------|-----------------|  
|Visual Studio 效能分析|用來分析要部署至執行 Windows 作業系統的電腦之 .NET Framework 應用程式的 CPU 使用率。<br /><br /> 當您開啟專案之後，可從 Visual Studio 的 [偵錯] 功能表中取得這項工具。 如需詳細資訊，請參閱[效能總管](/visualstudio/profiling/performance-explorer)。 **注意：** 以 Windows Phone 為目標時，請使用 Windows Phone 應用程式分析 (請參閱下一列)。|  
|Windows Phone 應用程式分析|用來分析您的 Windows Phone 應用程式中的 CPU 和記憶體、網路資料傳輸速率、應用程式回應性和耗電量。<br /><br /> 當您安裝 [Windows Phone SDK](https://go.microsoft.com/fwlink/?LinkId=265773) 之後，可針對 Windows Phone 專案，從 Visual Studio 的 [偵錯] 功能表中取得這項工具。 如需詳細資訊，請參閱 [Windows Phone 的應用程式分析](https://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx)。|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|用來識別 CPU 和記憶體相關的效能問題。 這項工具使用 Windows 事件追蹤 (ETW) 和 CLR 程式碼分析應用程式開發介面，提供進階的記憶體和 CPU 調查，以及有關記憶體回收和 JIT 編譯的資訊。 如需如何使用 PerfView 的詳細資訊，請參閱應用程式中隨附的教學課程和說明檔、[Channel 9 影片教學課程](http://channel9.msdn.com/Series/PerfView-Tutorial)和[部落格文章](https://blogs.msdn.com/b/vancem/archive/tags/perfview/)。<br /><br /> 若是記憶體特定問題，請參閱 [Using PerfView for Memory Investigations](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots) (使用 PerfView 進行記憶體調查)。|  
|[Windows Performance Analyzer](https://www.microsoft.com/download/details.aspx?id=30652)|當多個應用程式在相同電腦上執行時，用來判斷整個系統效能，例如應用程式的記憶體和儲存體使用。 您可以從下載中心取得屬於 [!INCLUDE[win8](../../../includes/win8-md.md)] 的 Windows 評定及部署套件 (ADK) 一部分的這項工具。 如需詳細資訊，請參閱 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/desktop/hh448170.aspx)。|  
  
### <a name="event-tracing-for-windows-etw"></a>Windows 事件追蹤 (ETW)  
 ETW 是一項技術，可讓您取得有關執行中程式碼的診斷資訊，對於之前所提到的許多效能工具而言，是不可或缺的一項技術。 ETW 會在 .NET Framework 應用程式和 Windows 引發特定事件時建立記錄檔。 透過 ETW，您可以動態啟用和停用記錄，讓您在生產環境中執行詳細追蹤，而不需要重新啟動應用程式。 .NET Framework 提供對 ETW 事件的支援，而許多程式碼分析和效能工具會使用 ETW 來產生效能資料。 這些工具通常會啟用和停用 ETW 事件，因此熟悉這些事件會很有幫助。 您可以使用特定 ETW 事件收集有關您的應用程式特定元件的效能資訊。 如需 .NET Framework 中 ETW 支援的詳細資訊，請參閱[通用語言執行平台中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)和[工作平行程式庫和 PLINQ 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md)。  
  
## <a name="performance-by-app-type"></a>依應用程式類型的效能  
 每一種類型的 .NET Framework 應用程式都有自己用於評估效能的最佳做法、考量和工具。 下表連結至特定 .NET Framework 應用程式類型的效能主題。  
  
|應用程式類型|請參閱|  
|--------------|---------|  
|所有平台的 .NET 應用程式|[記憶體回收和效能](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [效能秘訣](../../../docs/framework/performance/performance-tips.md)|  
|以 C++、C# 和 Visual Basic 撰寫的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式|[使用 C++、C# 及 Visual Basic 的 Windows 市集應用程式的效能最佳做法](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Windows Phone 的應用程式效能考量](https://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Windows Phone 應用程式分析](https://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [使 Windows Phone 應用程式更快推出市集](https://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[WPF 效能套件](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[效能祕訣](https://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[ASP.NET 效能概觀](https://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[提升 Windows Forms 應用程式效能的實用祕訣](https://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[.NET Framework 應用程式中的快取](../../../docs/framework/performance/caching-in-net-framework-applications.md)|描述用於提升應用程式效能的快取資料技術。|  
|[延遲初始設定](../../../docs/framework/performance/lazy-initialization.md)|描述如何視需要初始化物件以提升效能，特別是在應用程式啟動時。|  
|[可靠性](../../../docs/framework/performance/reliability.md)|提供有關防止伺服器環境中發生非同步例外狀況的資訊。|  
|[撰寫大型且可回應的 .NET Framework 應用程式](../../../docs/framework/performance/writing-large-responsive-apps.md)|提供從以 Managed 程式碼重寫 C# 和 Visual Basic 編譯器蒐集的效能提示，包含數個 C# 編譯器的實際範例。|
