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
ms.openlocfilehash: 3de85626be6ae8e4769ac261f4de1479461417ec
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893533"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="ce013-102">ICorDebugCode::GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="ce013-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="ce013-103">取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，代表從 Microsoft 中繼語言（MSIL）位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="ce013-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce013-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce013-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce013-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce013-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="ce013-106">[in] `map` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ce013-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="ce013-107">脫銷`map`陣列中所傳回專案實際數目的指標。</span><span class="sxs-lookup"><span data-stu-id="ce013-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="ce013-108">脫銷`COR_DEBUG_IL_TO_NATIVE_MAP`結構的陣列，其中每一個都代表從 MSIL 位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="ce013-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="ce013-109">不會對傳回的元素陣列進行排序。</span><span class="sxs-lookup"><span data-stu-id="ce013-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce013-110">備註</span><span class="sxs-lookup"><span data-stu-id="ce013-110">Remarks</span></span>  
 <span data-ttu-id="ce013-111">只有`GetILToNativeMapping`在這個 "ICorDebugCode" 實例代表從 MSIL 程式碼編譯的機器碼（JIT）時，方法才會傳回有意義的結果。</span><span class="sxs-lookup"><span data-stu-id="ce013-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce013-112">需求</span><span class="sxs-lookup"><span data-stu-id="ce013-112">Requirements</span></span>  
 <span data-ttu-id="ce013-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce013-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce013-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce013-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce013-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce013-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce013-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce013-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce013-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce013-117">See also</span></span>

- [<span data-ttu-id="ce013-118">ICorDebugCode 介面</span><span class="sxs-lookup"><span data-stu-id="ce013-118">ICorDebugCode Interface</span></span>](icordebugcode-interface1.md)
