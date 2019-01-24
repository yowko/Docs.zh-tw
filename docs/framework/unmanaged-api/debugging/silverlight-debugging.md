---
title: Silverlight 偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414526d498b39e894c6bd3530a446f8c06f46378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572743"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="98291-102">Silverlight 偵錯</span><span class="sxs-lookup"><span data-stu-id="98291-102">Silverlight Debugging</span></span>
<span data-ttu-id="98291-103">本節中的主題說明 Common Language Runtime (CLR) 為了支援對 Windows 作業系統或 Macintosh 平台上執行的 Silverlight 應用程式進行偵錯，所提供的環境和介面。</span><span class="sxs-lookup"><span data-stu-id="98291-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98291-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="98291-104">In This Section</span></span>  
 [<span data-ttu-id="98291-105">EnumerateCLRs 函式</span><span class="sxs-lookup"><span data-stu-id="98291-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="98291-106">提供在處理程序中列舉 CLRs 的機制。</span><span class="sxs-lookup"><span data-stu-id="98291-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="98291-107">CloseCLREnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="98291-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="98291-108">關閉所傳回的控制代碼陣列中任何有效 CLR 繼續-啟動事件[EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)，並釋放用於控制代碼和字串路徑陣列的記憶體。</span><span class="sxs-lookup"><span data-stu-id="98291-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="98291-109">CreateCoreClrDebugTarget 函式</span><span class="sxs-lookup"><span data-stu-id="98291-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="98291-110">針對處理序和執行階段列舉，建立與遠端目標的連接。</span><span class="sxs-lookup"><span data-stu-id="98291-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="98291-111">CreateCordbObject 函式</span><span class="sxs-lookup"><span data-stu-id="98291-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="98291-112">建立偵錯工具介面，以提供在遠端處理序上具現化 Managed 偵錯工作階段的功能。</span><span class="sxs-lookup"><span data-stu-id="98291-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="98291-113">CreateVersionStringFromModule 函式</span><span class="sxs-lookup"><span data-stu-id="98291-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="98291-114">從目標處理序中的 CLR 路徑來建立版本字串。</span><span class="sxs-lookup"><span data-stu-id="98291-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="98291-115">CreateDebuggingInterfaceFromVersion 函式</span><span class="sxs-lookup"><span data-stu-id="98291-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="98291-116">接受從傳回的 CLR 版本字串[CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)函式，並傳回對應的偵錯工具介面。</span><span class="sxs-lookup"><span data-stu-id="98291-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="98291-117">CoreClrDebugProcInfo 結構</span><span class="sxs-lookup"><span data-stu-id="98291-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="98291-118">代表正在遠端電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="98291-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="98291-119">CoreClrDebugRuntimeInfo 結構</span><span class="sxs-lookup"><span data-stu-id="98291-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="98291-120">代表載入遠端電腦上之處理序的 CLR 執行個體。</span><span class="sxs-lookup"><span data-stu-id="98291-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="98291-121">GetStartupNotificationEvent 函式</span><span class="sxs-lookup"><span data-stu-id="98291-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="98291-122">建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。</span><span class="sxs-lookup"><span data-stu-id="98291-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="98291-123">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="98291-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="98291-124">針對處理序和執行階段列舉，建立與遠端目標的連接。</span><span class="sxs-lookup"><span data-stu-id="98291-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="98291-125">InitDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="98291-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="98291-126">針對處理序和執行階段列舉，對要與遠端目標連接的傳輸管理員初始化。</span><span class="sxs-lookup"><span data-stu-id="98291-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="98291-127">ShutdownDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="98291-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="98291-128">關閉傳輸管理員，以便與遠端目標電腦連接。</span><span class="sxs-lookup"><span data-stu-id="98291-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98291-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98291-129">See also</span></span>
- [<span data-ttu-id="98291-130">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="98291-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [<span data-ttu-id="98291-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="98291-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="98291-132">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="98291-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [<span data-ttu-id="98291-133">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="98291-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="98291-134">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="98291-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
