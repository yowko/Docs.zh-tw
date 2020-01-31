---
title: ICorDebugCodeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: 127022fb8e9f9559ccb0f0c877d25db67eea3037
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784005"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="0b3db-102">ICorDebugCodeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="0b3db-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="0b3db-103">會執行 "ICorDebugEnum" 方法，並列舉 "ICorDebugCode" 陣列。</span><span class="sxs-lookup"><span data-stu-id="0b3db-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b3db-104">方法</span><span class="sxs-lookup"><span data-stu-id="0b3db-104">Methods</span></span>  
  
|<span data-ttu-id="0b3db-105">方法</span><span class="sxs-lookup"><span data-stu-id="0b3db-105">Method</span></span>|<span data-ttu-id="0b3db-106">描述</span><span class="sxs-lookup"><span data-stu-id="0b3db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b3db-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="0b3db-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="0b3db-108">從列舉中取得指定數目的 `ICorDebugCode` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="0b3db-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b3db-109">備註</span><span class="sxs-lookup"><span data-stu-id="0b3db-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b3db-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0b3db-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b3db-111">需求</span><span class="sxs-lookup"><span data-stu-id="0b3db-111">Requirements</span></span>  
 <span data-ttu-id="0b3db-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b3db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b3db-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b3db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b3db-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b3db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b3db-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b3db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3db-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0b3db-116">See also</span></span>

- [<span data-ttu-id="0b3db-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0b3db-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
