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
ms.openlocfilehash: 0e49c24a4b98a5287ec27b1667f45055d9a94d53
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903408"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="8e88f-102">ICorDebugCode::GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="8e88f-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="8e88f-103">取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，表示對應從 Microsoft intermediate language (MSIL) 位移到原生位移陣列。</span><span class="sxs-lookup"><span data-stu-id="8e88f-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e88f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e88f-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e88f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e88f-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="8e88f-106">[in] `map` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="8e88f-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="8e88f-107">[out]項目中傳回的實際數目的指標`map`陣列。</span><span class="sxs-lookup"><span data-stu-id="8e88f-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="8e88f-108">[out]陣列`COR_DEBUG_IL_TO_NATIVE_MAP`結構，每一個都代表從 MSIL 位移到原生位移的對應。</span><span class="sxs-lookup"><span data-stu-id="8e88f-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="8e88f-109">沒有任何排序傳回的項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="8e88f-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e88f-110">備註</span><span class="sxs-lookup"><span data-stu-id="8e88f-110">Remarks</span></span>  
 <span data-ttu-id="8e88f-111">`GetILToNativeMapping`方法會傳回有意義的結果，只有當此"ICorDebugCode 」 執行個體代表已在 just-in-time (JIT) 編譯的 MSIL 程式碼的原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="8e88f-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e88f-112">需求</span><span class="sxs-lookup"><span data-stu-id="8e88f-112">Requirements</span></span>  
 <span data-ttu-id="8e88f-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e88f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e88f-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e88f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e88f-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e88f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e88f-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e88f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e88f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e88f-117">See also</span></span>
- [<span data-ttu-id="8e88f-118">ICorDebugCode 介面 1</span><span class="sxs-lookup"><span data-stu-id="8e88f-118">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
