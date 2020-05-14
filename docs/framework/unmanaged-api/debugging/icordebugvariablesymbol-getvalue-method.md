---
title: ICorDebugVariableSymbol::GetValue Method
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: f217f7226d53a27363f66eb90a340fd3604a0217
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396510"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="fe497-102">ICorDebugVariableSymbol::GetValue Method</span><span class="sxs-lookup"><span data-stu-id="fe497-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="fe497-103">取得變數的值做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="fe497-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe497-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe497-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe497-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe497-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="fe497-106">[in] 要從中讀取值之變數的開始位移。</span><span class="sxs-lookup"><span data-stu-id="fe497-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="fe497-107">讀取物件中的成員欄位時，會使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="fe497-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="fe497-108">[in] 以位元組為單位的 `context` 引數大小。</span><span class="sxs-lookup"><span data-stu-id="fe497-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="fe497-109">[in] 用來讀取值的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="fe497-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="fe497-110">[in] 以位元組為單位的 `pValue` 緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="fe497-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="fe497-111">[out] 實際寫入至 `pValue` 緩衝區的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="fe497-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="fe497-112">[out] 包含變數值的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="fe497-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe497-113">備註</span><span class="sxs-lookup"><span data-stu-id="fe497-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe497-114">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="fe497-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe497-115">需求</span><span class="sxs-lookup"><span data-stu-id="fe497-115">Requirements</span></span>  
 <span data-ttu-id="fe497-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe497-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe497-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe497-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe497-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe497-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe497-119">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe497-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe497-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe497-120">See also</span></span>

- [<span data-ttu-id="fe497-121">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="fe497-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="fe497-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fe497-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
