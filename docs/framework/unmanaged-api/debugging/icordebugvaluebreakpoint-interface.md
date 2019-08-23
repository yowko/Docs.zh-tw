---
title: ICorDebugValueBreakpoint Interface
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f77268e069d322d0f491f78b154cf63b691e3e38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966819"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="9814a-102">ICorDebugValueBreakpoint Interface</span><span class="sxs-lookup"><span data-stu-id="9814a-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="9814a-103">擴充 ICorDebugBreakpoint 介面, 以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="9814a-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9814a-104">方法</span><span class="sxs-lookup"><span data-stu-id="9814a-104">Methods</span></span>  
  
|<span data-ttu-id="9814a-105">方法</span><span class="sxs-lookup"><span data-stu-id="9814a-105">Method</span></span>|<span data-ttu-id="9814a-106">描述</span><span class="sxs-lookup"><span data-stu-id="9814a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9814a-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="9814a-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="9814a-108">取得 ICorDebugValue 物件的介面指標, 表示設定中斷點所在物件的值。</span><span class="sxs-lookup"><span data-stu-id="9814a-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9814a-109">備註</span><span class="sxs-lookup"><span data-stu-id="9814a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9814a-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="9814a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9814a-111">需求</span><span class="sxs-lookup"><span data-stu-id="9814a-111">Requirements</span></span>  
 <span data-ttu-id="9814a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9814a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9814a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9814a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9814a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9814a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9814a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9814a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9814a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9814a-116">See also</span></span>

- [<span data-ttu-id="9814a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9814a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
