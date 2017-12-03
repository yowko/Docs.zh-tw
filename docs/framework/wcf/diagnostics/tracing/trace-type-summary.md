---
title: "追蹤類型摘要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1570832e5f179b6d2685ad33fad743c9530bb16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="trace-type-summary"></a><span data-ttu-id="9d29a-102">追蹤類型摘要</span><span class="sxs-lookup"><span data-stu-id="9d29a-102">Trace Type Summary</span></span>
<span data-ttu-id="9d29a-103">[來源層級](http://go.microsoft.com/fwlink/?LinkID=94943)定義各種不同的追蹤層級： 重大、 錯誤、 警告、 資訊和詳細資訊，以及做為提供描述`ActivityTracing`切換輸出的旗標追蹤界限與活動傳輸事件。</span><span class="sxs-lookup"><span data-stu-id="9d29a-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="9d29a-104">您也可以檢閱[TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169)可以從發出的追蹤類型<xref:System.Diagnostics>。</span><span class="sxs-lookup"><span data-stu-id="9d29a-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="9d29a-105">下表列出最重要的幾個。</span><span class="sxs-lookup"><span data-stu-id="9d29a-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="9d29a-106">追蹤類型</span><span class="sxs-lookup"><span data-stu-id="9d29a-106">Trace Type</span></span>|<span data-ttu-id="9d29a-107">描述</span><span class="sxs-lookup"><span data-stu-id="9d29a-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="9d29a-108">Critical</span><span class="sxs-lookup"><span data-stu-id="9d29a-108">Critical</span></span>|<span data-ttu-id="9d29a-109">嚴重錯誤或應用程式損毀。</span><span class="sxs-lookup"><span data-stu-id="9d29a-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="9d29a-110">錯誤</span><span class="sxs-lookup"><span data-stu-id="9d29a-110">Error</span></span>|<span data-ttu-id="9d29a-111">可修復錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d29a-111">Recoverable error.</span></span>|  
|<span data-ttu-id="9d29a-112">警告</span><span class="sxs-lookup"><span data-stu-id="9d29a-112">Warning</span></span>|<span data-ttu-id="9d29a-113">告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="9d29a-113">Informational message.</span></span>|  
|<span data-ttu-id="9d29a-114">資訊</span><span class="sxs-lookup"><span data-stu-id="9d29a-114">Information</span></span>|<span data-ttu-id="9d29a-115">非嚴重問題。</span><span class="sxs-lookup"><span data-stu-id="9d29a-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="9d29a-116">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9d29a-116">Verbose</span></span>|<span data-ttu-id="9d29a-117">偵錯追蹤。</span><span class="sxs-lookup"><span data-stu-id="9d29a-117">Debugging trace.</span></span>|  
|<span data-ttu-id="9d29a-118">啟動</span><span class="sxs-lookup"><span data-stu-id="9d29a-118">Start</span></span>|<span data-ttu-id="9d29a-119">開始邏輯處理單位。</span><span class="sxs-lookup"><span data-stu-id="9d29a-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d29a-120">暫止</span><span class="sxs-lookup"><span data-stu-id="9d29a-120">Suspend</span></span>|<span data-ttu-id="9d29a-121">暫停邏輯處理單位。</span><span class="sxs-lookup"><span data-stu-id="9d29a-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d29a-122">繼續</span><span class="sxs-lookup"><span data-stu-id="9d29a-122">Resume</span></span>|<span data-ttu-id="9d29a-123">繼續邏輯處理單位。</span><span class="sxs-lookup"><span data-stu-id="9d29a-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d29a-124">停止</span><span class="sxs-lookup"><span data-stu-id="9d29a-124">Stop</span></span>|<span data-ttu-id="9d29a-125">停止邏輯處理單位。</span><span class="sxs-lookup"><span data-stu-id="9d29a-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d29a-126">傳輸</span><span class="sxs-lookup"><span data-stu-id="9d29a-126">Transfer</span></span>|<span data-ttu-id="9d29a-127">相互關聯身分識別變更。</span><span class="sxs-lookup"><span data-stu-id="9d29a-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="9d29a-128">活動會定義為上述追蹤類型的組合。</span><span class="sxs-lookup"><span data-stu-id="9d29a-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="9d29a-129">下列是定義本機 (追蹤來源) 範圍內理想活動的規則運算式：</span><span class="sxs-lookup"><span data-stu-id="9d29a-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="9d29a-130">這表示活動必須滿足下列條件。</span><span class="sxs-lookup"><span data-stu-id="9d29a-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="9d29a-131">必須分別由「開始」和「停止」追蹤來開始與停止</span><span class="sxs-lookup"><span data-stu-id="9d29a-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="9d29a-132">必須有「傳輸」追蹤緊接在「暫停」或「繼續」追蹤之前</span><span class="sxs-lookup"><span data-stu-id="9d29a-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="9d29a-133">在「暫停」或「繼續」追蹤之間不可以有任何追蹤 (如果有這種追蹤的話)</span><span class="sxs-lookup"><span data-stu-id="9d29a-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="9d29a-134">只要觀察到之前的條件，就可以有任意個嚴重/錯誤/警告/資訊/詳細資訊/傳輸追蹤</span><span class="sxs-lookup"><span data-stu-id="9d29a-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="9d29a-135">下列是定義全域範圍內理想活動的規則運算式：</span><span class="sxs-lookup"><span data-stu-id="9d29a-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="9d29a-136">其中 R 表示本機範圍內活動的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="9d29a-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="9d29a-137">這會轉譯為：</span><span class="sxs-lookup"><span data-stu-id="9d29a-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
