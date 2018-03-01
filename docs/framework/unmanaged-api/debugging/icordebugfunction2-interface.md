---
title: ICorDebugFunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="18234-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="18234-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="18234-103">以邏輯方式擴充 ICorDebugFunction 介面 Just My Code 逐步執行偵錯提供支援，這會略過的非使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="18234-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18234-104">方法</span><span class="sxs-lookup"><span data-stu-id="18234-104">Methods</span></span>  
  
|<span data-ttu-id="18234-105">方法</span><span class="sxs-lookup"><span data-stu-id="18234-105">Method</span></span>|<span data-ttu-id="18234-106">描述</span><span class="sxs-lookup"><span data-stu-id="18234-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18234-107">EnumerateNativeCode 方法</span><span class="sxs-lookup"><span data-stu-id="18234-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="18234-108">（尚未實作）。取得包含此 ICorDebugFunction2 物件所參考的函式中的原生程式碼陳述式 ICorDebugCodeEnum 介面指標。</span><span class="sxs-lookup"><span data-stu-id="18234-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="18234-109">GetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="18234-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="18234-110">取得值，指出是否要將此函式標記為使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="18234-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="18234-111">GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="18234-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="18234-112">取得此函式的編輯後繼續版本。</span><span class="sxs-lookup"><span data-stu-id="18234-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="18234-113">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="18234-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="18234-114">將此函式標示為 Just My Code 逐步執行。</span><span class="sxs-lookup"><span data-stu-id="18234-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18234-115">備註</span><span class="sxs-lookup"><span data-stu-id="18234-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18234-116">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="18234-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18234-117">需求</span><span class="sxs-lookup"><span data-stu-id="18234-117">Requirements</span></span>  
 <span data-ttu-id="18234-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18234-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18234-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18234-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18234-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18234-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18234-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18234-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18234-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="18234-122">See Also</span></span>  
 [<span data-ttu-id="18234-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="18234-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
