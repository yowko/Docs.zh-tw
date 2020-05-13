---
title: ICorDebugReferenceValue::IsNull 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: e8b778c0880040f5ffd639a445fd5663ce493219
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379089"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="ff083-102">ICorDebugReferenceValue::IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="ff083-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="ff083-103">取得值，指出這個 ICorDebugReferenceValue 是否為 null 值，在此情況下， `ICorDebugReferenceValue` 不會指向物件。</span><span class="sxs-lookup"><span data-stu-id="ff083-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff083-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff083-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff083-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff083-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="ff083-106">脫銷布林值的指標， `true` 如果這個物件是 null，則為， `ICorDebugReferenceValue` 否則 `pbNull` 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="ff083-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff083-107">需求</span><span class="sxs-lookup"><span data-stu-id="ff083-107">Requirements</span></span>  
 <span data-ttu-id="ff083-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff083-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff083-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff083-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff083-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff083-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff083-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff083-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
