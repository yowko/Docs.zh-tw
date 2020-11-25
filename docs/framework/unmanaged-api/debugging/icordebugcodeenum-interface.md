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
ms.openlocfilehash: b611dcabc1e5cc36f5c6342f0a832cc81de8c1d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720733"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="24e9f-102">ICorDebugCodeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="24e9f-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="24e9f-103">會執行 "ICorDebugEnum" 方法，並列舉 "ICorDebugCode" 陣列。</span><span class="sxs-lookup"><span data-stu-id="24e9f-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24e9f-104">方法</span><span class="sxs-lookup"><span data-stu-id="24e9f-104">Methods</span></span>  
  
|<span data-ttu-id="24e9f-105">方法</span><span class="sxs-lookup"><span data-stu-id="24e9f-105">Method</span></span>|<span data-ttu-id="24e9f-106">描述</span><span class="sxs-lookup"><span data-stu-id="24e9f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24e9f-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="24e9f-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="24e9f-108">`ICorDebugCode`從目前位置開始，取得列舉的指定實例數目。</span><span class="sxs-lookup"><span data-stu-id="24e9f-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24e9f-109">備註</span><span class="sxs-lookup"><span data-stu-id="24e9f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24e9f-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="24e9f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e9f-111">需求</span><span class="sxs-lookup"><span data-stu-id="24e9f-111">Requirements</span></span>  

 <span data-ttu-id="24e9f-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24e9f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24e9f-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24e9f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24e9f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24e9f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24e9f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e9f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e9f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e9f-116">See also</span></span>

- [<span data-ttu-id="24e9f-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="24e9f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
