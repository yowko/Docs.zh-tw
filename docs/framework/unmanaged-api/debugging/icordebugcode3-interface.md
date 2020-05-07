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
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893459"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="6ff95-102">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="6ff95-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="6ff95-103">提供擴充 "ICorDebugCode" 和 "ICorDebugCode2" 的方法，以提供受控傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6ff95-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ff95-104">方法</span><span class="sxs-lookup"><span data-stu-id="6ff95-104">Methods</span></span>  
  
|<span data-ttu-id="6ff95-105">方法</span><span class="sxs-lookup"><span data-stu-id="6ff95-105">Method</span></span>|<span data-ttu-id="6ff95-106">描述</span><span class="sxs-lookup"><span data-stu-id="6ff95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ff95-107">GetReturnValueLiveOffset 方法</span><span class="sxs-lookup"><span data-stu-id="6ff95-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="6ff95-108">針對指定的 IL 位移，取得應放置中斷點的原生位移，讓偵錯工具可以從函數取得傳回值。</span><span class="sxs-lookup"><span data-stu-id="6ff95-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ff95-109">備註</span><span class="sxs-lookup"><span data-stu-id="6ff95-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ff95-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6ff95-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ff95-111">需求</span><span class="sxs-lookup"><span data-stu-id="6ff95-111">Requirements</span></span>  
 <span data-ttu-id="6ff95-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff95-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ff95-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ff95-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ff95-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ff95-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ff95-115">**.NET Framework 版本：**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ff95-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff95-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ff95-116">See also</span></span>

- [<span data-ttu-id="6ff95-117">ICorDebugILFrame3 介面</span><span class="sxs-lookup"><span data-stu-id="6ff95-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="6ff95-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6ff95-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
