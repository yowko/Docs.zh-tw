---
title: Common Language Runtime 中的 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ad58813da5b71b884ad55f796db3522b2f1920
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046618"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="e0993-102">Common Language Runtime 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e0993-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="e0993-103">Common language runtime (CLR) 透過各式各樣的偵錯和分析事件，提供有用的 Windows 事件追蹤 (ETW) 診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="e0993-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="e0993-104">CLR ETW 事件會運用 Windows ETW 追蹤系統，來增強 Common Language Runtime 提供的現有分析和偵錯支援。</span><span class="sxs-lookup"><span data-stu-id="e0993-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="e0993-105">您可以在 MSDN 上的[使用 ETW 改善偵錯和效能調整](https://go.microsoft.com/fwlink/?LinkID=161142)一文中取得 ETW 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e0993-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="e0993-106">您可以在 NTDebugging 部落格的 [Windows 效能工具組 - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) 一文中找到 Xperf 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e0993-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="e0993-107">事件主題中所述的所有事件都需要 .NET Framework 4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e0993-107">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="e0993-108">Windows Vista 作業系統是支援的最低需求用戶端，而 Windows Server 2008 是支援的最低需求伺服器。</span><span class="sxs-lookup"><span data-stu-id="e0993-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0993-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="e0993-109">In This Section</span></span>  
 [<span data-ttu-id="e0993-110">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="e0993-110">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="e0993-111">描述擷取及檢視 ETW 事件的工具與命令。</span><span class="sxs-lookup"><span data-stu-id="e0993-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="e0993-112">CLR ETW 提供者</span><span class="sxs-lookup"><span data-stu-id="e0993-112">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="e0993-113">提供執行階段和取消提供者的相關資訊，以及您如何使用它們處理 ETW 資料收集。</span><span class="sxs-lookup"><span data-stu-id="e0993-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="e0993-114">CLR ETW 關鍵字和層級</span><span class="sxs-lookup"><span data-stu-id="e0993-114">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="e0993-115">說明可依分類啟用事件篩選的執行階段和取消提供者的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e0993-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="e0993-116">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e0993-116">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="e0993-117">提供 CLR ETW 事件、其關鍵字、層級和事件資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e0993-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0993-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0993-118">See also</span></span>

- [<span data-ttu-id="e0993-119">.NET Framework 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e0993-119">ETW Events in the .NET Framework</span></span>](etw-events.md)
