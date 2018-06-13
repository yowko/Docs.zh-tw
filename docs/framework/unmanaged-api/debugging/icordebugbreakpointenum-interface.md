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
ms.openlocfilehash: 8299be7189522c1b508e647ae227de5d5dd68c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403314"
---
# <a name="icordebugbreakpointenum-interface1"></a><span data-ttu-id="dbaf3-102">ICorDebugBreakpointEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="dbaf3-102">ICorDebugBreakpointEnum Interface1</span></span>
<span data-ttu-id="dbaf3-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="dbaf3-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbaf3-104">方法</span><span class="sxs-lookup"><span data-stu-id="dbaf3-104">Methods</span></span>  
  
|<span data-ttu-id="dbaf3-105">方法</span><span class="sxs-lookup"><span data-stu-id="dbaf3-105">Method</span></span>|<span data-ttu-id="dbaf3-106">描述</span><span class="sxs-lookup"><span data-stu-id="dbaf3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbaf3-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="dbaf3-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="dbaf3-108">取得指定的數目`ICorDebugBreakpoint`列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbaf3-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbaf3-109">備註</span><span class="sxs-lookup"><span data-stu-id="dbaf3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbaf3-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="dbaf3-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbaf3-111">需求</span><span class="sxs-lookup"><span data-stu-id="dbaf3-111">Requirements</span></span>  
 <span data-ttu-id="dbaf3-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbaf3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbaf3-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbaf3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbaf3-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbaf3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbaf3-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbaf3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbaf3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbaf3-116">See Also</span></span>  
 [<span data-ttu-id="dbaf3-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="dbaf3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
