---
title: Silverlight 偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790317"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="6d744-102">Silverlight 偵錯</span><span class="sxs-lookup"><span data-stu-id="6d744-102">Silverlight Debugging</span></span>
<span data-ttu-id="6d744-103">本節中的主題說明 Common Language Runtime (CLR) 為了支援對 Windows 作業系統或 Macintosh 平台上執行的 Silverlight 應用程式進行偵錯，所提供的環境和介面。</span><span class="sxs-lookup"><span data-stu-id="6d744-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d744-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6d744-104">In This Section</span></span>  
 [<span data-ttu-id="6d744-105">EnumerateCLRs 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="6d744-106">提供在處理程序中列舉 CLRs 的機制。</span><span class="sxs-lookup"><span data-stu-id="6d744-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="6d744-107">CloseCLREnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="6d744-108">關閉位於[EnumerateCLRs](enumerateclrs-function.md)函式所傳回之控制碼陣列中的任何有效 CLR 繼續-啟動事件，並釋放控制碼和字串路徑陣列的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6d744-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="6d744-109">CreateCoreClrDebugTarget 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="6d744-110">針對處理序和執行階段列舉，建立與遠端目標的連接。</span><span class="sxs-lookup"><span data-stu-id="6d744-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6d744-111">CreateCordbObject 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="6d744-112">建立偵錯工具介面，以提供在遠端處理序上具現化 Managed 偵錯工作階段的功能。</span><span class="sxs-lookup"><span data-stu-id="6d744-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="6d744-113">CreateVersionStringFromModule 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="6d744-114">從目標處理序中的 CLR 路徑來建立版本字串。</span><span class="sxs-lookup"><span data-stu-id="6d744-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="6d744-115">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="6d744-116">接受從[CreateVersionStringFromModule](createversionstringfrommodule-function.md)函式函式傳回的 CLR 版本字串，並傳回對應的偵錯工具介面。</span><span class="sxs-lookup"><span data-stu-id="6d744-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="6d744-117">CoreClrDebugProcInfo 結構</span><span class="sxs-lookup"><span data-stu-id="6d744-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="6d744-118">代表正在遠端電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="6d744-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="6d744-119">CoreClrDebugRuntimeInfo 結構</span><span class="sxs-lookup"><span data-stu-id="6d744-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="6d744-120">代表載入遠端電腦上之處理序的 CLR 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6d744-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="6d744-121">GetStartupNotificationEvent 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="6d744-122">建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6d744-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="6d744-123">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="6d744-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="6d744-124">針對處理序和執行階段列舉，建立與遠端目標的連接。</span><span class="sxs-lookup"><span data-stu-id="6d744-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6d744-125">InitDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="6d744-126">針對處理序和執行階段列舉，初始化要與遠端目標連接的傳輸管理員。</span><span class="sxs-lookup"><span data-stu-id="6d744-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6d744-127">ShutdownDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="6d744-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="6d744-128">關閉要與遠端目標電腦連接的傳輸管理員。</span><span class="sxs-lookup"><span data-stu-id="6d744-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d744-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d744-129">See also</span></span>

- [<span data-ttu-id="6d744-130">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="6d744-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="6d744-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6d744-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6d744-132">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6d744-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="6d744-133">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="6d744-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="6d744-134">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="6d744-134">Debugging Structures</span></span>](debugging-structures.md)
