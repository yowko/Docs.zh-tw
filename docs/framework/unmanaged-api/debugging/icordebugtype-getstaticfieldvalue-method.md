---
title: ICorDebugType::GetStaticFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 95183701987d3ddec3835a17c5d256c25c2c4c64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132073"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="46713-102">ICorDebugType::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="46713-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="46713-103">取得 ICorDebugValue 物件的介面指標，其中包含指定之堆疊框架中指定欄位標記所參考的靜態欄位值。</span><span class="sxs-lookup"><span data-stu-id="46713-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46713-104">語法</span><span class="sxs-lookup"><span data-stu-id="46713-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46713-105">參數</span><span class="sxs-lookup"><span data-stu-id="46713-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="46713-106">在指定靜態欄位的 `mdFieldDef` token。</span><span class="sxs-lookup"><span data-stu-id="46713-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="46713-107">在代表堆疊框架之 ICorDebugFrame 的指標。</span><span class="sxs-lookup"><span data-stu-id="46713-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="46713-108">脫銷`ICorDebugValue` 的位址指標，其中包含靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="46713-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46713-109">備註</span><span class="sxs-lookup"><span data-stu-id="46713-109">Remarks</span></span>  
 <span data-ttu-id="46713-110">只有在類型是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 時，才可以使用 `GetStaticFieldValue` 方法，如[ICorDebugType：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法所指示。</span><span class="sxs-lookup"><span data-stu-id="46713-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="46713-111">針對非泛型型別，`GetStaticFieldValue` 所執行的作業等同于在[ICorDebugType：： GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)傳回的 ICorDebugClass 物件上呼叫[ICorDebugClass：： GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="46713-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="46713-112">若是泛型型別，靜態域值會相對於特定的具現化。</span><span class="sxs-lookup"><span data-stu-id="46713-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="46713-113">此外，如果靜態欄位可能相對於執行緒、內容或應用程式域，則堆疊框架會協助偵錯工具判斷適當的值。</span><span class="sxs-lookup"><span data-stu-id="46713-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46713-114">備註</span><span class="sxs-lookup"><span data-stu-id="46713-114">Remarks</span></span>  
 <span data-ttu-id="46713-115">只有在呼叫 `ICorDebugType::GetType` 傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的值時，才能使用 `GetStaticFieldValue`。</span><span class="sxs-lookup"><span data-stu-id="46713-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46713-116">需求</span><span class="sxs-lookup"><span data-stu-id="46713-116">Requirements</span></span>  
 <span data-ttu-id="46713-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46713-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46713-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46713-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46713-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46713-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46713-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46713-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
