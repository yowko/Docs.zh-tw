---
title: ICorDebugProcessEnum Interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3651a4be94fa624d0dd6ab64b8c3f8169945de0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987619"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="54bef-102">ICorDebugProcessEnum Interface</span><span class="sxs-lookup"><span data-stu-id="54bef-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="54bef-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugProcess 陣列。</span><span class="sxs-lookup"><span data-stu-id="54bef-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54bef-104">方法</span><span class="sxs-lookup"><span data-stu-id="54bef-104">Methods</span></span>  
  
|<span data-ttu-id="54bef-105">方法</span><span class="sxs-lookup"><span data-stu-id="54bef-105">Method</span></span>|<span data-ttu-id="54bef-106">描述</span><span class="sxs-lookup"><span data-stu-id="54bef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54bef-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="54bef-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="54bef-108">取得指定的數目`ICorDebugProcess`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="54bef-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54bef-109">備註</span><span class="sxs-lookup"><span data-stu-id="54bef-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54bef-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="54bef-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54bef-111">需求</span><span class="sxs-lookup"><span data-stu-id="54bef-111">Requirements</span></span>  
 <span data-ttu-id="54bef-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54bef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54bef-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54bef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54bef-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54bef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54bef-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54bef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54bef-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54bef-116">See also</span></span>

- [<span data-ttu-id="54bef-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="54bef-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
