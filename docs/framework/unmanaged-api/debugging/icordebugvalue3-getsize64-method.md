---
title: ICorDebugValue3::GetSize64 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c0b45e08f7b88d9374023f95c6e3e22139c8949
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144764"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="e5493-102">ICorDebugValue3::GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="e5493-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="e5493-103">取得大小，以位元組為單位，這[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="e5493-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5493-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5493-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5493-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5493-105">Parameters</span></span>  
 <span data-ttu-id="e5493-106">pSize</span><span class="sxs-lookup"><span data-stu-id="e5493-106">pSize</span></span>  
 <span data-ttu-id="e5493-107">[out]大小 （位元組），這個物件的指標。</span><span class="sxs-lookup"><span data-stu-id="e5493-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5493-108">備註</span><span class="sxs-lookup"><span data-stu-id="e5493-108">Remarks</span></span>  
 <span data-ttu-id="e5493-109">如果此值的型別是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="e5493-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="e5493-110">`ICorDebugValue3::GetSize`方法不同於[icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)其輸出參數的型別中的方法。</span><span class="sxs-lookup"><span data-stu-id="e5493-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="e5493-111">在  [icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)，輸出參數是`ULONG32`; 在`ICorDebugValue3::GetSize`，它是`ULONG64`。</span><span class="sxs-lookup"><span data-stu-id="e5493-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="e5493-112">這可讓[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)介面來報告的大小超過 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e5493-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5493-113">需求</span><span class="sxs-lookup"><span data-stu-id="e5493-113">Requirements</span></span>  
 <span data-ttu-id="e5493-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5493-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5493-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5493-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5493-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5493-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e5493-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e5493-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5493-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5493-118">See also</span></span>

- [<span data-ttu-id="e5493-119">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="e5493-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="e5493-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e5493-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
