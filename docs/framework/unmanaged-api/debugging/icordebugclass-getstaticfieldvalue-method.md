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
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125753"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="86cd7-102">ICorDebugClass::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="86cd7-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="86cd7-103">取得指定靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="86cd7-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cd7-104">語法</span><span class="sxs-lookup"><span data-stu-id="86cd7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86cd7-105">參數</span><span class="sxs-lookup"><span data-stu-id="86cd7-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="86cd7-106">在欄位 `Def` token，此權杖會參考要抓取的欄位。</span><span class="sxs-lookup"><span data-stu-id="86cd7-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="86cd7-107">在ICorDebugFrame 物件的指標，代表要用來區分執行緒、內容或應用程式域靜態變數的框架。</span><span class="sxs-lookup"><span data-stu-id="86cd7-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="86cd7-108">如果靜態欄位是相對於執行緒、內容或應用程式域，則此框架會決定適當的值。</span><span class="sxs-lookup"><span data-stu-id="86cd7-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="86cd7-109">脫銷ICorDebugValue 物件位址的指標，表示靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="86cd7-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86cd7-110">備註</span><span class="sxs-lookup"><span data-stu-id="86cd7-110">Remarks</span></span>  
 <span data-ttu-id="86cd7-111">針對參數化型別，靜態欄位的值是相對於特定具現化。</span><span class="sxs-lookup"><span data-stu-id="86cd7-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="86cd7-112">因此，如果類別的函式接受 <xref:System.Type>類型的參數，請呼叫[ICorDebugType：： GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) ，而不是 `ICorDebugClass::GetStaticFieldValue`。</span><span class="sxs-lookup"><span data-stu-id="86cd7-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86cd7-113">需求</span><span class="sxs-lookup"><span data-stu-id="86cd7-113">Requirements</span></span>  
 <span data-ttu-id="86cd7-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86cd7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86cd7-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86cd7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86cd7-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86cd7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86cd7-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86cd7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
