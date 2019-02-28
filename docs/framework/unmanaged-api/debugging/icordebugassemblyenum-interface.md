---
title: ICorDebugAssemblyEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b259ceb8af61785bc77536d2718bdfbb3683c066
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979888"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="58b5a-102">ICorDebugAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="58b5a-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="58b5a-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugAssembly 陣列。</span><span class="sxs-lookup"><span data-stu-id="58b5a-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58b5a-104">方法</span><span class="sxs-lookup"><span data-stu-id="58b5a-104">Methods</span></span>  
  
|<span data-ttu-id="58b5a-105">方法</span><span class="sxs-lookup"><span data-stu-id="58b5a-105">Method</span></span>|<span data-ttu-id="58b5a-106">描述</span><span class="sxs-lookup"><span data-stu-id="58b5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58b5a-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="58b5a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-next-method.md)|<span data-ttu-id="58b5a-108">取得指定的數目`ICorDebugAssembly`在列舉中，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="58b5a-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58b5a-109">備註</span><span class="sxs-lookup"><span data-stu-id="58b5a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58b5a-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="58b5a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b5a-111">需求</span><span class="sxs-lookup"><span data-stu-id="58b5a-111">Requirements</span></span>  
 <span data-ttu-id="58b5a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58b5a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58b5a-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58b5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58b5a-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58b5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58b5a-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58b5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b5a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b5a-116">See also</span></span>
- [<span data-ttu-id="58b5a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58b5a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
