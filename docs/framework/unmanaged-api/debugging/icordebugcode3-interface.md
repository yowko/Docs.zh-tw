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
ms.openlocfilehash: 5cb9aa09447acf28f1ed10ba409ce936cdb4f84a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085034"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="70be0-102">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="70be0-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="70be0-103">提供可擴充"ICorDebugCode"和"ICorDebugCode2 」 可以提供 managed 傳回值的相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="70be0-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70be0-104">方法</span><span class="sxs-lookup"><span data-stu-id="70be0-104">Methods</span></span>  
  
|<span data-ttu-id="70be0-105">方法</span><span class="sxs-lookup"><span data-stu-id="70be0-105">Method</span></span>|<span data-ttu-id="70be0-106">描述</span><span class="sxs-lookup"><span data-stu-id="70be0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70be0-107">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="70be0-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="70be0-108">指定的 IL 位移，取得原生位移的中斷點應放置的位置，讓偵錯工具可以從函式取得的傳回值。</span><span class="sxs-lookup"><span data-stu-id="70be0-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70be0-109">備註</span><span class="sxs-lookup"><span data-stu-id="70be0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70be0-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="70be0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70be0-111">需求</span><span class="sxs-lookup"><span data-stu-id="70be0-111">Requirements</span></span>  
 <span data-ttu-id="70be0-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70be0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70be0-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70be0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70be0-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70be0-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70be0-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="70be0-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70be0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70be0-116">See also</span></span>

- [<span data-ttu-id="70be0-117">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="70be0-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="70be0-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70be0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
