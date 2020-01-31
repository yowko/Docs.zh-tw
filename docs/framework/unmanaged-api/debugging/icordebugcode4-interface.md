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
ms.openlocfilehash: 373df8a47bdcbc833ffaea05bb205a63b5f583ec
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777776"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="2384c-102">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="2384c-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="2384c-103">提供一種方法，可讓偵錯工具列舉函式中的區域變數和引數。</span><span class="sxs-lookup"><span data-stu-id="2384c-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2384c-104">方法</span><span class="sxs-lookup"><span data-stu-id="2384c-104">Methods</span></span>  
  
|<span data-ttu-id="2384c-105">方法</span><span class="sxs-lookup"><span data-stu-id="2384c-105">Method</span></span>|<span data-ttu-id="2384c-106">描述</span><span class="sxs-lookup"><span data-stu-id="2384c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2384c-107">EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="2384c-107">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="2384c-108">取得函數中區域變數和引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="2384c-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2384c-109">備註</span><span class="sxs-lookup"><span data-stu-id="2384c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2384c-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2384c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2384c-111">需求</span><span class="sxs-lookup"><span data-stu-id="2384c-111">Requirements</span></span>  
 <span data-ttu-id="2384c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2384c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2384c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2384c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2384c-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2384c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2384c-115">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2384c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2384c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2384c-116">See also</span></span>

- [<span data-ttu-id="2384c-117">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="2384c-117">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="2384c-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2384c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
