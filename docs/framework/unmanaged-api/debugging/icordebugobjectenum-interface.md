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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0144539987f14bed83bfc9eab2f5ca26d2a609ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942385"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="d1f73-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d1f73-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="d1f73-103">實作 ICorDebugEnum 方法，並列舉物件的陣列的相對虛擬位址 (Rva)。</span><span class="sxs-lookup"><span data-stu-id="d1f73-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1f73-104">方法</span><span class="sxs-lookup"><span data-stu-id="d1f73-104">Methods</span></span>  
  
|<span data-ttu-id="d1f73-105">方法</span><span class="sxs-lookup"><span data-stu-id="d1f73-105">Method</span></span>|<span data-ttu-id="d1f73-106">描述</span><span class="sxs-lookup"><span data-stu-id="d1f73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1f73-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="d1f73-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="d1f73-108">從列舉型別，從目前位置開始，取得指定的物件數目的 Rva。</span><span class="sxs-lookup"><span data-stu-id="d1f73-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1f73-109">備註</span><span class="sxs-lookup"><span data-stu-id="d1f73-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1f73-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d1f73-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1f73-111">需求</span><span class="sxs-lookup"><span data-stu-id="d1f73-111">Requirements</span></span>  
 <span data-ttu-id="d1f73-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1f73-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1f73-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1f73-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1f73-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1f73-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1f73-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1f73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f73-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1f73-116">See also</span></span>

- [<span data-ttu-id="d1f73-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d1f73-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
