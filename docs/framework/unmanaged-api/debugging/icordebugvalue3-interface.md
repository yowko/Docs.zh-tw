---
title: "ICorDebugValue3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3
helpviewer_keywords: ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3948a4c404036235767f8de6747966709b75bc4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="553af-102">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="553af-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="553af-103">擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="553af-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="553af-104">方法</span><span class="sxs-lookup"><span data-stu-id="553af-104">Methods</span></span>  
  
|<span data-ttu-id="553af-105">方法</span><span class="sxs-lookup"><span data-stu-id="553af-105">Method</span></span>|<span data-ttu-id="553af-106">說明</span><span class="sxs-lookup"><span data-stu-id="553af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="553af-107">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="553af-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="553af-108">取得以位元組為單位，這個大小，`ICorDebugValue3`物件。</span><span class="sxs-lookup"><span data-stu-id="553af-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="553af-109">備註</span><span class="sxs-lookup"><span data-stu-id="553af-109">Remarks</span></span>  
 <span data-ttu-id="553af-110">[Icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法會傳回物件大小，範圍從 0 到 2,147,483,647 個位元組。</span><span class="sxs-lookup"><span data-stu-id="553af-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="553af-111">在[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，陣列大小可以超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="553af-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="553af-112">`ICorDebugValue3`介面可讓您判斷這些陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="553af-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="553af-113">需求</span><span class="sxs-lookup"><span data-stu-id="553af-113">Requirements</span></span>  
 <span data-ttu-id="553af-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="553af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="553af-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="553af-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="553af-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="553af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="553af-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="553af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553af-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="553af-118">See Also</span></span>  
    
    
 [<span data-ttu-id="553af-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="553af-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="553af-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="553af-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
