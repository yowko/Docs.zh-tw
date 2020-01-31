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
ms.openlocfilehash: 703f159c5bc6b73dcd0e770bdeb61f676aae034c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792370"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="6d8ec-102">ICorDebugProcess5::GetGCHeapInformation 方法</span><span class="sxs-lookup"><span data-stu-id="6d8ec-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="6d8ec-103">提供有關垃圾收集堆積的一般資訊，包括目前是否可列舉。</span><span class="sxs-lookup"><span data-stu-id="6d8ec-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d8ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d8ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d8ec-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="6d8ec-106">脫銷提供有關垃圾收集堆積之一般資訊的[COR_HEAPINFO](cor-heapinfo-structure.md)值指標。</span><span class="sxs-lookup"><span data-stu-id="6d8ec-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d8ec-107">備註</span><span class="sxs-lookup"><span data-stu-id="6d8ec-107">Remarks</span></span>  
 <span data-ttu-id="6d8ec-108">在列舉堆積或個別堆積區域之前，必須先呼叫 `ICorDebugProcess5::GetGCHeapInformation` 方法，以確保進程中的垃圾收集結構目前有效。</span><span class="sxs-lookup"><span data-stu-id="6d8ec-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="6d8ec-109">當集合正在進行時，無法逐步執行垃圾收集堆積。</span><span class="sxs-lookup"><span data-stu-id="6d8ec-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="6d8ec-110">否則，列舉可能會捕捉到不正確垃圾收集結構。</span><span class="sxs-lookup"><span data-stu-id="6d8ec-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d8ec-111">需求</span><span class="sxs-lookup"><span data-stu-id="6d8ec-111">Requirements</span></span>  
 <span data-ttu-id="6d8ec-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d8ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d8ec-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d8ec-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d8ec-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d8ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d8ec-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d8ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8ec-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d8ec-116">See also</span></span>

- [<span data-ttu-id="6d8ec-117">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="6d8ec-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="6d8ec-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6d8ec-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
