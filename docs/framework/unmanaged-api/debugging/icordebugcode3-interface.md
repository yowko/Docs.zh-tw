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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: febfe7df52a0c1f44cb156faf2da310d317e01a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411321"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="98cd8-102">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="98cd8-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="98cd8-103">提供方法，以擴充 「 ICorDebugCode"和"ICorDebugCode2 」 提供 managed 傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="98cd8-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98cd8-104">方法</span><span class="sxs-lookup"><span data-stu-id="98cd8-104">Methods</span></span>  
  
|<span data-ttu-id="98cd8-105">方法</span><span class="sxs-lookup"><span data-stu-id="98cd8-105">Method</span></span>|<span data-ttu-id="98cd8-106">描述</span><span class="sxs-lookup"><span data-stu-id="98cd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98cd8-107">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="98cd8-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="98cd8-108">針對指定的 IL 位移，取得原生位移中斷點放置的位置，讓偵錯工具可以從函式取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="98cd8-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98cd8-109">備註</span><span class="sxs-lookup"><span data-stu-id="98cd8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98cd8-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="98cd8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98cd8-111">需求</span><span class="sxs-lookup"><span data-stu-id="98cd8-111">Requirements</span></span>  
 <span data-ttu-id="98cd8-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98cd8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98cd8-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98cd8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98cd8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98cd8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98cd8-115">**.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98cd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cd8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98cd8-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="98cd8-117">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="98cd8-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="98cd8-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="98cd8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
