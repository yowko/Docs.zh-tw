---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123382"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="63598-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="63598-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="63598-103">[在 .NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="63598-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="63598-104">啟用或停用特定類型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="63598-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63598-105">語法</span><span class="sxs-lookup"><span data-stu-id="63598-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63598-106">參數</span><span class="sxs-lookup"><span data-stu-id="63598-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="63598-107">[in]</span><span class="sxs-lookup"><span data-stu-id="63598-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63598-108">備註</span><span class="sxs-lookup"><span data-stu-id="63598-108">Remarks</span></span>  
 <span data-ttu-id="63598-109">如果 `enableExceptionsOutsideOfJMC` 的值為 `false`：</span><span class="sxs-lookup"><span data-stu-id="63598-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="63598-110">DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致偵錯工具的回呼。</span><span class="sxs-lookup"><span data-stu-id="63598-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="63598-111">如果例外狀況絕對不會在使用者程式碼中進行轉義（也就是從例外狀況來源到例外狀況處理常式的路徑沒有標記為 JustMyCode 或 JMC 的方法），則 DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致偵錯工具的回呼。</span><span class="sxs-lookup"><span data-stu-id="63598-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="63598-112">`enableExceptionsOutsideOfJMC` 的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="63598-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63598-113">需求</span><span class="sxs-lookup"><span data-stu-id="63598-113">Requirements</span></span>  
 <span data-ttu-id="63598-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63598-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63598-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63598-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63598-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63598-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63598-117">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63598-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63598-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="63598-118">See also</span></span>

- [<span data-ttu-id="63598-119">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="63598-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="63598-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="63598-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
