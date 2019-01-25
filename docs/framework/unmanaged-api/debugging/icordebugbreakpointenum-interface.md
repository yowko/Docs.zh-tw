---
title: ICorDebugBreakpointEnum Interface1
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
ms.openlocfilehash: 508cb9b4b2ff13a58f1313b958acd7b043741848
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642931"
---
# <a name="icordebugbreakpointenum-interface1"></a><span data-ttu-id="44ac9-102">ICorDebugBreakpointEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="44ac9-102">ICorDebugBreakpointEnum Interface1</span></span>
<span data-ttu-id="44ac9-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="44ac9-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44ac9-104">方法</span><span class="sxs-lookup"><span data-stu-id="44ac9-104">Methods</span></span>  
  
|<span data-ttu-id="44ac9-105">方法</span><span class="sxs-lookup"><span data-stu-id="44ac9-105">Method</span></span>|<span data-ttu-id="44ac9-106">描述</span><span class="sxs-lookup"><span data-stu-id="44ac9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44ac9-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="44ac9-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="44ac9-108">取得指定的數目`ICorDebugBreakpoint`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="44ac9-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44ac9-109">備註</span><span class="sxs-lookup"><span data-stu-id="44ac9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44ac9-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="44ac9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ac9-111">需求</span><span class="sxs-lookup"><span data-stu-id="44ac9-111">Requirements</span></span>  
 <span data-ttu-id="44ac9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44ac9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44ac9-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44ac9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44ac9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44ac9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44ac9-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ac9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ac9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44ac9-116">See also</span></span>
- [<span data-ttu-id="44ac9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="44ac9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
