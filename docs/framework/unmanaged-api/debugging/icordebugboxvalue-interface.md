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
ms.openlocfilehash: 1a9a647a9c77a3c1f82ae3691e2a5e5b2f544cad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645405"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="d4640-102">ICorDebugBoxValue 介面</span><span class="sxs-lookup"><span data-stu-id="d4640-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="d4640-103">「 ICorDebugHeapValue"，表示 boxed 實的值類別物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="d4640-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4640-104">方法</span><span class="sxs-lookup"><span data-stu-id="d4640-104">Methods</span></span>  
  
|<span data-ttu-id="d4640-105">方法</span><span class="sxs-lookup"><span data-stu-id="d4640-105">Method</span></span>|<span data-ttu-id="d4640-106">描述</span><span class="sxs-lookup"><span data-stu-id="d4640-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4640-107">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="d4640-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="d4640-108">取得 boxed"ICorDebugObjectValue 」 執行個體的介面指標。</span><span class="sxs-lookup"><span data-stu-id="d4640-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4640-109">備註</span><span class="sxs-lookup"><span data-stu-id="d4640-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4640-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d4640-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4640-111">需求</span><span class="sxs-lookup"><span data-stu-id="d4640-111">Requirements</span></span>  
 <span data-ttu-id="d4640-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4640-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4640-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4640-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4640-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4640-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4640-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4640-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4640-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4640-116">See also</span></span>

- [<span data-ttu-id="d4640-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d4640-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
