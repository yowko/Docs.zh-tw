---
title: ICorDebugBoxValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7238574334b599c7922693c7e9a476a51785491
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967318"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="272fb-102">ICorDebugBoxValue 介面</span><span class="sxs-lookup"><span data-stu-id="272fb-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="272fb-103">「 ICorDebugHeapValue"，表示 boxed 實的值類別物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="272fb-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="272fb-104">方法</span><span class="sxs-lookup"><span data-stu-id="272fb-104">Methods</span></span>  
  
|<span data-ttu-id="272fb-105">方法</span><span class="sxs-lookup"><span data-stu-id="272fb-105">Method</span></span>|<span data-ttu-id="272fb-106">描述</span><span class="sxs-lookup"><span data-stu-id="272fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="272fb-107">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="272fb-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="272fb-108">取得 boxed"ICorDebugObjectValue 」 執行個體的介面指標。</span><span class="sxs-lookup"><span data-stu-id="272fb-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="272fb-109">備註</span><span class="sxs-lookup"><span data-stu-id="272fb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="272fb-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="272fb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="272fb-111">需求</span><span class="sxs-lookup"><span data-stu-id="272fb-111">Requirements</span></span>  
 <span data-ttu-id="272fb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="272fb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="272fb-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="272fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="272fb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="272fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="272fb-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="272fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="272fb-116">See also</span></span>
- [<span data-ttu-id="272fb-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="272fb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
