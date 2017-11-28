---
title: "ICorDebugType::GetStaticFieldValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34a37ef9a28dd0e6325db9bee61146f14d4638a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="a3942-102">ICorDebugType::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="a3942-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="a3942-103">取得 ICorDebugValue 物件，其中包含所指定的欄位參考的靜態欄位值的介面指標的指定之堆疊框架中語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a3942-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3942-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3942-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3942-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3942-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="a3942-106">[in]`mdFieldDef`指定的靜態欄位的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a3942-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="a3942-107">[in]代表堆疊框架 ICorDebugFrame 指標。</span><span class="sxs-lookup"><span data-stu-id="a3942-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a3942-108">[out]位址指標`ICorDebugValue`，其中包含靜態欄位值。</span><span class="sxs-lookup"><span data-stu-id="a3942-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3942-109">備註</span><span class="sxs-lookup"><span data-stu-id="a3942-109">Remarks</span></span>  
 <span data-ttu-id="a3942-110">`GetStaticFieldValue`方法可能僅使用的類型為 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE，由[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a3942-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="a3942-111">非泛型類型的作業則是由執行`GetStaticFieldValue`等同於呼叫[icordebugclass:: Getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass 物件傳回的上[icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="a3942-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="a3942-112">泛型型別，靜態欄位值都是相對於特定的具現化。</span><span class="sxs-lookup"><span data-stu-id="a3942-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="a3942-113">此外，如果相對於執行緒、 內容或應用程式定義域可能是靜態欄位，然後堆疊框架可協助偵錯工具判斷正確的值。</span><span class="sxs-lookup"><span data-stu-id="a3942-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3942-114">備註</span><span class="sxs-lookup"><span data-stu-id="a3942-114">Remarks</span></span>  
 <span data-ttu-id="a3942-115">`GetStaticFieldValue`可用時，才呼叫`ICorDebugType::GetType`傳回值的 ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE。</span><span class="sxs-lookup"><span data-stu-id="a3942-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3942-116">需求</span><span class="sxs-lookup"><span data-stu-id="a3942-116">Requirements</span></span>  
 <span data-ttu-id="a3942-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3942-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3942-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3942-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3942-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3942-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3942-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3942-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
