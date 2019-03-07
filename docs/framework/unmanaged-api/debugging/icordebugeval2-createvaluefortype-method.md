---
title: ICorDebugEval2::CreateValueForType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27e40618d6128c21e99745ca45e139a9c21c843
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475030"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="929fb-102">ICorDebugEval2::CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="929fb-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="929fb-103">取得指定的型別，新 ICorDebugValue 其初始值為零或 null 指標。</span><span class="sxs-lookup"><span data-stu-id="929fb-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="929fb-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="929fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="929fb-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="929fb-106">[in]ICorDebugType 物件，表示類型的指標。</span><span class="sxs-lookup"><span data-stu-id="929fb-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="929fb-107">[out]指標的位址`ICorDebugValue`物件，表示值。</span><span class="sxs-lookup"><span data-stu-id="929fb-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="929fb-108">備註</span><span class="sxs-lookup"><span data-stu-id="929fb-108">Remarks</span></span>  
 <span data-ttu-id="929fb-109">`CreateValueForType` 一般化[icordebugeval:: Createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)可讓您指定任意的物件類型，包括建構類型這類`List<int>`。</span><span class="sxs-lookup"><span data-stu-id="929fb-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="929fb-110">這個方法的唯一目的是產生可傳遞至函式評估的值。</span><span class="sxs-lookup"><span data-stu-id="929fb-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="929fb-111">類型必須是類別或實值型別。</span><span class="sxs-lookup"><span data-stu-id="929fb-111">The type must be a class or a value type.</span></span> <span data-ttu-id="929fb-112">您無法使用這個方法來建立陣列的值或字串值。</span><span class="sxs-lookup"><span data-stu-id="929fb-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="929fb-113">需求</span><span class="sxs-lookup"><span data-stu-id="929fb-113">Requirements</span></span>  
 <span data-ttu-id="929fb-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="929fb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="929fb-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="929fb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="929fb-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="929fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="929fb-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="929fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
