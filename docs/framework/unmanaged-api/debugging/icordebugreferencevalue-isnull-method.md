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
ms.openlocfilehash: bcd4c8ba4b81821ae7dd9deaf0f76a76d335aff8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728390"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="9b58c-102">ICorDebugReferenceValue::IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="9b58c-102">ICorDebugReferenceValue::IsNull Method</span></span>

<span data-ttu-id="9b58c-103">取得值，這個值表示此 ICorDebugReferenceValue 是否為 null 值，在此情況下，不 `ICorDebugReferenceValue` 會指向物件。</span><span class="sxs-lookup"><span data-stu-id="9b58c-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b58c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b58c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b58c-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b58c-105">Parameters</span></span>  

 `pbNull`  
 <span data-ttu-id="9b58c-106">擴展布林值的指標， `true` 如果這個 `ICorDebugReferenceValue` 物件為 null，則為，否則 `pbNull` 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9b58c-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b58c-107">需求</span><span class="sxs-lookup"><span data-stu-id="9b58c-107">Requirements</span></span>  

 <span data-ttu-id="9b58c-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b58c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b58c-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b58c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b58c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b58c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b58c-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b58c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
