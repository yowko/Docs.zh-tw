---
title: ICorDebugCode4 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: 6c74a6c371ababb21bfda9b8dd2910d6a7881e6a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125533"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="f8482-102">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="f8482-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="f8482-103">提供一種方法，可讓偵錯工具列舉函式中的區域變數和引數。</span><span class="sxs-lookup"><span data-stu-id="f8482-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8482-104">方法</span><span class="sxs-lookup"><span data-stu-id="f8482-104">Methods</span></span>  
  
|<span data-ttu-id="f8482-105">方法</span><span class="sxs-lookup"><span data-stu-id="f8482-105">Method</span></span>|<span data-ttu-id="f8482-106">描述</span><span class="sxs-lookup"><span data-stu-id="f8482-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8482-107">EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="f8482-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="f8482-108">取得函數中區域變數和引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f8482-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8482-109">備註</span><span class="sxs-lookup"><span data-stu-id="f8482-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8482-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f8482-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8482-111">需求</span><span class="sxs-lookup"><span data-stu-id="f8482-111">Requirements</span></span>  
 <span data-ttu-id="f8482-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8482-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8482-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8482-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8482-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8482-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8482-115">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8482-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8482-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8482-116">See also</span></span>

- [<span data-ttu-id="f8482-117">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="f8482-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="f8482-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f8482-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
