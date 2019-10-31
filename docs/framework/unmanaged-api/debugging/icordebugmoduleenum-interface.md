---
title: ICorDebugModuleEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: eaf00369cf77aaa1ba16879bae1b74aba2eb9eab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123533"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="411d5-102">ICorDebugModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="411d5-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="411d5-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugModule 陣列。</span><span class="sxs-lookup"><span data-stu-id="411d5-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="411d5-104">方法</span><span class="sxs-lookup"><span data-stu-id="411d5-104">Methods</span></span>  
  
|<span data-ttu-id="411d5-105">方法</span><span class="sxs-lookup"><span data-stu-id="411d5-105">Method</span></span>|<span data-ttu-id="411d5-106">描述</span><span class="sxs-lookup"><span data-stu-id="411d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="411d5-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="411d5-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="411d5-108">從列舉中取得指定數目的 `ICorDebugModule` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="411d5-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="411d5-109">備註</span><span class="sxs-lookup"><span data-stu-id="411d5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="411d5-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="411d5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="411d5-111">需求</span><span class="sxs-lookup"><span data-stu-id="411d5-111">Requirements</span></span>  
 <span data-ttu-id="411d5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="411d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="411d5-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="411d5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="411d5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="411d5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="411d5-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="411d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411d5-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="411d5-116">See also</span></span>

- [<span data-ttu-id="411d5-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="411d5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
