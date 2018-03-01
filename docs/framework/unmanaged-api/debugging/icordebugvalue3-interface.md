---
title: "ICorDebugValue3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6a470113dc54876937850294f6d99fc15a2cf98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="113d4-102">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="113d4-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="113d4-103">擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="113d4-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="113d4-104">方法</span><span class="sxs-lookup"><span data-stu-id="113d4-104">Methods</span></span>  
  
|<span data-ttu-id="113d4-105">方法</span><span class="sxs-lookup"><span data-stu-id="113d4-105">Method</span></span>|<span data-ttu-id="113d4-106">描述</span><span class="sxs-lookup"><span data-stu-id="113d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="113d4-107">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="113d4-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="113d4-108">取得以位元組為單位，這個大小，`ICorDebugValue3`物件。</span><span class="sxs-lookup"><span data-stu-id="113d4-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="113d4-109">備註</span><span class="sxs-lookup"><span data-stu-id="113d4-109">Remarks</span></span>  
 <span data-ttu-id="113d4-110">[Icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法會傳回物件大小，範圍從 0 到 2,147,483,647 個位元組。</span><span class="sxs-lookup"><span data-stu-id="113d4-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="113d4-111">在[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，陣列大小可以超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="113d4-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="113d4-112">`ICorDebugValue3`介面可讓您判斷這些陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="113d4-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="113d4-113">需求</span><span class="sxs-lookup"><span data-stu-id="113d4-113">Requirements</span></span>  
 <span data-ttu-id="113d4-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="113d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="113d4-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="113d4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="113d4-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="113d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="113d4-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="113d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113d4-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="113d4-118">See Also</span></span>  
    
    
 [<span data-ttu-id="113d4-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="113d4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="113d4-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="113d4-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
