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
ms.openlocfilehash: 683457c249915708becadaeda9dec265666e2023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412103"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="0a11d-102">ICorDebugEval2::CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="0a11d-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="0a11d-103">取得指定的型別，新 ICorDebugValue 其初始值為零或 null 指標。</span><span class="sxs-lookup"><span data-stu-id="0a11d-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a11d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a11d-104">Syntax</span></span>  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a11d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a11d-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="0a11d-106">[in]ICorDebugType 物件，表示類型的指標。</span><span class="sxs-lookup"><span data-stu-id="0a11d-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0a11d-107">[out]位址指標`ICorDebugValue`物件，表示值。</span><span class="sxs-lookup"><span data-stu-id="0a11d-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a11d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0a11d-108">Remarks</span></span>  
 <span data-ttu-id="0a11d-109">`CreateValueForType` 一般化[icordebugeval:: Createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)允許您指定任意物件類型，包括建構類型例如`List<int>`。</span><span class="sxs-lookup"><span data-stu-id="0a11d-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="0a11d-110">這個方法的唯一目的是產生可傳遞至函式評估的值。</span><span class="sxs-lookup"><span data-stu-id="0a11d-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="0a11d-111">類型必須是類別或實值類型。</span><span class="sxs-lookup"><span data-stu-id="0a11d-111">The type must be a class or a value type.</span></span> <span data-ttu-id="0a11d-112">您無法使用這個方法來建立陣列值或字串值。</span><span class="sxs-lookup"><span data-stu-id="0a11d-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a11d-113">需求</span><span class="sxs-lookup"><span data-stu-id="0a11d-113">Requirements</span></span>  
 <span data-ttu-id="0a11d-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a11d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a11d-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a11d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a11d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a11d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a11d-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a11d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
