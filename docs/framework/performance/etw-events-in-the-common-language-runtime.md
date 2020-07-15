---
title: Common Language Runtime 中的 ETW 事件
description: 閱讀有關 common language runtime （CLR）中的 Windows 事件追蹤（ETW）事件的摘要和視圖連結。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: aa422dcb7efbc0f6f7f09e09a6c9e44b40ada86b
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309478"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="63fcb-103">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="63fcb-103">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="63fcb-104">Common language runtime (CLR) 透過各式各樣的偵錯和分析事件，提供有用的 Windows 事件追蹤 (ETW) 診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="63fcb-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="63fcb-105">CLR ETW 事件會運用 Windows ETW 追蹤系統，來增強 Common Language Runtime 提供的現有分析和偵錯支援。</span><span class="sxs-lookup"><span data-stu-id="63fcb-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="63fcb-106">如需 ETW 的詳細資訊，請參閱[使用 Etw 改善調試和效能微調](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)一文。</span><span class="sxs-lookup"><span data-stu-id="63fcb-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="63fcb-107">您可以在 NTDebugging 部落格的 [Windows 效能工具組 - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) 一文中找到 Xperf 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="63fcb-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="63fcb-108">事件主題中所述的所有事件都需要 .NET Framework 4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="63fcb-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="63fcb-109">Windows Vista 作業系統是支援的最低需求用戶端，而 Windows Server 2008 是支援的最低需求伺服器。</span><span class="sxs-lookup"><span data-stu-id="63fcb-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63fcb-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="63fcb-110">In This Section</span></span>  
 [<span data-ttu-id="63fcb-111">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="63fcb-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="63fcb-112">描述擷取及檢視 ETW 事件的工具與命令。</span><span class="sxs-lookup"><span data-stu-id="63fcb-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="63fcb-113">CLR ETW 提供者</span><span class="sxs-lookup"><span data-stu-id="63fcb-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="63fcb-114">提供執行階段和取消提供者的相關資訊，以及您如何使用它們處理 ETW 資料收集。</span><span class="sxs-lookup"><span data-stu-id="63fcb-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="63fcb-115">CLR ETW 關鍵字和層級</span><span class="sxs-lookup"><span data-stu-id="63fcb-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="63fcb-116">說明可依分類啟用事件篩選的執行階段和取消提供者的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="63fcb-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="63fcb-117">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="63fcb-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="63fcb-118">提供 CLR ETW 事件、其關鍵字、層級和事件資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="63fcb-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63fcb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63fcb-119">See also</span></span>

- [<span data-ttu-id="63fcb-120">.NET Framework 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="63fcb-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
