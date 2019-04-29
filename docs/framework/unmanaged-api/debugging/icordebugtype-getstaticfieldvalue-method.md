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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c6b86c5ce3cc246af600d9b65d2fe12a0427f9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663839"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="d3748-102">ICorDebugType::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="d3748-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="d3748-103">取得 ICorDebugValue 物件，其中包含指定的欄位所參考的靜態欄位值的介面指標權杖中指定的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="d3748-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3748-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3748-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3748-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3748-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="d3748-106">[in]`mdFieldDef`指定靜態欄位的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d3748-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="d3748-107">[in]ICorDebugFrame 代表堆疊框架指標。</span><span class="sxs-lookup"><span data-stu-id="d3748-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d3748-108">[out]位址指標`ICorDebugValue`，其中包含靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="d3748-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3748-109">備註</span><span class="sxs-lookup"><span data-stu-id="d3748-109">Remarks</span></span>  
 <span data-ttu-id="d3748-110">`GetStaticFieldValue`方法可能只使用型別是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，如所示[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d3748-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="d3748-111">對於非泛型型別，作業則是由執行`GetStaticFieldValue`等同於呼叫[icordebugclass:: Getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass 物件所傳回[icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="d3748-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="d3748-112">泛型型別，對於靜態欄位值會相對於特定的具現化。</span><span class="sxs-lookup"><span data-stu-id="d3748-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="d3748-113">此外，如果相對於執行緒、 內容或應用程式定義域可能是靜態欄位，然後堆疊框架會協助偵錯工具判斷適當的值。</span><span class="sxs-lookup"><span data-stu-id="d3748-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3748-114">備註</span><span class="sxs-lookup"><span data-stu-id="d3748-114">Remarks</span></span>  
 <span data-ttu-id="d3748-115">`GetStaticFieldValue` 可用時，才呼叫`ICorDebugType::GetType`傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的值。</span><span class="sxs-lookup"><span data-stu-id="d3748-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3748-116">需求</span><span class="sxs-lookup"><span data-stu-id="d3748-116">Requirements</span></span>  
 <span data-ttu-id="d3748-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3748-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3748-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3748-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3748-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3748-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3748-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3748-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
