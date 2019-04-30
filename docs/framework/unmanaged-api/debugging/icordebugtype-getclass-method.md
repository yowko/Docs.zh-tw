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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0915027ce6a3768ff854eafc5496c5057081cc4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946207"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="b6691-102">ICorDebugType::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="b6691-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="b6691-103">取得表示未具現化的泛型型別 ICorDebugClass 介面指標。</span><span class="sxs-lookup"><span data-stu-id="b6691-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6691-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6691-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6691-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6691-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="b6691-106">[out]位址指標`ICorDebugClass`介面，表示未具現化的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="b6691-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6691-107">備註</span><span class="sxs-lookup"><span data-stu-id="b6691-107">Remarks</span></span>  
 <span data-ttu-id="b6691-108">`GetClass` 您可以只在某些情況下呼叫。</span><span class="sxs-lookup"><span data-stu-id="b6691-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="b6691-109">呼叫[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)再呼叫`GetClass`。</span><span class="sxs-lookup"><span data-stu-id="b6691-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="b6691-110">如果`ICorDebugType::GetType`傳回 CorElementType 值，這個值是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，`GetClass`可以呼叫以取得泛型型別未具現化的型別。</span><span class="sxs-lookup"><span data-stu-id="b6691-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6691-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6691-111">Requirements</span></span>  
 <span data-ttu-id="b6691-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6691-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6691-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6691-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6691-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6691-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6691-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6691-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
