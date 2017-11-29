---
title: "ICorDebugDataTarget2::EnumerateThreadIDs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c20b7dd1bcbc27edb9be11419b7919250301d488
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="485b5-102">ICorDebugDataTarget2::EnumerateThreadIDs 方法</span><span class="sxs-lookup"><span data-stu-id="485b5-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="485b5-103">傳回使用中執行緒 ID 的清單。</span><span class="sxs-lookup"><span data-stu-id="485b5-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="485b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="485b5-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="485b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="485b5-105">Parameters</span></span>  
 <span data-ttu-id="485b5-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="485b5-106">cThreadIDs</span></span>  
 <span data-ttu-id="485b5-107">[in] 可傳回其 ID 的執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="485b5-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="485b5-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="485b5-108">pcThreadIds</span></span>  
 <span data-ttu-id="485b5-109">[out] 表示寫入 `ULONG32` 陣列的實際執行緒 ID 數目之 `pThreadIds` 的指標。</span><span class="sxs-lookup"><span data-stu-id="485b5-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="485b5-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="485b5-110">pThreadIDs</span></span>  
 <span data-ttu-id="485b5-111">執行緒識別項的陣列。</span><span class="sxs-lookup"><span data-stu-id="485b5-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="485b5-112">備註</span><span class="sxs-lookup"><span data-stu-id="485b5-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="485b5-113">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="485b5-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="485b5-114">需求</span><span class="sxs-lookup"><span data-stu-id="485b5-114">Requirements</span></span>  
 <span data-ttu-id="485b5-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="485b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="485b5-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="485b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="485b5-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="485b5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485b5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="485b5-118">See Also</span></span>  
 [<span data-ttu-id="485b5-119">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="485b5-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="485b5-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="485b5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
