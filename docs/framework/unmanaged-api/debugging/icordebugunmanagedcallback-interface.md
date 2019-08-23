---
title: ICorDebugUnmanagedCallback 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a34454e7e007b4eba557c712cb824362aa5047c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952981"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="eb284-102">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="eb284-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="eb284-103">提供與 common language runtime (CLR) 不直接相關之原生事件的通知。</span><span class="sxs-lookup"><span data-stu-id="eb284-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb284-104">方法</span><span class="sxs-lookup"><span data-stu-id="eb284-104">Methods</span></span>  
  
|<span data-ttu-id="eb284-105">方法</span><span class="sxs-lookup"><span data-stu-id="eb284-105">Method</span></span>|<span data-ttu-id="eb284-106">描述</span><span class="sxs-lookup"><span data-stu-id="eb284-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb284-107">DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="eb284-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="eb284-108">通知偵錯工具已引發原生事件。</span><span class="sxs-lookup"><span data-stu-id="eb284-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb284-109">備註</span><span class="sxs-lookup"><span data-stu-id="eb284-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb284-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="eb284-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb284-111">需求</span><span class="sxs-lookup"><span data-stu-id="eb284-111">Requirements</span></span>  
 <span data-ttu-id="eb284-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb284-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb284-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb284-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb284-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb284-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb284-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb284-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb284-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb284-116">See also</span></span>

- [<span data-ttu-id="eb284-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eb284-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
