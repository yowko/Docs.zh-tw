---
title: ICorDebugILFrame3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: b3094eb6e3006be49cf17c1ca2a220b8ec58b673
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139065"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="225ef-102">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="225ef-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="225ef-103">提供封裝函式傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="225ef-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="225ef-104">`ICorDebugILFrame3` 是 ICorDebugILFrame 和 ICorDebugILFrame2 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="225ef-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="225ef-105">方法</span><span class="sxs-lookup"><span data-stu-id="225ef-105">Methods</span></span>  
  
|<span data-ttu-id="225ef-106">方法</span><span class="sxs-lookup"><span data-stu-id="225ef-106">Method</span></span>|<span data-ttu-id="225ef-107">描述</span><span class="sxs-lookup"><span data-stu-id="225ef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="225ef-108">GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="225ef-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="225ef-109">取得 ICorDebugValue 物件，它會封裝函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="225ef-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225ef-110">備註</span><span class="sxs-lookup"><span data-stu-id="225ef-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="225ef-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="225ef-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="225ef-112">需求</span><span class="sxs-lookup"><span data-stu-id="225ef-112">Requirements</span></span>  
 <span data-ttu-id="225ef-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="225ef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="225ef-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="225ef-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="225ef-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="225ef-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="225ef-116">**.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="225ef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225ef-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="225ef-117">See also</span></span>

- [<span data-ttu-id="225ef-118">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="225ef-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="225ef-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="225ef-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
