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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 972df4613255dc1b71801e02d387a735dfc632c0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477253"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="33668-102">ICorDebugReferenceValue::IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="33668-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="33668-103">取得值，指出此 ICorDebugReferenceValue 是否為 null 值，在此情況下`ICorDebugReferenceValue`未指向物件。</span><span class="sxs-lookup"><span data-stu-id="33668-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33668-104">語法</span><span class="sxs-lookup"><span data-stu-id="33668-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33668-105">參數</span><span class="sxs-lookup"><span data-stu-id="33668-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="33668-106">[out]布林值的指標`true`如果這個`ICorDebugReferenceValue`物件是 null，否則`pbNull`是`false`。</span><span class="sxs-lookup"><span data-stu-id="33668-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33668-107">需求</span><span class="sxs-lookup"><span data-stu-id="33668-107">Requirements</span></span>  
 <span data-ttu-id="33668-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33668-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33668-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33668-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33668-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33668-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33668-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33668-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
