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
ms.openlocfilehash: 9ffddb8242b6627239a99bd9223b98762910b831
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753245"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="53ba6-102">ICorDebugEval2::CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="53ba6-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="53ba6-103">取得指定的型別，新 ICorDebugValue 其初始值為零或 null 指標。</span><span class="sxs-lookup"><span data-stu-id="53ba6-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ba6-104">語法</span><span class="sxs-lookup"><span data-stu-id="53ba6-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53ba6-105">參數</span><span class="sxs-lookup"><span data-stu-id="53ba6-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="53ba6-106">[in]ICorDebugType 物件，表示類型的指標。</span><span class="sxs-lookup"><span data-stu-id="53ba6-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="53ba6-107">[out]指標的位址`ICorDebugValue`物件，表示值。</span><span class="sxs-lookup"><span data-stu-id="53ba6-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53ba6-108">備註</span><span class="sxs-lookup"><span data-stu-id="53ba6-108">Remarks</span></span>  
 <span data-ttu-id="53ba6-109">`CreateValueForType` 一般化[icordebugeval:: Createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)可讓您指定任意的物件類型，包括建構類型這類`List<int>`。</span><span class="sxs-lookup"><span data-stu-id="53ba6-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="53ba6-110">這個方法的唯一目的是產生可傳遞至函式評估的值。</span><span class="sxs-lookup"><span data-stu-id="53ba6-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="53ba6-111">類型必須是類別或實值型別。</span><span class="sxs-lookup"><span data-stu-id="53ba6-111">The type must be a class or a value type.</span></span> <span data-ttu-id="53ba6-112">您無法使用這個方法來建立陣列的值或字串值。</span><span class="sxs-lookup"><span data-stu-id="53ba6-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ba6-113">需求</span><span class="sxs-lookup"><span data-stu-id="53ba6-113">Requirements</span></span>  
 <span data-ttu-id="53ba6-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53ba6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ba6-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53ba6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53ba6-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53ba6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53ba6-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ba6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
