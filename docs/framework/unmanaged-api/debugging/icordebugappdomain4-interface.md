---
title: ICorDebugAppDomain4 介面
ms.date: 03/30/2017
ms.assetid: c536b9dc-148e-4924-bde1-1daa98d49d90
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c6077f16f07c5f1fc76b6525ccb036aa1e4fa06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099296"
---
# <a name="icordebugappdomain4-interface"></a><span data-ttu-id="df7e9-102">ICorDebugAppDomain4 介面</span><span class="sxs-lookup"><span data-stu-id="df7e9-102">ICorDebugAppDomain4 Interface</span></span>
<span data-ttu-id="df7e9-103">以邏輯方式擴充 ICorDebugAppDomain 介面，以從 COM 可呼叫包裝函式取得 managed 的物件。</span><span class="sxs-lookup"><span data-stu-id="df7e9-103">Logically extends the ICorDebugAppDomain interface to get a managed object from a COM callable wrapper.</span></span>  
  
## <a name="method"></a><span data-ttu-id="df7e9-104">方法</span><span class="sxs-lookup"><span data-stu-id="df7e9-104">Method</span></span>  
  
|<span data-ttu-id="df7e9-105">方法</span><span class="sxs-lookup"><span data-stu-id="df7e9-105">Method</span></span>|<span data-ttu-id="df7e9-106">描述</span><span class="sxs-lookup"><span data-stu-id="df7e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df7e9-107">GetObjectForCCW 方法</span><span class="sxs-lookup"><span data-stu-id="df7e9-107">GetObjectForCCW Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-getobjectforccw-method.md)|<span data-ttu-id="df7e9-108">從 COM 可呼叫包裝函式 (CCW) 指標取得 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="df7e9-108">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df7e9-109">備註</span><span class="sxs-lookup"><span data-stu-id="df7e9-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df7e9-110">需求</span><span class="sxs-lookup"><span data-stu-id="df7e9-110">Requirements</span></span>  
 <span data-ttu-id="df7e9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df7e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df7e9-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df7e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df7e9-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df7e9-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="df7e9-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="df7e9-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="df7e9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df7e9-115">See also</span></span>

- [<span data-ttu-id="df7e9-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="df7e9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="df7e9-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="df7e9-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
