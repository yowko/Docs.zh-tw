---
title: "ICorDebugProcess8 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8fba6d04a3d91cf51ce843230a36b1844a400381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="d9c35-102">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="d9c35-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="d9c35-103">[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="d9c35-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="d9c35-104">以邏輯方式擴充 ICorDebugProcess 介面，啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="d9c35-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9c35-105">方法</span><span class="sxs-lookup"><span data-stu-id="d9c35-105">Methods</span></span>  
  
|<span data-ttu-id="d9c35-106">方法</span><span class="sxs-lookup"><span data-stu-id="d9c35-106">Method</span></span>|<span data-ttu-id="d9c35-107">說明</span><span class="sxs-lookup"><span data-stu-id="d9c35-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9c35-108">EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="d9c35-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="d9c35-109">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="d9c35-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9c35-110">備註</span><span class="sxs-lookup"><span data-stu-id="d9c35-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9c35-111">需求</span><span class="sxs-lookup"><span data-stu-id="d9c35-111">Requirements</span></span>  
 <span data-ttu-id="d9c35-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9c35-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9c35-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9c35-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9c35-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9c35-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9c35-115">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9c35-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c35-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c35-116">See Also</span></span>  
 [<span data-ttu-id="d9c35-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d9c35-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d9c35-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="d9c35-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
