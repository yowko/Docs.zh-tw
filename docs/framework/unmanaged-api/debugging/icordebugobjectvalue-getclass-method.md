---
title: "ICorDebugObjectValue::GetClass 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dee9f110647230e54df527959651dc5b2fb73b3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="2a1e9-102">ICorDebugObjectValue::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="2a1e9-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="2a1e9-103">取得這個物件值的類別。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a1e9-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a1e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a1e9-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="2a1e9-106">[out]表示這個 「 ICorDebugObjectValue 」 物件所表示之物件值的類別 」 ICorDebugClass 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a1e9-107">備註</span><span class="sxs-lookup"><span data-stu-id="2a1e9-107">Remarks</span></span>  
 <span data-ttu-id="2a1e9-108">`GetClass`和[icordebugvalue:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)方法都會傳回值的類型資訊; 它們同時取代感知泛型[icordebugvalue2:: Getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a1e9-109">需求</span><span class="sxs-lookup"><span data-stu-id="2a1e9-109">Requirements</span></span>  
 <span data-ttu-id="2a1e9-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a1e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1e9-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a1e9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a1e9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a1e9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a1e9-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a1e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1e9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a1e9-114">See Also</span></span>  
    
 
