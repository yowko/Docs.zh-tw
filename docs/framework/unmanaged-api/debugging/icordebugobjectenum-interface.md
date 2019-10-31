---
title: ICorDebugObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: b77d5859986c90d6ef61c02547014d0bec354106
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096147"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="cd610-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="cd610-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="cd610-103">會執行 ICorDebugEnum 方法，並依其相對虛擬位址（Rva）來列舉物件陣列。</span><span class="sxs-lookup"><span data-stu-id="cd610-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd610-104">方法</span><span class="sxs-lookup"><span data-stu-id="cd610-104">Methods</span></span>  
  
|<span data-ttu-id="cd610-105">方法</span><span class="sxs-lookup"><span data-stu-id="cd610-105">Method</span></span>|<span data-ttu-id="cd610-106">描述</span><span class="sxs-lookup"><span data-stu-id="cd610-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd610-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="cd610-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="cd610-108">從目前的位置開始，取得列舉中指定數目之物件的 Rva。</span><span class="sxs-lookup"><span data-stu-id="cd610-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd610-109">備註</span><span class="sxs-lookup"><span data-stu-id="cd610-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd610-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="cd610-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd610-111">需求</span><span class="sxs-lookup"><span data-stu-id="cd610-111">Requirements</span></span>  
 <span data-ttu-id="cd610-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd610-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd610-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd610-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd610-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd610-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd610-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd610-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd610-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd610-116">See also</span></span>

- [<span data-ttu-id="cd610-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="cd610-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
