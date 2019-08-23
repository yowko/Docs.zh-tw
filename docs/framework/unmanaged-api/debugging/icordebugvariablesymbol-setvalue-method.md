---
title: ICorDebugVariableSymbol::SetValue Method
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5436f56d3dcad7de3df2296485b0a36e5b3cfd79
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967971"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="06e4a-102">ICorDebugVariableSymbol::SetValue Method</span><span class="sxs-lookup"><span data-stu-id="06e4a-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="06e4a-103">指派位元組陣列的值給變數。</span><span class="sxs-lookup"><span data-stu-id="06e4a-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="06e4a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06e4a-105">參數</span><span class="sxs-lookup"><span data-stu-id="06e4a-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="06e4a-106">[in] 變數中要設定該值的開始位移。</span><span class="sxs-lookup"><span data-stu-id="06e4a-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="06e4a-107">寫入物件中的成員欄位時，會使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="06e4a-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="06e4a-108">[in] 執行緒識別碼，此執行緒的內容必須更新，以反映新的值。</span><span class="sxs-lookup"><span data-stu-id="06e4a-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="06e4a-109">[in] 以位元組為單位的執行緒內容大小。</span><span class="sxs-lookup"><span data-stu-id="06e4a-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="06e4a-110">[in] 用來將值寫入的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="06e4a-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="06e4a-111">[in] 以位元組為單位的 `pValue` 緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="06e4a-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="06e4a-112">[in] 包含要設定之值的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="06e4a-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06e4a-113">備註</span><span class="sxs-lookup"><span data-stu-id="06e4a-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06e4a-114">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="06e4a-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e4a-115">需求</span><span class="sxs-lookup"><span data-stu-id="06e4a-115">Requirements</span></span>  
 <span data-ttu-id="06e4a-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06e4a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06e4a-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06e4a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06e4a-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06e4a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06e4a-119">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06e4a-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e4a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06e4a-120">See also</span></span>

- [<span data-ttu-id="06e4a-121">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="06e4a-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="06e4a-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="06e4a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
