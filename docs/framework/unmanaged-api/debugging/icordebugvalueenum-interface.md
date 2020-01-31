---
title: ICorDebugValueEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
ms.openlocfilehash: ba61df045caa117acae3756eb879cf67d0791222
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791058"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="e787a-102">ICorDebugValueEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e787a-102">ICorDebugValueEnum Interface</span></span>
<span data-ttu-id="e787a-103">會執行 "ICorDebugEnum" 方法，並列舉 "ICorDebugValue" 陣列。</span><span class="sxs-lookup"><span data-stu-id="e787a-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e787a-104">方法</span><span class="sxs-lookup"><span data-stu-id="e787a-104">Methods</span></span>  
  
|<span data-ttu-id="e787a-105">方法</span><span class="sxs-lookup"><span data-stu-id="e787a-105">Method</span></span>|<span data-ttu-id="e787a-106">描述</span><span class="sxs-lookup"><span data-stu-id="e787a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e787a-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="e787a-107">Next Method</span></span>](icordebugvalueenum-next-method.md)|<span data-ttu-id="e787a-108">從列舉中取得指定數目的 `ICorDebugValue` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="e787a-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e787a-109">備註</span><span class="sxs-lookup"><span data-stu-id="e787a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e787a-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e787a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e787a-111">需求</span><span class="sxs-lookup"><span data-stu-id="e787a-111">Requirements</span></span>  
 <span data-ttu-id="e787a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e787a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e787a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e787a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e787a-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e787a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e787a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e787a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e787a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e787a-116">See also</span></span>

- [<span data-ttu-id="e787a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e787a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
