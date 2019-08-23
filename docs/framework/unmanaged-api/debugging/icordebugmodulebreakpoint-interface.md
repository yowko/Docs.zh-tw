---
title: ICorDebugModuleBreakpoint Interface
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03616f2756830e180155102492b15e18fee1085c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965120"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="2df4c-102">ICorDebugModuleBreakpoint Interface</span><span class="sxs-lookup"><span data-stu-id="2df4c-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="2df4c-103">提供特定模組的存取權。</span><span class="sxs-lookup"><span data-stu-id="2df4c-103">Provides access to specific modules.</span></span> <span data-ttu-id="2df4c-104">這個介面是 ICorDebugBreakpoint 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="2df4c-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2df4c-105">方法</span><span class="sxs-lookup"><span data-stu-id="2df4c-105">Methods</span></span>  
  
|<span data-ttu-id="2df4c-106">方法</span><span class="sxs-lookup"><span data-stu-id="2df4c-106">Method</span></span>|<span data-ttu-id="2df4c-107">描述</span><span class="sxs-lookup"><span data-stu-id="2df4c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2df4c-108">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="2df4c-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="2df4c-109">取得參考已設定此中斷點之模組的 ICorDebugModule 介面指標。</span><span class="sxs-lookup"><span data-stu-id="2df4c-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2df4c-110">備註</span><span class="sxs-lookup"><span data-stu-id="2df4c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2df4c-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2df4c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df4c-112">需求</span><span class="sxs-lookup"><span data-stu-id="2df4c-112">Requirements</span></span>  
 <span data-ttu-id="2df4c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2df4c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df4c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2df4c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2df4c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df4c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df4c-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df4c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df4c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2df4c-117">See also</span></span>

- [<span data-ttu-id="2df4c-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2df4c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
