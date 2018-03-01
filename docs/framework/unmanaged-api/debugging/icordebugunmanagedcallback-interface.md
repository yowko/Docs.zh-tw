---
title: "ICorDebugUnmanagedCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e2a0dc561010ead94f1b2ffcd306a6067a04d7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="78dd9-102">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="78dd9-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="78dd9-103">提供原生 common language runtime (CLR) 沒有直接相關的事件的通知。</span><span class="sxs-lookup"><span data-stu-id="78dd9-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78dd9-104">方法</span><span class="sxs-lookup"><span data-stu-id="78dd9-104">Methods</span></span>  
  
|<span data-ttu-id="78dd9-105">方法</span><span class="sxs-lookup"><span data-stu-id="78dd9-105">Method</span></span>|<span data-ttu-id="78dd9-106">描述</span><span class="sxs-lookup"><span data-stu-id="78dd9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78dd9-107">DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="78dd9-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="78dd9-108">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="78dd9-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78dd9-109">備註</span><span class="sxs-lookup"><span data-stu-id="78dd9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78dd9-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="78dd9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78dd9-111">需求</span><span class="sxs-lookup"><span data-stu-id="78dd9-111">Requirements</span></span>  
 <span data-ttu-id="78dd9-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78dd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78dd9-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78dd9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78dd9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78dd9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78dd9-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78dd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78dd9-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="78dd9-116">See Also</span></span>  
 [<span data-ttu-id="78dd9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="78dd9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
