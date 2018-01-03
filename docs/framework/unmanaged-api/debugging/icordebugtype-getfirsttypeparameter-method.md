---
title: "ICorDebugType::GetFirstTypeParameter 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetFirstTypeParameter
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e963553bfeac2d659de8fc460a938d2d523b53e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="12eab-102">ICorDebugType::GetFirstTypeParameter 方法</span><span class="sxs-lookup"><span data-stu-id="12eab-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="12eab-103">取得的介面指標來代表第一個 ICorDebugType<xref:System.Type>參數所表示之型別的`ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="12eab-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12eab-104">語法</span><span class="sxs-lookup"><span data-stu-id="12eab-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12eab-105">參數</span><span class="sxs-lookup"><span data-stu-id="12eab-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="12eab-106">[out]位址指標`ICorDebugType`物件，表示第一個參數。</span><span class="sxs-lookup"><span data-stu-id="12eab-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12eab-107">備註</span><span class="sxs-lookup"><span data-stu-id="12eab-107">Remarks</span></span>  
 <span data-ttu-id="12eab-108">`GetFirstTypeParameter`可以呼叫在其中類型相關的其他資訊涉及，最多的情況下一個型別參數。</span><span class="sxs-lookup"><span data-stu-id="12eab-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="12eab-109">特別是，它可以做為 ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR，該類型時所指定[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="12eab-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12eab-110">需求</span><span class="sxs-lookup"><span data-stu-id="12eab-110">Requirements</span></span>  
 <span data-ttu-id="12eab-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12eab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12eab-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12eab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12eab-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12eab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12eab-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12eab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
