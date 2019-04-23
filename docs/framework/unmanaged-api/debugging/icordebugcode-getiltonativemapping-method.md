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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c30623e53b57a78287b26d4a362793cfb32baede
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131055"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="96262-102">ICorDebugCode::GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="96262-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="96262-103">取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，表示對應從 Microsoft intermediate language (MSIL) 位移到原生位移陣列。</span><span class="sxs-lookup"><span data-stu-id="96262-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96262-104">語法</span><span class="sxs-lookup"><span data-stu-id="96262-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96262-105">參數</span><span class="sxs-lookup"><span data-stu-id="96262-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="96262-106">[in] `map` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="96262-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="96262-107">[out]項目中傳回的實際數目的指標`map`陣列。</span><span class="sxs-lookup"><span data-stu-id="96262-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="96262-108">[out]陣列`COR_DEBUG_IL_TO_NATIVE_MAP`結構，每一個都代表從 MSIL 位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="96262-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="96262-109">沒有任何排序傳回的項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="96262-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96262-110">備註</span><span class="sxs-lookup"><span data-stu-id="96262-110">Remarks</span></span>  
 <span data-ttu-id="96262-111">`GetILToNativeMapping`方法會傳回有意義的結果，只有當此"ICorDebugCode 」 執行個體代表已在 just-in-time (JIT) 編譯的 MSIL 程式碼的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="96262-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96262-112">需求</span><span class="sxs-lookup"><span data-stu-id="96262-112">Requirements</span></span>  
 <span data-ttu-id="96262-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96262-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96262-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96262-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96262-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96262-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96262-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96262-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96262-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96262-117">See also</span></span>

- [<span data-ttu-id="96262-118">ICorDebugCode 介面</span><span class="sxs-lookup"><span data-stu-id="96262-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
