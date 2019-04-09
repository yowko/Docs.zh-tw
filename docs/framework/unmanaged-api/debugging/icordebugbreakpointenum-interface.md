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
ms.openlocfilehash: 7fd42f13f699b0b79fd69311186f2b2ca0c9998a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149067"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="64e30-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="64e30-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="64e30-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="64e30-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64e30-104">方法</span><span class="sxs-lookup"><span data-stu-id="64e30-104">Methods</span></span>  
  
|<span data-ttu-id="64e30-105">方法</span><span class="sxs-lookup"><span data-stu-id="64e30-105">Method</span></span>|<span data-ttu-id="64e30-106">描述</span><span class="sxs-lookup"><span data-stu-id="64e30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64e30-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="64e30-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="64e30-108">取得指定的數目`ICorDebugBreakpoint`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="64e30-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64e30-109">備註</span><span class="sxs-lookup"><span data-stu-id="64e30-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64e30-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="64e30-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e30-111">需求</span><span class="sxs-lookup"><span data-stu-id="64e30-111">Requirements</span></span>  
 <span data-ttu-id="64e30-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64e30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e30-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64e30-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64e30-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64e30-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="64e30-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="64e30-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64e30-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64e30-116">See also</span></span>

- [<span data-ttu-id="64e30-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="64e30-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
