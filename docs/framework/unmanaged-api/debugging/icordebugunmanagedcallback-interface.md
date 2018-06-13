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
ms.openlocfilehash: 5b55b27d45ef3efea10215c8a4163b5981f9d145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422845"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="b849a-102">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b849a-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="b849a-103">提供原生 common language runtime (CLR) 沒有直接相關的事件的通知。</span><span class="sxs-lookup"><span data-stu-id="b849a-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b849a-104">方法</span><span class="sxs-lookup"><span data-stu-id="b849a-104">Methods</span></span>  
  
|<span data-ttu-id="b849a-105">方法</span><span class="sxs-lookup"><span data-stu-id="b849a-105">Method</span></span>|<span data-ttu-id="b849a-106">描述</span><span class="sxs-lookup"><span data-stu-id="b849a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b849a-107">DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b849a-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="b849a-108">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b849a-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b849a-109">備註</span><span class="sxs-lookup"><span data-stu-id="b849a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b849a-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b849a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b849a-111">需求</span><span class="sxs-lookup"><span data-stu-id="b849a-111">Requirements</span></span>  
 <span data-ttu-id="b849a-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b849a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b849a-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b849a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b849a-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b849a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b849a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b849a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b849a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b849a-116">See Also</span></span>  
 [<span data-ttu-id="b849a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b849a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
