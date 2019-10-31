---
title: ICorDebugProcess8 介面
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: dc7de361386b9ee21d6cf05c36a7f63c3e1c25f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123361"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="b4ea9-102">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="b4ea9-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="b4ea9-103">[在 .NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="b4ea9-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="b4ea9-104">以邏輯方式擴充 ICorDebugProcess 介面，以啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="b4ea9-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4ea9-105">方法</span><span class="sxs-lookup"><span data-stu-id="b4ea9-105">Methods</span></span>  
  
|<span data-ttu-id="b4ea9-106">方法</span><span class="sxs-lookup"><span data-stu-id="b4ea9-106">Method</span></span>|<span data-ttu-id="b4ea9-107">描述</span><span class="sxs-lookup"><span data-stu-id="b4ea9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4ea9-108">EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="b4ea9-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="b4ea9-109">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="b4ea9-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4ea9-110">備註</span><span class="sxs-lookup"><span data-stu-id="b4ea9-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ea9-111">需求</span><span class="sxs-lookup"><span data-stu-id="b4ea9-111">Requirements</span></span>  
 <span data-ttu-id="b4ea9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4ea9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ea9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4ea9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4ea9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4ea9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4ea9-115">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ea9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ea9-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ea9-116">See also</span></span>

- [<span data-ttu-id="b4ea9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b4ea9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b4ea9-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="b4ea9-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
