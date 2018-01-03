---
title: "ICorDebugComObjectValue::GetCachedInterfacePointers 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue::GetCachedInterfacePointers
api_location: mscordbi.dll
f1_keywords: ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="2ec1b-102">ICorDebugComObjectValue::GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="2ec1b-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="2ec1b-103">取得目前執行階段可呼叫包裝函式 (RCW) 上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="2ec1b-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ec1b-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ec1b-105">參數</span><span class="sxs-lookup"><span data-stu-id="2ec1b-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="2ec1b-106">[in]值，指出該方法會傳回只[!INCLUDE[wrt](../../../../includes/wrt-md.md)]介面 (`IInspectable`介面) 或執行階段可呼叫包裝函式 (RCW) 不會快取的所有 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="2ec1b-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="2ec1b-107">[in]要擷取其位址的物件數目。</span><span class="sxs-lookup"><span data-stu-id="2ec1b-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="2ec1b-108">[out]數目的指標`CORDB_ADDRESS`中實際傳回的值`ptrs`。</span><span class="sxs-lookup"><span data-stu-id="2ec1b-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="2ec1b-109">陣列的起始位址的指標`CORDB_ADDRESS`值包含地址的快取介面物件。</span><span class="sxs-lookup"><span data-stu-id="2ec1b-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec1b-110">備註</span><span class="sxs-lookup"><span data-stu-id="2ec1b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec1b-111">需求</span><span class="sxs-lookup"><span data-stu-id="2ec1b-111">Requirements</span></span>  
 <span data-ttu-id="2ec1b-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ec1b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec1b-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ec1b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ec1b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ec1b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ec1b-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec1b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec1b-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ec1b-116">See Also</span></span>  
 [<span data-ttu-id="2ec1b-117">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="2ec1b-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="2ec1b-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2ec1b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
