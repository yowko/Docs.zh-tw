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
ms.openlocfilehash: 281b9f46194e93220f47ef8aadbf29ce03084582
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711944"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="a04c5-102">ICorDebugType::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="a04c5-102">ICorDebugType::GetStaticFieldValue Method</span></span>

<span data-ttu-id="a04c5-103">取得 ICorDebugValue 物件的介面指標，其中包含指定之堆疊框架中指定之欄位標記所參考的靜態域值。</span><span class="sxs-lookup"><span data-stu-id="a04c5-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="a04c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a04c5-105">參數</span><span class="sxs-lookup"><span data-stu-id="a04c5-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="a04c5-106">在 `mdFieldDef` 指定靜態欄位的 token。</span><span class="sxs-lookup"><span data-stu-id="a04c5-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="a04c5-107">在代表堆疊框架之 ICorDebugFrame 的指標。</span><span class="sxs-lookup"><span data-stu-id="a04c5-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a04c5-108">擴展的位址指標 `ICorDebugValue` ，其中包含靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="a04c5-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04c5-109">備註</span><span class="sxs-lookup"><span data-stu-id="a04c5-109">Remarks</span></span>  

 <span data-ttu-id="a04c5-110">`GetStaticFieldValue`只有當型別是 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 時，才可使用方法，如[ICorDebugType：： GetType](icordebugtype-gettype-method.md)方法所示。</span><span class="sxs-lookup"><span data-stu-id="a04c5-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="a04c5-111">針對非泛型型別，所執行的作業與在 `GetStaticFieldValue` [ICorDebugType：： GetClass](icordebugtype-getclass-method.md)傳回的 ICorDebugClass 物件上呼叫[ICorDebugClass：： GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md)相同。</span><span class="sxs-lookup"><span data-stu-id="a04c5-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="a04c5-112">若為泛型型別，靜態域值會相對於特定具現化。</span><span class="sxs-lookup"><span data-stu-id="a04c5-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="a04c5-113">此外，如果靜態欄位可能相對於執行緒、內容或應用程式域，則堆疊框架將有助於偵錯工具判斷適當的值。</span><span class="sxs-lookup"><span data-stu-id="a04c5-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a04c5-114">備註</span><span class="sxs-lookup"><span data-stu-id="a04c5-114">Remarks</span></span>  

 <span data-ttu-id="a04c5-115">`GetStaticFieldValue` 只有在呼叫傳回 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE 的值時，才能使用 `ICorDebugType::GetType` 。</span><span class="sxs-lookup"><span data-stu-id="a04c5-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a04c5-116">需求</span><span class="sxs-lookup"><span data-stu-id="a04c5-116">Requirements</span></span>  

 <span data-ttu-id="a04c5-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a04c5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a04c5-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a04c5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a04c5-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a04c5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a04c5-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a04c5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
