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
ms.openlocfilehash: 7f3010cccc584288608b3f6ba95efbeb95f271fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132052"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="46e2b-102">ICorDebugType::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="46e2b-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="46e2b-103">取得 CorElementType 值，描述此 ICorDebugType 所表示之 common language runtime （CLR） <xref:System.Type> 的原生類型。</span><span class="sxs-lookup"><span data-stu-id="46e2b-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="46e2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46e2b-105">參數</span><span class="sxs-lookup"><span data-stu-id="46e2b-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="46e2b-106">脫銷`CorElementType` 列舉值的指標，表示此 `ICorDebugType` 所代表的 CLR <xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="46e2b-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46e2b-107">備註</span><span class="sxs-lookup"><span data-stu-id="46e2b-107">Remarks</span></span>  
 <span data-ttu-id="46e2b-108">如果 `ty` 的值是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，則可以呼叫[ICorDebugType：： GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)方法來取得泛型型別的未具現化型別。否則，請勿呼叫 `ICorDebugType::GetClass`。</span><span class="sxs-lookup"><span data-stu-id="46e2b-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46e2b-109">需求</span><span class="sxs-lookup"><span data-stu-id="46e2b-109">Requirements</span></span>  
 <span data-ttu-id="46e2b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46e2b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46e2b-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46e2b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46e2b-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46e2b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46e2b-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46e2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
