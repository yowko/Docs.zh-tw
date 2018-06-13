---
title: ICorDebugObjectEnum Interface1
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
ms.openlocfilehash: 3674643d5590c320bddd5a0e6f1f95814e07ecf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420199"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="eda9d-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="eda9d-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="eda9d-103">實作 ICorDebugEnum 方法，並依相對虛擬位址 （rva） 來列舉物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="eda9d-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eda9d-104">方法</span><span class="sxs-lookup"><span data-stu-id="eda9d-104">Methods</span></span>  
  
|<span data-ttu-id="eda9d-105">方法</span><span class="sxs-lookup"><span data-stu-id="eda9d-105">Method</span></span>|<span data-ttu-id="eda9d-106">描述</span><span class="sxs-lookup"><span data-stu-id="eda9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eda9d-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="eda9d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="eda9d-108">從列舉型別，從目前位置開始，取得指定的物件數目的 Rva。</span><span class="sxs-lookup"><span data-stu-id="eda9d-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eda9d-109">備註</span><span class="sxs-lookup"><span data-stu-id="eda9d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eda9d-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="eda9d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda9d-111">需求</span><span class="sxs-lookup"><span data-stu-id="eda9d-111">Requirements</span></span>  
 <span data-ttu-id="eda9d-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eda9d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda9d-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eda9d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eda9d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eda9d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eda9d-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eda9d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda9d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eda9d-116">See Also</span></span>  
 [<span data-ttu-id="eda9d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eda9d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
