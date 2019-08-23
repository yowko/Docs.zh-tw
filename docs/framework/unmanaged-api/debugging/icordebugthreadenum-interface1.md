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
ms.openlocfilehash: 5b7e5b0a9f4166923a559eb3886aa0f9cabbcd72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962953"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="be06c-102">ICorDebugThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="be06c-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="be06c-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugThread 陣列。</span><span class="sxs-lookup"><span data-stu-id="be06c-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be06c-104">方法</span><span class="sxs-lookup"><span data-stu-id="be06c-104">Methods</span></span>  
  
|<span data-ttu-id="be06c-105">方法</span><span class="sxs-lookup"><span data-stu-id="be06c-105">Method</span></span>|<span data-ttu-id="be06c-106">描述</span><span class="sxs-lookup"><span data-stu-id="be06c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be06c-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="be06c-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="be06c-108">從列舉中取得指定`ICorDebugThread`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="be06c-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be06c-109">備註</span><span class="sxs-lookup"><span data-stu-id="be06c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be06c-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="be06c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be06c-111">需求</span><span class="sxs-lookup"><span data-stu-id="be06c-111">Requirements</span></span>  
 <span data-ttu-id="be06c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be06c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be06c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be06c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be06c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be06c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be06c-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be06c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be06c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be06c-116">See also</span></span>

- [<span data-ttu-id="be06c-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="be06c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
