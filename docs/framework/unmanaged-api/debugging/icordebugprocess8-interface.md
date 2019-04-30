---
title: ICorDebugProcess8 介面
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 349e0cf93a981a2c598d02f67978e524a6763728
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948573"
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="0c17d-102">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="0c17d-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="0c17d-103">[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="0c17d-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="0c17d-104">以邏輯方式擴充 ICorDebugProcess 介面，啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="0c17d-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c17d-105">方法</span><span class="sxs-lookup"><span data-stu-id="0c17d-105">Methods</span></span>  
  
|<span data-ttu-id="0c17d-106">方法</span><span class="sxs-lookup"><span data-stu-id="0c17d-106">Method</span></span>|<span data-ttu-id="0c17d-107">描述</span><span class="sxs-lookup"><span data-stu-id="0c17d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c17d-108">EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="0c17d-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="0c17d-109">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="0c17d-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c17d-110">備註</span><span class="sxs-lookup"><span data-stu-id="0c17d-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c17d-111">需求</span><span class="sxs-lookup"><span data-stu-id="0c17d-111">Requirements</span></span>  
 <span data-ttu-id="0c17d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c17d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c17d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c17d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c17d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c17d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c17d-115">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c17d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c17d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c17d-116">See also</span></span>

- [<span data-ttu-id="0c17d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0c17d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0c17d-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="0c17d-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
