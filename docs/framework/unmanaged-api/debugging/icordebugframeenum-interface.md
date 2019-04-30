---
title: ICorDebugFrameEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd24dfa6771ca450e79b4b932735968ecc51fc90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995783"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="66777-102">ICorDebugFrameEnum 介面</span><span class="sxs-lookup"><span data-stu-id="66777-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="66777-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugFrame 陣列。</span><span class="sxs-lookup"><span data-stu-id="66777-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66777-104">方法</span><span class="sxs-lookup"><span data-stu-id="66777-104">Methods</span></span>  
  
|<span data-ttu-id="66777-105">方法</span><span class="sxs-lookup"><span data-stu-id="66777-105">Method</span></span>|<span data-ttu-id="66777-106">描述</span><span class="sxs-lookup"><span data-stu-id="66777-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66777-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="66777-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="66777-108">取得指定的數目`ICorDebugFrame`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="66777-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66777-109">備註</span><span class="sxs-lookup"><span data-stu-id="66777-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66777-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="66777-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66777-111">需求</span><span class="sxs-lookup"><span data-stu-id="66777-111">Requirements</span></span>  
 <span data-ttu-id="66777-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66777-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66777-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66777-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66777-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66777-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66777-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66777-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66777-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66777-116">See also</span></span>

- [<span data-ttu-id="66777-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="66777-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
