---
title: ICorDebugProcess8 介面
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ee7cae6f226993b0366ba34afa853e432e2e50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547981"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="02a73-102">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="02a73-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="02a73-103">[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="02a73-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="02a73-104">以邏輯方式擴充 ICorDebugProcess 介面，啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="02a73-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02a73-105">方法</span><span class="sxs-lookup"><span data-stu-id="02a73-105">Methods</span></span>  
  
|<span data-ttu-id="02a73-106">方法</span><span class="sxs-lookup"><span data-stu-id="02a73-106">Method</span></span>|<span data-ttu-id="02a73-107">描述</span><span class="sxs-lookup"><span data-stu-id="02a73-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02a73-108">EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="02a73-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="02a73-109">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="02a73-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02a73-110">備註</span><span class="sxs-lookup"><span data-stu-id="02a73-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02a73-111">需求</span><span class="sxs-lookup"><span data-stu-id="02a73-111">Requirements</span></span>  
 <span data-ttu-id="02a73-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02a73-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02a73-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02a73-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02a73-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02a73-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02a73-115">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02a73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a73-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02a73-116">See also</span></span>
- [<span data-ttu-id="02a73-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="02a73-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="02a73-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="02a73-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
