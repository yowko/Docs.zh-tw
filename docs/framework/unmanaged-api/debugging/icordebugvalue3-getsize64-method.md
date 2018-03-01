---
title: "ICorDebugValue3::GetSize64 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4eb0c4691b82bdfaecb97c5969a942c113987c04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="a5c7b-102">ICorDebugValue3::GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="a5c7b-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="a5c7b-103">取得以位元組為單位，這個大小， [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5c7b-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5c7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5c7b-105">Parameters</span></span>  
 <span data-ttu-id="a5c7b-106">pSize</span><span class="sxs-lookup"><span data-stu-id="a5c7b-106">pSize</span></span>  
 <span data-ttu-id="a5c7b-107">[out]大小 （位元組），這個物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c7b-108">備註</span><span class="sxs-lookup"><span data-stu-id="a5c7b-108">Remarks</span></span>  
 <span data-ttu-id="a5c7b-109">如果此值的類型是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="a5c7b-110">`ICorDebugValue3::GetSize`方法不同於[icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)其輸出參數的型別中的方法。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="a5c7b-111">在[icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)，輸出參數是`ULONG32`; 在`ICorDebugValue3::GetSize`，它是`ULONG64`。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="a5c7b-112">這可讓[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)介面的報表大小超過 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c7b-113">需求</span><span class="sxs-lookup"><span data-stu-id="a5c7b-113">Requirements</span></span>  
 <span data-ttu-id="a5c7b-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5c7b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c7b-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5c7b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5c7b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5c7b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5c7b-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c7b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c7b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c7b-118">See Also</span></span>  
 [<span data-ttu-id="a5c7b-119">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="a5c7b-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="a5c7b-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a5c7b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
