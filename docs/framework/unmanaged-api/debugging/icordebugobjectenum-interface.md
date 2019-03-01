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
ms.openlocfilehash: 452216a2ba4e8013d107977d82eae1508b2aba78
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967759"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="234a0-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="234a0-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="234a0-103">實作 ICorDebugEnum 方法，並列舉物件的陣列的相對虛擬位址 (Rva)。</span><span class="sxs-lookup"><span data-stu-id="234a0-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="234a0-104">方法</span><span class="sxs-lookup"><span data-stu-id="234a0-104">Methods</span></span>  
  
|<span data-ttu-id="234a0-105">方法</span><span class="sxs-lookup"><span data-stu-id="234a0-105">Method</span></span>|<span data-ttu-id="234a0-106">描述</span><span class="sxs-lookup"><span data-stu-id="234a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="234a0-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="234a0-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="234a0-108">從列舉型別，從目前位置開始，取得指定的物件數目的 Rva。</span><span class="sxs-lookup"><span data-stu-id="234a0-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="234a0-109">備註</span><span class="sxs-lookup"><span data-stu-id="234a0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="234a0-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="234a0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="234a0-111">需求</span><span class="sxs-lookup"><span data-stu-id="234a0-111">Requirements</span></span>  
 <span data-ttu-id="234a0-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="234a0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="234a0-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="234a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="234a0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="234a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="234a0-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="234a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234a0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="234a0-116">See also</span></span>
- [<span data-ttu-id="234a0-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="234a0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
