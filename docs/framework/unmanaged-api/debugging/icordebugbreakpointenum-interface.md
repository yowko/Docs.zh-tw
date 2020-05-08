---
title: ICorDebugBreakpointEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: e391a02571481d75ce88ae3f3b2b6421705d661c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894708"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="960f9-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="960f9-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="960f9-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="960f9-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="960f9-104">方法</span><span class="sxs-lookup"><span data-stu-id="960f9-104">Methods</span></span>  
  
|<span data-ttu-id="960f9-105">方法</span><span class="sxs-lookup"><span data-stu-id="960f9-105">Method</span></span>|<span data-ttu-id="960f9-106">描述</span><span class="sxs-lookup"><span data-stu-id="960f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="960f9-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="960f9-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="960f9-108">從列舉中取得指定`ICorDebugBreakpoint`的實例數目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="960f9-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="960f9-109">備註</span><span class="sxs-lookup"><span data-stu-id="960f9-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="960f9-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="960f9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="960f9-111">需求</span><span class="sxs-lookup"><span data-stu-id="960f9-111">Requirements</span></span>  
 <span data-ttu-id="960f9-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="960f9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="960f9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="960f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="960f9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="960f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="960f9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="960f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960f9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="960f9-116">See also</span></span>

- [<span data-ttu-id="960f9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="960f9-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
