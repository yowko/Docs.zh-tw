---
title: "ICorDebugCode4 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30c0599e183d51030ac5b063a2aca4352ad95eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="69477-102">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="69477-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="69477-103">提供方法，以允許列舉的本機變數和引數的函式中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="69477-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69477-104">方法</span><span class="sxs-lookup"><span data-stu-id="69477-104">Methods</span></span>  
  
|<span data-ttu-id="69477-105">方法</span><span class="sxs-lookup"><span data-stu-id="69477-105">Method</span></span>|<span data-ttu-id="69477-106">描述</span><span class="sxs-lookup"><span data-stu-id="69477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69477-107">EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="69477-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="69477-108">取得列舉值的本機變數和引數的函式中。</span><span class="sxs-lookup"><span data-stu-id="69477-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69477-109">備註</span><span class="sxs-lookup"><span data-stu-id="69477-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69477-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="69477-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69477-111">需求</span><span class="sxs-lookup"><span data-stu-id="69477-111">Requirements</span></span>  
 <span data-ttu-id="69477-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69477-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69477-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69477-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69477-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69477-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69477-115">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69477-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69477-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="69477-116">See Also</span></span>  
    
    
 [<span data-ttu-id="69477-117">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="69477-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="69477-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="69477-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
