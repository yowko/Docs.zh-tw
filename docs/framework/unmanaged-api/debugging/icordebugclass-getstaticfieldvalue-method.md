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
ms.openlocfilehash: dd1608badf553650b05b7de98d9bbcd76b2f3edf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728429"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="075b2-102">ICorDebugClass::GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="075b2-102">ICorDebugClass::GetStaticFieldValue Method</span></span>

<span data-ttu-id="075b2-103">取得指定之靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="075b2-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="075b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="075b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="075b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="075b2-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="075b2-106">在 `Def` 參考要取出之欄位的欄位標記。</span><span class="sxs-lookup"><span data-stu-id="075b2-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="075b2-107">在ICorDebugFrame 物件的指標，表示用來區分執行緒、內容或應用程式域靜態的框架。</span><span class="sxs-lookup"><span data-stu-id="075b2-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="075b2-108">如果靜態欄位相對於執行緒、內容或應用程式域，框架將會決定適當的值。</span><span class="sxs-lookup"><span data-stu-id="075b2-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="075b2-109">擴展ICorDebugValue 物件位址的指標，該物件表示靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="075b2-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="075b2-110">備註</span><span class="sxs-lookup"><span data-stu-id="075b2-110">Remarks</span></span>  

 <span data-ttu-id="075b2-111">若為參數化型別，靜態欄位的值會相對於特定具現化。</span><span class="sxs-lookup"><span data-stu-id="075b2-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="075b2-112">因此，如果類別的函式採用型別的參數 <xref:System.Type> ，請呼叫 [ICorDebugType：： GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) 而不是 `ICorDebugClass::GetStaticFieldValue` 。</span><span class="sxs-lookup"><span data-stu-id="075b2-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="075b2-113">需求</span><span class="sxs-lookup"><span data-stu-id="075b2-113">Requirements</span></span>  

 <span data-ttu-id="075b2-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="075b2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="075b2-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="075b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="075b2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="075b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="075b2-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="075b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
