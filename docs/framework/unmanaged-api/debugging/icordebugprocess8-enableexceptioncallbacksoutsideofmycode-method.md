---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08937e87b8bd2249b8608f8ec1ed1f7734961b3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184830"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="d63d7-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="d63d7-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="d63d7-103">[受到 [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="d63d7-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="d63d7-104">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況的回呼。</span><span class="sxs-lookup"><span data-stu-id="d63d7-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d63d7-105">語法</span><span class="sxs-lookup"><span data-stu-id="d63d7-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d63d7-106">參數</span><span class="sxs-lookup"><span data-stu-id="d63d7-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="d63d7-107">[in]</span><span class="sxs-lookup"><span data-stu-id="d63d7-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d63d7-108">備註</span><span class="sxs-lookup"><span data-stu-id="d63d7-108">Remarks</span></span>  
 <span data-ttu-id="d63d7-109">如果 `enableExceptionsOutsideOfJMC` 的值為 `false`：</span><span class="sxs-lookup"><span data-stu-id="d63d7-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
-   <span data-ttu-id="d63d7-110">DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致回呼偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d63d7-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
-   <span data-ttu-id="d63d7-111">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致回呼偵錯工具如果例外狀況絕不會逸出到使用者程式碼 （也就是從例外狀況來源到例外狀況處理常式的路徑有沒有標記為 JustMyCode 或 JMC 的方法）。</span><span class="sxs-lookup"><span data-stu-id="d63d7-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="d63d7-112">`enableExceptionsOutsideOfJMC` 的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d63d7-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d63d7-113">需求</span><span class="sxs-lookup"><span data-stu-id="d63d7-113">Requirements</span></span>  
 <span data-ttu-id="d63d7-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d63d7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d63d7-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d63d7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d63d7-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d63d7-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d63d7-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d63d7-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d63d7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d63d7-118">See also</span></span>

- [<span data-ttu-id="d63d7-119">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="d63d7-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="d63d7-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d63d7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
