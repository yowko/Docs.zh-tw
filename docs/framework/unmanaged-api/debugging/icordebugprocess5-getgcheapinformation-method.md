---
title: ICorDebugProcess5::GetGCHeapInformation 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf3d362902eb338e5d797b66c5fe2af4f3e1ae9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508323"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="467b1-102">ICorDebugProcess5::GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="467b1-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="467b1-103">提供記憶體回收堆積，包括其是否目前可列舉的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="467b1-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="467b1-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="467b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="467b1-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="467b1-106">[out]指標[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)提供記憶體回收堆積的一般資訊的值。</span><span class="sxs-lookup"><span data-stu-id="467b1-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="467b1-107">備註</span><span class="sxs-lookup"><span data-stu-id="467b1-107">Remarks</span></span>  
 <span data-ttu-id="467b1-108">`ICorDebugProcess5::GetGCHeapInformation`之前正在列舉堆積，必須呼叫方法，或個別的堆積的區域，以確保記憶體回收結構中的程序目前有效值。</span><span class="sxs-lookup"><span data-stu-id="467b1-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="467b1-109">當集合正在進行時，無法檢視過記憶體回收堆積。</span><span class="sxs-lookup"><span data-stu-id="467b1-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="467b1-110">否則，列舉型別可能會擷取無效記憶體回收結構。</span><span class="sxs-lookup"><span data-stu-id="467b1-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="467b1-111">需求</span><span class="sxs-lookup"><span data-stu-id="467b1-111">Requirements</span></span>  
 <span data-ttu-id="467b1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="467b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="467b1-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="467b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="467b1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="467b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="467b1-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="467b1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467b1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="467b1-116">See also</span></span>
- [<span data-ttu-id="467b1-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="467b1-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="467b1-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="467b1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
