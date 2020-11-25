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
ms.openlocfilehash: c3120a0dd859f581e6356fc260043cb83250ae9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724828"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="a2a73-102">ICorDebugComObjectValue::GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="a2a73-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>

<span data-ttu-id="a2a73-103">取得在目前執行時間可呼叫包裝函式上快取的原始介面指標 (RCW) 。</span><span class="sxs-lookup"><span data-stu-id="a2a73-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a73-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2a73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2a73-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2a73-105">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="a2a73-106">在值，這個值會指出方法是否只會傳回 Windows 執行階段介面 (`IInspectable` 介面) 或由執行時間可呼叫包裝函式快取的所有 COM 介面 (RCW) 。</span><span class="sxs-lookup"><span data-stu-id="a2a73-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="a2a73-107">在要取出其位址的物件數目。</span><span class="sxs-lookup"><span data-stu-id="a2a73-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a2a73-108">擴展實際傳回的值數目指標 `CORDB_ADDRESS` `ptrs` 。</span><span class="sxs-lookup"><span data-stu-id="a2a73-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="a2a73-109">值陣列的起始位址指標 `CORDB_ADDRESS` ，其中包含快取介面物件的位址。</span><span class="sxs-lookup"><span data-stu-id="a2a73-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2a73-110">備註</span><span class="sxs-lookup"><span data-stu-id="a2a73-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a73-111">需求</span><span class="sxs-lookup"><span data-stu-id="a2a73-111">Requirements</span></span>  

 <span data-ttu-id="a2a73-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2a73-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a73-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2a73-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2a73-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2a73-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2a73-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2a73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a73-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2a73-116">See also</span></span>

- [<span data-ttu-id="a2a73-117">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="a2a73-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="a2a73-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a2a73-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
