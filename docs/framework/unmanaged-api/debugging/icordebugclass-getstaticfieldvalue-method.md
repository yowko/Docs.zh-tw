---
title: ICorDebugClass::GetStaticFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471621"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="770e8-102">ICorDebugClass::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="770e8-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="770e8-103">取得指定的靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="770e8-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="770e8-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="770e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="770e8-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="770e8-106">[in]欄位`Def`參考要擷取欄位的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="770e8-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="770e8-107">[in]ICorDebugFrame 物件，表示要用來區分執行緒、 內容或應用程式網域的靜態變數的框架指標。</span><span class="sxs-lookup"><span data-stu-id="770e8-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="770e8-108">如果靜態欄位相對於執行緒、 內容或應用程式定義域中，框架會決定適當的值。</span><span class="sxs-lookup"><span data-stu-id="770e8-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="770e8-109">[out]ICorDebugValue 物件，表示的靜態欄位值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="770e8-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="770e8-110">備註</span><span class="sxs-lookup"><span data-stu-id="770e8-110">Remarks</span></span>  
 <span data-ttu-id="770e8-111">參數化類型的靜態欄位的值是相對於特定的具現化。</span><span class="sxs-lookup"><span data-stu-id="770e8-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="770e8-112">因此，如果類別建構函式不接受參數的型別<xref:System.Type>，呼叫[icordebugtype:: Getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)而不是`ICorDebugClass::GetStaticFieldValue`。</span><span class="sxs-lookup"><span data-stu-id="770e8-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="770e8-113">需求</span><span class="sxs-lookup"><span data-stu-id="770e8-113">Requirements</span></span>  
 <span data-ttu-id="770e8-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="770e8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="770e8-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="770e8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="770e8-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="770e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="770e8-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="770e8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
