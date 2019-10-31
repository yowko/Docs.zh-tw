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
ms.openlocfilehash: 9d5047b1d44f836d10b659f18cf885eba3b0e973
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139828"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="0c62d-102">ICorDebugReferenceValue::IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="0c62d-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="0c62d-103">取得值，指出這個 ICorDebugReferenceValue 是否為 null 值，在此情況下，`ICorDebugReferenceValue` 不會指向物件。</span><span class="sxs-lookup"><span data-stu-id="0c62d-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c62d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c62d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c62d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0c62d-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="0c62d-106">脫銷布林值的指標，如果這個 `ICorDebugReferenceValue` 物件為 null，則為 `true`;否則，會 `false``pbNull`。</span><span class="sxs-lookup"><span data-stu-id="0c62d-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c62d-107">需求</span><span class="sxs-lookup"><span data-stu-id="0c62d-107">Requirements</span></span>  
 <span data-ttu-id="0c62d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c62d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c62d-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c62d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c62d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c62d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c62d-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c62d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
