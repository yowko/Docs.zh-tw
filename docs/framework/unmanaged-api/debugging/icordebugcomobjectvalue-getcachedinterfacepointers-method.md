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
ms.openlocfilehash: 9d1d6d2f506086dd3204053b0b635da2e7cdc87e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783957"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="f481d-102">ICorDebugComObjectValue::GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="f481d-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="f481d-103">取得在目前執行時間可呼叫包裝函式（RCW）上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="f481d-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f481d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f481d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f481d-105">參數</span><span class="sxs-lookup"><span data-stu-id="f481d-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="f481d-106">在值，指出此方法是否只會傳回 Windows 執行階段介面（`IInspectable` 介面）或由執行時間可呼叫包裝函式（RCW）所快取的所有 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="f481d-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="f481d-107">在要抓取其位址的物件數目。</span><span class="sxs-lookup"><span data-stu-id="f481d-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f481d-108">脫銷`ptrs`中實際傳回之 `CORDB_ADDRESS` 值數目的指標。</span><span class="sxs-lookup"><span data-stu-id="f481d-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="f481d-109">`CORDB_ADDRESS` 值陣列的起始位址指標，其中包含快取介面物件的位址。</span><span class="sxs-lookup"><span data-stu-id="f481d-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f481d-110">備註</span><span class="sxs-lookup"><span data-stu-id="f481d-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f481d-111">需求</span><span class="sxs-lookup"><span data-stu-id="f481d-111">Requirements</span></span>  
 <span data-ttu-id="f481d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f481d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f481d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f481d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f481d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f481d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f481d-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f481d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f481d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f481d-116">See also</span></span>

- [<span data-ttu-id="f481d-117">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="f481d-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="f481d-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f481d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
