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
ms.openlocfilehash: 778359a7d26b6e2f19984a1f7ff06a527f2449f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167742"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="b724c-102">ICorDebugValueBreakpoint Interface</span><span class="sxs-lookup"><span data-stu-id="b724c-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="b724c-103">擴充 ICorDebugBreakpoint 介面，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="b724c-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b724c-104">方法</span><span class="sxs-lookup"><span data-stu-id="b724c-104">Methods</span></span>  
  
|<span data-ttu-id="b724c-105">方法</span><span class="sxs-lookup"><span data-stu-id="b724c-105">Method</span></span>|<span data-ttu-id="b724c-106">描述</span><span class="sxs-lookup"><span data-stu-id="b724c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b724c-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="b724c-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="b724c-108">ICorDebugValue 物件，表示在其中設定中斷點之物件的值取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="b724c-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b724c-109">備註</span><span class="sxs-lookup"><span data-stu-id="b724c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b724c-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b724c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b724c-111">需求</span><span class="sxs-lookup"><span data-stu-id="b724c-111">Requirements</span></span>  
 <span data-ttu-id="b724c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b724c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b724c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b724c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b724c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b724c-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b724c-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b724c-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b724c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b724c-116">See also</span></span>

- [<span data-ttu-id="b724c-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b724c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
