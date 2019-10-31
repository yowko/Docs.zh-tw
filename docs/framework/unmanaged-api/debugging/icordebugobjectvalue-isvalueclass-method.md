---
title: ICorDebugObjectValue::IsValueClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
ms.openlocfilehash: 0682c0786182422587adb976ff6bc2455b9e5cdc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128940"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="1f253-102">ICorDebugObjectValue::IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="1f253-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="1f253-103">取得值，指出這個物件值是否為實值型別。</span><span class="sxs-lookup"><span data-stu-id="1f253-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f253-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f253-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f253-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f253-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="1f253-106">脫銷布林值的指標，如果物件值（由這個 "ICorDebugObjectValue" 表示）是實數值型別，而不是參考型別，則為 `true`。否則，會 `false``pbIsValueClass`。</span><span class="sxs-lookup"><span data-stu-id="1f253-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f253-107">需求</span><span class="sxs-lookup"><span data-stu-id="1f253-107">Requirements</span></span>  
 <span data-ttu-id="1f253-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f253-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f253-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f253-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f253-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f253-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f253-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f253-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f253-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="1f253-112">See also</span></span>
