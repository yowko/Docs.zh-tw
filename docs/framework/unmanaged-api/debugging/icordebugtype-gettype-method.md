---
title: ICorDebugType::GetType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78f2733584e07433171c91d6a2674d3a67c8e283
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772513"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="2d93c-102">ICorDebugType::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="2d93c-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="2d93c-103">取得描述 common language runtime (CLR) 的原生類型 CorElementType 值<xref:System.Type>此 ICorDebugType 所表示。</span><span class="sxs-lookup"><span data-stu-id="2d93c-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d93c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d93c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d93c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d93c-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="2d93c-106">[out]值的指標`CorElementType`列舉，指出 CLR<xref:System.Type>這個`ICorDebugType`表示。</span><span class="sxs-lookup"><span data-stu-id="2d93c-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d93c-107">備註</span><span class="sxs-lookup"><span data-stu-id="2d93c-107">Remarks</span></span>  
 <span data-ttu-id="2d93c-108">如果值`ty`ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE， [icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)方法可能會呼叫以取得泛型型別未具現化的型別; 否則請勿呼叫`ICorDebugType::GetClass`。</span><span class="sxs-lookup"><span data-stu-id="2d93c-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d93c-109">需求</span><span class="sxs-lookup"><span data-stu-id="2d93c-109">Requirements</span></span>  
 <span data-ttu-id="2d93c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d93c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d93c-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d93c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d93c-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d93c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d93c-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d93c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
