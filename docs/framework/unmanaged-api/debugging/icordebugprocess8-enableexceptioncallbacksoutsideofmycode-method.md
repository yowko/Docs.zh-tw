---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 2c0da899b3f6f3c229c6f5e5b4cafe48fdc19742
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792163"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="daea7-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="daea7-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="daea7-103">[在 .NET Framework 4.6 和更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="daea7-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="daea7-104">啟用或停用特定類型的[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)例外狀況回呼。</span><span class="sxs-lookup"><span data-stu-id="daea7-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daea7-105">語法</span><span class="sxs-lookup"><span data-stu-id="daea7-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daea7-106">參數</span><span class="sxs-lookup"><span data-stu-id="daea7-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="daea7-107">[in]</span><span class="sxs-lookup"><span data-stu-id="daea7-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daea7-108">備註</span><span class="sxs-lookup"><span data-stu-id="daea7-108">Remarks</span></span>  
 <span data-ttu-id="daea7-109">如果 `enableExceptionsOutsideOfJMC` 的值為 `false`：</span><span class="sxs-lookup"><span data-stu-id="daea7-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="daea7-110">DEBUG_EXCEPTION_FIRST_CHANCE 例外狀況不會導致回呼偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="daea7-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="daea7-111">如果例外狀況絕不會逸出到使用者程式碼中 (也就是從例外狀況來源到例外狀況處理常式的路徑沒有標記為 JustMyCode 或 JMC 的方法)，則 DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外狀況不會導致回呼偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="daea7-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="daea7-112">`enableExceptionsOutsideOfJMC` 的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="daea7-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daea7-113">需求</span><span class="sxs-lookup"><span data-stu-id="daea7-113">Requirements</span></span>  
 <span data-ttu-id="daea7-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="daea7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daea7-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="daea7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daea7-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daea7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daea7-117">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daea7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daea7-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="daea7-118">See also</span></span>

- [<span data-ttu-id="daea7-119">ICorDebugProcess8 介面</span><span class="sxs-lookup"><span data-stu-id="daea7-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="daea7-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="daea7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
