---
title: ICorDebugDataTarget2::EnumerateThreadIDs 方法
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 4a65b76f384cdad68cba75af524dbe672c309624
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976482"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="45954-102">ICorDebugDataTarget2::EnumerateThreadIDs 方法</span><span class="sxs-lookup"><span data-stu-id="45954-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="45954-103">傳回使用中執行緒 ID 的清單。</span><span class="sxs-lookup"><span data-stu-id="45954-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45954-104">語法</span><span class="sxs-lookup"><span data-stu-id="45954-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45954-105">參數</span><span class="sxs-lookup"><span data-stu-id="45954-105">Parameters</span></span>  
 <span data-ttu-id="45954-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="45954-106">cThreadIDs</span></span>  
 <span data-ttu-id="45954-107">[in] 可傳回其 ID 的執行緒最大數目。</span><span class="sxs-lookup"><span data-stu-id="45954-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="45954-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="45954-108">pcThreadIds</span></span>  
 <span data-ttu-id="45954-109">[out] 表示寫入 `ULONG32` 陣列的實際執行緒 ID 數目之 `pThreadIds` 的指標。</span><span class="sxs-lookup"><span data-stu-id="45954-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="45954-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="45954-110">pThreadIDs</span></span>  
 <span data-ttu-id="45954-111">執行緒識別項的陣列。</span><span class="sxs-lookup"><span data-stu-id="45954-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45954-112">備註</span><span class="sxs-lookup"><span data-stu-id="45954-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45954-113">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="45954-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45954-114">需求</span><span class="sxs-lookup"><span data-stu-id="45954-114">Requirements</span></span>  
 <span data-ttu-id="45954-115">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。**標頭：** Cordebug.h .idl，Cordebug.h。h</span><span class="sxs-lookup"><span data-stu-id="45954-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45954-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45954-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45954-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45954-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45954-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45954-118">See also</span></span>

- [<span data-ttu-id="45954-119">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="45954-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="45954-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="45954-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
