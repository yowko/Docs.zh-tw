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
ms.openlocfilehash: 8a373afdf41590ec44a7cbac7360719a12faa82e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720720"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="59cc8-102">ICorDebugCode4 介面</span><span class="sxs-lookup"><span data-stu-id="59cc8-102">ICorDebugCode4 Interface</span></span>

<span data-ttu-id="59cc8-103">提供方法，此方法可讓偵錯工具列舉函數中的區域變數和引數。</span><span class="sxs-lookup"><span data-stu-id="59cc8-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59cc8-104">方法</span><span class="sxs-lookup"><span data-stu-id="59cc8-104">Methods</span></span>  
  
|<span data-ttu-id="59cc8-105">方法</span><span class="sxs-lookup"><span data-stu-id="59cc8-105">Method</span></span>|<span data-ttu-id="59cc8-106">描述</span><span class="sxs-lookup"><span data-stu-id="59cc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59cc8-107">EnumerateVariableHomes 方法</span><span class="sxs-lookup"><span data-stu-id="59cc8-107">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="59cc8-108">取得函數中區域變數和引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="59cc8-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59cc8-109">備註</span><span class="sxs-lookup"><span data-stu-id="59cc8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59cc8-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="59cc8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cc8-111">需求</span><span class="sxs-lookup"><span data-stu-id="59cc8-111">Requirements</span></span>  

 <span data-ttu-id="59cc8-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59cc8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59cc8-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59cc8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59cc8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59cc8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59cc8-115">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cc8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cc8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59cc8-116">See also</span></span>

- [<span data-ttu-id="59cc8-117">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="59cc8-117">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="59cc8-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="59cc8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
