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
ms.openlocfilehash: 6d58ae048382a78c422703d5c6caeb3bbc739849
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723164"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="7e0cc-102">ICorDebugBoxValue 介面</span><span class="sxs-lookup"><span data-stu-id="7e0cc-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="7e0cc-103">"ICorDebugHeapValue" 的子類別，表示已裝箱的實值類別物件。</span><span class="sxs-lookup"><span data-stu-id="7e0cc-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e0cc-104">方法</span><span class="sxs-lookup"><span data-stu-id="7e0cc-104">Methods</span></span>  
  
|<span data-ttu-id="7e0cc-105">方法</span><span class="sxs-lookup"><span data-stu-id="7e0cc-105">Method</span></span>|<span data-ttu-id="7e0cc-106">描述</span><span class="sxs-lookup"><span data-stu-id="7e0cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e0cc-107">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="7e0cc-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="7e0cc-108">取得已封裝之 "ICorDebugObjectValue" 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="7e0cc-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e0cc-109">備註</span><span class="sxs-lookup"><span data-stu-id="7e0cc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e0cc-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7e0cc-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e0cc-111">需求</span><span class="sxs-lookup"><span data-stu-id="7e0cc-111">Requirements</span></span>  

 <span data-ttu-id="7e0cc-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e0cc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e0cc-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e0cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e0cc-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e0cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e0cc-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e0cc-116">See also</span></span>

- [<span data-ttu-id="7e0cc-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7e0cc-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
