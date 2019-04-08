---
title: ICorDebugFunction2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 159cebc76f732629ed84a3b6c9041cc15f8bbb69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199371"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="ed821-102">ICorDebugFunction2 介面</span><span class="sxs-lookup"><span data-stu-id="ed821-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="ed821-103">以邏輯方式擴充 ICorDebugFunction 介面以支援 Just My Code 逐步執行偵錯，這會略過非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed821-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed821-104">方法</span><span class="sxs-lookup"><span data-stu-id="ed821-104">Methods</span></span>  
  
|<span data-ttu-id="ed821-105">方法</span><span class="sxs-lookup"><span data-stu-id="ed821-105">Method</span></span>|<span data-ttu-id="ed821-106">描述</span><span class="sxs-lookup"><span data-stu-id="ed821-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed821-107">EnumerateNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="ed821-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="ed821-108">（尚未實作）。取得包含此 ICorDebugFunction2 物件所參考的函式中的原生程式碼陳述式 ICorDebugCodeEnum 介面指標。</span><span class="sxs-lookup"><span data-stu-id="ed821-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="ed821-109">GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="ed821-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="ed821-110">取得值，指出是否要將此函式標記為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed821-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="ed821-111">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="ed821-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="ed821-112">取得此函式的 編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="ed821-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="ed821-113">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="ed821-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="ed821-114">將此函式標示為 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="ed821-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed821-115">備註</span><span class="sxs-lookup"><span data-stu-id="ed821-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed821-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ed821-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed821-117">需求</span><span class="sxs-lookup"><span data-stu-id="ed821-117">Requirements</span></span>  
 <span data-ttu-id="ed821-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed821-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed821-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed821-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed821-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed821-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ed821-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ed821-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ed821-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed821-122">See also</span></span>

- [<span data-ttu-id="ed821-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ed821-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
