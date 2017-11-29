---
title: "ICoreClrDebugTarget 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e13355078727a55c950bed795d3b01b6c7d52564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="0b736-102">ICoreClrDebugTarget 介面</span><span class="sxs-lookup"><span data-stu-id="0b736-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="0b736-103">提供方法來控制參考計數、 列舉處理序，並釋放與偵錯工具附加至遠端的 Macintosh Silverlight 目標相關聯的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b736-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b736-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b736-104">Syntax</span></span>  
  
```  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0b736-105">方法</span><span class="sxs-lookup"><span data-stu-id="0b736-105">Methods</span></span>  
  
|<span data-ttu-id="0b736-106">方法</span><span class="sxs-lookup"><span data-stu-id="0b736-106">Method</span></span>|<span data-ttu-id="0b736-107">說明</span><span class="sxs-lookup"><span data-stu-id="0b736-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b736-108">Icoreclrdebugtarget:: Enumprocesses 方法</span><span class="sxs-lookup"><span data-stu-id="0b736-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="0b736-109">列舉在遠端電腦上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="0b736-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="0b736-110">Icoreclrdebugtarget:: Enumruntimes 方法</span><span class="sxs-lookup"><span data-stu-id="0b736-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="0b736-111">列舉的 common language runtime (Clr) 中指定的處理序的遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="0b736-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="0b736-112">Icoreclrdebugtarget:: Freememory 方法</span><span class="sxs-lookup"><span data-stu-id="0b736-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="0b736-113">釋放由這個類別中的列舉型別方法所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0b736-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b736-114">備註</span><span class="sxs-lookup"><span data-stu-id="0b736-114">Remarks</span></span>  
 <span data-ttu-id="0b736-115">目前，這項功能僅適用於偵錯遠端的 Macintosh 電腦執行的 Silverlight 架構應用程式目標支援。</span><span class="sxs-lookup"><span data-stu-id="0b736-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b736-116">需求</span><span class="sxs-lookup"><span data-stu-id="0b736-116">Requirements</span></span>  
 <span data-ttu-id="0b736-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b736-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b736-118">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="0b736-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0b736-119">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0b736-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0b736-120">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="0b736-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b736-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b736-121">See Also</span></span>  
 [<span data-ttu-id="0b736-122">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="0b736-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="0b736-123">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="0b736-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="0b736-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0b736-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
