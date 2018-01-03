---
title: "ICorDebugValue::GetSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf99b35d45c1dda8f187e0206e068c128f347d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="b7c4d-102">ICorDebugValue::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="b7c4d-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="b7c4d-103">取得大小，以位元組為單位，此 「 ICorDebugValue 」 物件。</span><span class="sxs-lookup"><span data-stu-id="b7c4d-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7c4d-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7c4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7c4d-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="b7c4d-106">[out]以位元組為單位，此值物件的大小。</span><span class="sxs-lookup"><span data-stu-id="b7c4d-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7c4d-107">備註</span><span class="sxs-lookup"><span data-stu-id="b7c4d-107">Remarks</span></span>  
 <span data-ttu-id="b7c4d-108">如果值的類型是參考型別，這個方法會傳回指標的大小，而不是物件的大小。</span><span class="sxs-lookup"><span data-stu-id="b7c4d-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="b7c4d-109">`ICorDebugValue::GetSize`方法會傳回`COR_E_OVERFLOW`大於 4 GB，在 64 位元平台上的物件。</span><span class="sxs-lookup"><span data-stu-id="b7c4d-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="b7c4d-110">使用[icordebugvalue3:: Getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法的物件，是大於 4 GB。</span><span class="sxs-lookup"><span data-stu-id="b7c4d-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c4d-111">需求</span><span class="sxs-lookup"><span data-stu-id="b7c4d-111">Requirements</span></span>  
 <span data-ttu-id="b7c4d-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7c4d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c4d-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7c4d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7c4d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7c4d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7c4d-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7c4d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c4d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7c4d-116">See Also</span></span>  
    
 [<span data-ttu-id="b7c4d-117">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="b7c4d-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
