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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b46c74ec0bfc1fc44bcaca07439c472b0fd8393f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946438"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="21549-102">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="21549-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="21549-103">提供封裝函式傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="21549-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="21549-104">`ICorDebugILFrame3` 是的 ICorDebugILFrame 和 ICorDebugILFrame2 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="21549-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21549-105">方法</span><span class="sxs-lookup"><span data-stu-id="21549-105">Methods</span></span>  
  
|<span data-ttu-id="21549-106">方法</span><span class="sxs-lookup"><span data-stu-id="21549-106">Method</span></span>|<span data-ttu-id="21549-107">描述</span><span class="sxs-lookup"><span data-stu-id="21549-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21549-108">GetReturnValueForILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="21549-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="21549-109">取得封裝函式的傳回值的 ICorDebugValue 物件。</span><span class="sxs-lookup"><span data-stu-id="21549-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21549-110">備註</span><span class="sxs-lookup"><span data-stu-id="21549-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21549-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="21549-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21549-112">需求</span><span class="sxs-lookup"><span data-stu-id="21549-112">Requirements</span></span>  
 <span data-ttu-id="21549-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21549-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21549-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21549-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21549-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21549-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21549-116">**.NET framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21549-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21549-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21549-117">See also</span></span>

- [<span data-ttu-id="21549-118">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="21549-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="21549-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="21549-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
