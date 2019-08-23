---
title: ICorDebugCode3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4efcf6d477ab006e179e283ca4ce7b62c27018a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960761"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="6518f-102">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="6518f-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="6518f-103">提供擴充 "ICorDebugCode" 和 "ICorDebugCode2" 的方法, 以提供受控傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6518f-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6518f-104">方法</span><span class="sxs-lookup"><span data-stu-id="6518f-104">Methods</span></span>  
  
|<span data-ttu-id="6518f-105">方法</span><span class="sxs-lookup"><span data-stu-id="6518f-105">Method</span></span>|<span data-ttu-id="6518f-106">描述</span><span class="sxs-lookup"><span data-stu-id="6518f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6518f-107">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="6518f-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="6518f-108">針對指定的 IL 位移, 取得應放置中斷點的原生位移, 讓偵錯工具可以從函數取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="6518f-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6518f-109">備註</span><span class="sxs-lookup"><span data-stu-id="6518f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6518f-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6518f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6518f-111">需求</span><span class="sxs-lookup"><span data-stu-id="6518f-111">Requirements</span></span>  
 <span data-ttu-id="6518f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6518f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6518f-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6518f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6518f-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6518f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6518f-115">**.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6518f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6518f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6518f-116">See also</span></span>

- [<span data-ttu-id="6518f-117">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="6518f-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="6518f-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6518f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
