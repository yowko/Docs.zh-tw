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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b5268eb4240f7c3ff254f4d3d9a13ab494530a1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968734"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="0b222-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="0b222-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="0b222-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="0b222-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b222-104">方法</span><span class="sxs-lookup"><span data-stu-id="0b222-104">Methods</span></span>  
  
|<span data-ttu-id="0b222-105">方法</span><span class="sxs-lookup"><span data-stu-id="0b222-105">Method</span></span>|<span data-ttu-id="0b222-106">描述</span><span class="sxs-lookup"><span data-stu-id="0b222-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b222-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="0b222-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="0b222-108">取得指定的數目`ICorDebugBreakpoint`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0b222-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b222-109">備註</span><span class="sxs-lookup"><span data-stu-id="0b222-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b222-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b222-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b222-111">需求</span><span class="sxs-lookup"><span data-stu-id="0b222-111">Requirements</span></span>  
 <span data-ttu-id="0b222-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b222-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b222-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b222-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b222-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b222-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b222-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b222-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b222-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b222-116">See also</span></span>
- [<span data-ttu-id="0b222-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0b222-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
