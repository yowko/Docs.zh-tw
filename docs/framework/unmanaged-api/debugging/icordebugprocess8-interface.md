---
title: ICorDebugProcess8 介面
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 349e0cf93a981a2c598d02f67978e524a6763728
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119544"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="54f0b-102">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="54f0b-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="54f0b-103">[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="54f0b-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="54f0b-104">以邏輯方式擴充 ICorDebugProcess 介面，啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="54f0b-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54f0b-105">方法</span><span class="sxs-lookup"><span data-stu-id="54f0b-105">Methods</span></span>  
  
|<span data-ttu-id="54f0b-106">方法</span><span class="sxs-lookup"><span data-stu-id="54f0b-106">Method</span></span>|<span data-ttu-id="54f0b-107">描述</span><span class="sxs-lookup"><span data-stu-id="54f0b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54f0b-108">EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="54f0b-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="54f0b-109">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="54f0b-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54f0b-110">備註</span><span class="sxs-lookup"><span data-stu-id="54f0b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54f0b-111">需求</span><span class="sxs-lookup"><span data-stu-id="54f0b-111">Requirements</span></span>  
 <span data-ttu-id="54f0b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54f0b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54f0b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54f0b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54f0b-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54f0b-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="54f0b-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="54f0b-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="54f0b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54f0b-116">See also</span></span>

- [<span data-ttu-id="54f0b-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="54f0b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="54f0b-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="54f0b-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
