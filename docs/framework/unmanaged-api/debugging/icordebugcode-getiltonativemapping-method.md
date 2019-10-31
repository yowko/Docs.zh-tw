---
title: ICorDebugCode::GetILToNativeMapping 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 011da6aacbf4c40420329952f47b1fabdfc2c1a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125625"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="3a807-102">ICorDebugCode::GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="3a807-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="3a807-103">取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，代表從 Microsoft 中繼語言（MSIL）位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="3a807-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a807-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a807-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a807-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a807-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="3a807-106">[in] `map` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="3a807-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="3a807-107">脫銷`map` 陣列中所傳回之實際專案數目的指標。</span><span class="sxs-lookup"><span data-stu-id="3a807-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="3a807-108">脫銷`COR_DEBUG_IL_TO_NATIVE_MAP` 結構的陣列，其中每一個都代表從 MSIL 位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="3a807-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="3a807-109">不會對傳回的元素陣列進行排序。</span><span class="sxs-lookup"><span data-stu-id="3a807-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a807-110">備註</span><span class="sxs-lookup"><span data-stu-id="3a807-110">Remarks</span></span>  
 <span data-ttu-id="3a807-111">只有當這個 "ICorDebugCode" 實例代表從 MSIL 程式碼編譯而來的機器碼（JIT）時，`GetILToNativeMapping` 方法才會傳回有意義的結果。</span><span class="sxs-lookup"><span data-stu-id="3a807-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a807-112">需求</span><span class="sxs-lookup"><span data-stu-id="3a807-112">Requirements</span></span>  
 <span data-ttu-id="3a807-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a807-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a807-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a807-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a807-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a807-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a807-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a807-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a807-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a807-117">See also</span></span>

- [<span data-ttu-id="3a807-118">ICorDebugCode 介面</span><span class="sxs-lookup"><span data-stu-id="3a807-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
