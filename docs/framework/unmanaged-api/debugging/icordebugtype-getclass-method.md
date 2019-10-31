---
title: ICorDebugType::GetClass 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 3a895f432ed640cc35a492df0c91cece34893062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122371"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="4aa81-102">ICorDebugType::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="4aa81-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="4aa81-103">取得 ICorDebugClass 的介面指標，表示未具現化的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="4aa81-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa81-104">語法</span><span class="sxs-lookup"><span data-stu-id="4aa81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aa81-105">參數</span><span class="sxs-lookup"><span data-stu-id="4aa81-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="4aa81-106">脫銷表示未具現化泛型型別之 `ICorDebugClass` 介面的位址指標。</span><span class="sxs-lookup"><span data-stu-id="4aa81-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4aa81-107">備註</span><span class="sxs-lookup"><span data-stu-id="4aa81-107">Remarks</span></span>  
 <span data-ttu-id="4aa81-108">`GetClass` 只能在特定條件下呼叫。</span><span class="sxs-lookup"><span data-stu-id="4aa81-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="4aa81-109">呼叫[ICorDebugType：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ，再呼叫 `GetClass`。</span><span class="sxs-lookup"><span data-stu-id="4aa81-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="4aa81-110">如果 `ICorDebugType::GetType` 傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的 CorElementType 值，則可以呼叫 `GetClass` 以取得泛型型別的未具現化類型。</span><span class="sxs-lookup"><span data-stu-id="4aa81-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aa81-111">需求</span><span class="sxs-lookup"><span data-stu-id="4aa81-111">Requirements</span></span>  
 <span data-ttu-id="4aa81-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa81-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aa81-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4aa81-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4aa81-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aa81-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4aa81-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aa81-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
