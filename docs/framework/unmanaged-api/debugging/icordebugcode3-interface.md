---
title: ICorDebugCode3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: f2f75c3c54c0fa2d55dc0179c05e4edea6e36738
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777820"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="ecea5-102">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="ecea5-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="ecea5-103">提供擴充 "ICorDebugCode" 和 "ICorDebugCode2" 的方法，以提供受控傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ecea5-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ecea5-104">方法</span><span class="sxs-lookup"><span data-stu-id="ecea5-104">Methods</span></span>  
  
|<span data-ttu-id="ecea5-105">方法</span><span class="sxs-lookup"><span data-stu-id="ecea5-105">Method</span></span>|<span data-ttu-id="ecea5-106">描述</span><span class="sxs-lookup"><span data-stu-id="ecea5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ecea5-107">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="ecea5-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="ecea5-108">針對指定的 IL 位移，取得應放置中斷點的原生位移，讓偵錯工具可以從函數取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="ecea5-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecea5-109">備註</span><span class="sxs-lookup"><span data-stu-id="ecea5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecea5-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ecea5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecea5-111">需求</span><span class="sxs-lookup"><span data-stu-id="ecea5-111">Requirements</span></span>  
 <span data-ttu-id="ecea5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ecea5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecea5-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ecea5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecea5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecea5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecea5-115">**.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecea5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecea5-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ecea5-116">See also</span></span>

- [<span data-ttu-id="ecea5-117">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="ecea5-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="ecea5-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ecea5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
