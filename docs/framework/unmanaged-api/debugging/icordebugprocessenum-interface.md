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
ms.openlocfilehash: c11e286d8c33d6823127d9a6d5989064e2299bc4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792135"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="0338e-102">ICorDebugProcessEnum Interface</span><span class="sxs-lookup"><span data-stu-id="0338e-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="0338e-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugProcess 陣列。</span><span class="sxs-lookup"><span data-stu-id="0338e-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0338e-104">方法</span><span class="sxs-lookup"><span data-stu-id="0338e-104">Methods</span></span>  
  
|<span data-ttu-id="0338e-105">方法</span><span class="sxs-lookup"><span data-stu-id="0338e-105">Method</span></span>|<span data-ttu-id="0338e-106">描述</span><span class="sxs-lookup"><span data-stu-id="0338e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0338e-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="0338e-107">Next Method</span></span>](icordebugprocessenum-next-method.md)|<span data-ttu-id="0338e-108">從列舉中取得指定數目的 `ICorDebugProcess` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="0338e-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0338e-109">備註</span><span class="sxs-lookup"><span data-stu-id="0338e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0338e-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0338e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0338e-111">需求</span><span class="sxs-lookup"><span data-stu-id="0338e-111">Requirements</span></span>  
 <span data-ttu-id="0338e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0338e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0338e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0338e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0338e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0338e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0338e-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0338e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0338e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0338e-116">See also</span></span>

- [<span data-ttu-id="0338e-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0338e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
