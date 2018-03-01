---
title: "ICorDebugType::GetClass 方法"
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
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32462159bc00ea766af3e3bc0f9d3d7a35eb2e38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="a994e-102">ICorDebugType::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="a994e-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="a994e-103">取得表示未具現化的泛型型別 ICorDebugClass 介面指標。</span><span class="sxs-lookup"><span data-stu-id="a994e-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a994e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a994e-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a994e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a994e-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="a994e-106">[out]位址指標`ICorDebugClass`表示未具現化的泛型類型的介面。</span><span class="sxs-lookup"><span data-stu-id="a994e-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a994e-107">備註</span><span class="sxs-lookup"><span data-stu-id="a994e-107">Remarks</span></span>  
 <span data-ttu-id="a994e-108">`GetClass`只有在某些情況下，可以被呼叫。</span><span class="sxs-lookup"><span data-stu-id="a994e-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="a994e-109">呼叫[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)之前先呼叫`GetClass`。</span><span class="sxs-lookup"><span data-stu-id="a994e-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="a994e-110">如果`ICorDebugType::GetType`傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，CorElementType 值`GetClass`可以呼叫以取得泛型類型的未具現化的型別。</span><span class="sxs-lookup"><span data-stu-id="a994e-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a994e-111">需求</span><span class="sxs-lookup"><span data-stu-id="a994e-111">Requirements</span></span>  
 <span data-ttu-id="a994e-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a994e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a994e-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a994e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a994e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a994e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a994e-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a994e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
