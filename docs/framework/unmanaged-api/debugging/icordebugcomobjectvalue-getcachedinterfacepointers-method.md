---
title: ICorDebugComObjectValue::GetCachedInterfacePointers 方法
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdbec0101de269b3d5b09e750d552c993a0198ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748476"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="f15f2-102">ICorDebugComObjectValue::GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="f15f2-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="f15f2-103">取得目前執行階段可呼叫包裝函式 (RCW) 上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="f15f2-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="f15f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f15f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="f15f2-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="f15f2-106">[in]值，指出是否此方法會傳回唯一的 Windows 執行階段介面 (`IInspectable`介面) 或所快取的執行階段可呼叫包裝函式 (RCW) 的所有 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="f15f2-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="f15f2-107">[in]其位址是要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="f15f2-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f15f2-108">[out]指標的數目`CORDB_ADDRESS`中實際傳回的值`ptrs`。</span><span class="sxs-lookup"><span data-stu-id="f15f2-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="f15f2-109">陣列的起始位址的指標`CORDB_ADDRESS`快取的值，包含位址之介面的物件。</span><span class="sxs-lookup"><span data-stu-id="f15f2-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f15f2-110">備註</span><span class="sxs-lookup"><span data-stu-id="f15f2-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15f2-111">需求</span><span class="sxs-lookup"><span data-stu-id="f15f2-111">Requirements</span></span>  
 <span data-ttu-id="f15f2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f15f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f15f2-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f15f2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f15f2-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f15f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f15f2-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f15f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15f2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f15f2-116">See also</span></span>

- [<span data-ttu-id="f15f2-117">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="f15f2-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="f15f2-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f15f2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
