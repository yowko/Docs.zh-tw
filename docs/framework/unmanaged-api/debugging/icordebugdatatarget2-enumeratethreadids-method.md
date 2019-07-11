---
title: ICorDebugDataTarget2::EnumerateThreadIDs 方法
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 848929901e91164bdccda5c1e77069364452a782
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750244"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="a2c69-102">ICorDebugDataTarget2::EnumerateThreadIDs 方法</span><span class="sxs-lookup"><span data-stu-id="a2c69-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="a2c69-103">傳回使用中執行緒 ID 的清單。</span><span class="sxs-lookup"><span data-stu-id="a2c69-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c69-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2c69-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c69-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2c69-105">Parameters</span></span>  
 <span data-ttu-id="a2c69-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="a2c69-106">cThreadIDs</span></span>  
 <span data-ttu-id="a2c69-107">[in] 可傳回其 ID 的執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="a2c69-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="a2c69-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="a2c69-108">pcThreadIds</span></span>  
 <span data-ttu-id="a2c69-109">[out] 表示寫入 `ULONG32` 陣列的實際執行緒 ID 數目之 `pThreadIds` 的指標。</span><span class="sxs-lookup"><span data-stu-id="a2c69-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="a2c69-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="a2c69-110">pThreadIDs</span></span>  
 <span data-ttu-id="a2c69-111">執行緒識別項的陣列。</span><span class="sxs-lookup"><span data-stu-id="a2c69-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2c69-112">備註</span><span class="sxs-lookup"><span data-stu-id="a2c69-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2c69-113">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="a2c69-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c69-114">需求</span><span class="sxs-lookup"><span data-stu-id="a2c69-114">Requirements</span></span>  
 <span data-ttu-id="a2c69-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2c69-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2c69-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2c69-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c69-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c69-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c69-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2c69-118">See also</span></span>

- [<span data-ttu-id="a2c69-119">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="a2c69-119">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="a2c69-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a2c69-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
