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
ms.openlocfilehash: 60a1546068ae6a8c8be1c0af1ef3c7d770c23d70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128671"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="4a291-102">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4a291-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="4a291-103">提供原生與 common language runtime (CLR) 不直接相關的事件的通知。</span><span class="sxs-lookup"><span data-stu-id="4a291-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a291-104">方法</span><span class="sxs-lookup"><span data-stu-id="4a291-104">Methods</span></span>  
  
|<span data-ttu-id="4a291-105">方法</span><span class="sxs-lookup"><span data-stu-id="4a291-105">Method</span></span>|<span data-ttu-id="4a291-106">描述</span><span class="sxs-lookup"><span data-stu-id="4a291-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a291-107">DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="4a291-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="4a291-108">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="4a291-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a291-109">備註</span><span class="sxs-lookup"><span data-stu-id="4a291-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a291-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4a291-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a291-111">需求</span><span class="sxs-lookup"><span data-stu-id="4a291-111">Requirements</span></span>  
 <span data-ttu-id="4a291-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a291-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a291-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a291-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a291-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a291-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a291-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a291-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a291-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a291-116">See also</span></span>

- [<span data-ttu-id="4a291-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4a291-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
