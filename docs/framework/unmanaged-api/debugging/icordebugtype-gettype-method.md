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
ms.openlocfilehash: f0f45d5f0b2ea8cefa6bd36e909ae43d80c968ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700882"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="6dfa5-102">ICorDebugType::GetType 方法</span><span class="sxs-lookup"><span data-stu-id="6dfa5-102">ICorDebugType::GetType Method</span></span>

<span data-ttu-id="6dfa5-103">取得 CorElementType 值，這個值描述 <xref:System.Type> 此 ICorDebugType 所表示之 common language runtime (CLR) 的原生類型。</span><span class="sxs-lookup"><span data-stu-id="6dfa5-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfa5-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dfa5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dfa5-105">參數</span><span class="sxs-lookup"><span data-stu-id="6dfa5-105">Parameters</span></span>  

 `ty`  
 <span data-ttu-id="6dfa5-106">擴展列舉值的指標 `CorElementType` ，表示這個所代表的 CLR <xref:System.Type> `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="6dfa5-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dfa5-107">備註</span><span class="sxs-lookup"><span data-stu-id="6dfa5-107">Remarks</span></span>  

 <span data-ttu-id="6dfa5-108">如果的值 `ty` 為 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，可能會呼叫 [ICorDebugType：： GetClass](icordebugtype-getclass-method.md) 方法，以取得泛型型別的未具現化型別; 否則，請勿呼叫 `ICorDebugType::GetClass` 。</span><span class="sxs-lookup"><span data-stu-id="6dfa5-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfa5-109">需求</span><span class="sxs-lookup"><span data-stu-id="6dfa5-109">Requirements</span></span>  

 <span data-ttu-id="6dfa5-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dfa5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfa5-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6dfa5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6dfa5-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dfa5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dfa5-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfa5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
