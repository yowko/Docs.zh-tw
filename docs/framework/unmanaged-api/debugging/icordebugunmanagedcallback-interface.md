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
ms.openlocfilehash: fd61c8133d9f155ae8e15bbc6aa90b2b9de1aadd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647659"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="d3d00-102">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d3d00-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="d3d00-103">提供原生與 common language runtime (CLR) 不直接相關的事件的通知。</span><span class="sxs-lookup"><span data-stu-id="d3d00-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3d00-104">方法</span><span class="sxs-lookup"><span data-stu-id="d3d00-104">Methods</span></span>  
  
|<span data-ttu-id="d3d00-105">方法</span><span class="sxs-lookup"><span data-stu-id="d3d00-105">Method</span></span>|<span data-ttu-id="d3d00-106">描述</span><span class="sxs-lookup"><span data-stu-id="d3d00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3d00-107">DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="d3d00-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="d3d00-108">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d3d00-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d00-109">備註</span><span class="sxs-lookup"><span data-stu-id="d3d00-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3d00-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d3d00-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d00-111">需求</span><span class="sxs-lookup"><span data-stu-id="d3d00-111">Requirements</span></span>  
 <span data-ttu-id="d3d00-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d00-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d00-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3d00-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3d00-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3d00-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3d00-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d00-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d00-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3d00-116">See also</span></span>
- [<span data-ttu-id="d3d00-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d3d00-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
