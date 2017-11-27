---
title: "ICorDebugProcess5::GetGCHeapInformation 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetGCHeapInformation
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da423914d8af20c0f942d53ed6ac9f34ace01ca9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="7f92a-102">ICorDebugProcess5::GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="7f92a-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="7f92a-103">提供有關記憶體回收堆積，包括其是否目前可列舉的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="7f92a-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f92a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f92a-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f92a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f92a-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="7f92a-106">[out]指標[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)提供記憶體回收堆積的一般資訊的值。</span><span class="sxs-lookup"><span data-stu-id="7f92a-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f92a-107">備註</span><span class="sxs-lookup"><span data-stu-id="7f92a-107">Remarks</span></span>  
 <span data-ttu-id="7f92a-108">`ICorDebugProcess5::GetGCHeapInformation`列舉堆積之前，必須呼叫方法或個別的堆積區域，以確保記憶體回收結構程序中目前有效。</span><span class="sxs-lookup"><span data-stu-id="7f92a-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="7f92a-109">集合正在進行時，就無法受到記憶體回收堆積。</span><span class="sxs-lookup"><span data-stu-id="7f92a-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="7f92a-110">否則，列舉型別可能會擷取無效的記憶體回收結構。</span><span class="sxs-lookup"><span data-stu-id="7f92a-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f92a-111">需求</span><span class="sxs-lookup"><span data-stu-id="7f92a-111">Requirements</span></span>  
 <span data-ttu-id="7f92a-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f92a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f92a-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f92a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f92a-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f92a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f92a-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f92a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f92a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f92a-116">See Also</span></span>  
 [<span data-ttu-id="7f92a-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="7f92a-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="7f92a-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7f92a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
