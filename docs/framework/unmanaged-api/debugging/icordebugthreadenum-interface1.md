---
title: ICorDebugThreadEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7edf103e397c6e3e1577b5ed4bc8fc0df264b843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993846"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="a7437-102">ICorDebugThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a7437-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="a7437-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugThread 陣列。</span><span class="sxs-lookup"><span data-stu-id="a7437-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7437-104">方法</span><span class="sxs-lookup"><span data-stu-id="a7437-104">Methods</span></span>  
  
|<span data-ttu-id="a7437-105">方法</span><span class="sxs-lookup"><span data-stu-id="a7437-105">Method</span></span>|<span data-ttu-id="a7437-106">描述</span><span class="sxs-lookup"><span data-stu-id="a7437-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7437-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="a7437-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="a7437-108">取得指定的數目`ICorDebugThread`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a7437-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7437-109">備註</span><span class="sxs-lookup"><span data-stu-id="a7437-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7437-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a7437-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7437-111">需求</span><span class="sxs-lookup"><span data-stu-id="a7437-111">Requirements</span></span>  
 <span data-ttu-id="a7437-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7437-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7437-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7437-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7437-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7437-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7437-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7437-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7437-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7437-116">See also</span></span>

- [<span data-ttu-id="a7437-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a7437-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
