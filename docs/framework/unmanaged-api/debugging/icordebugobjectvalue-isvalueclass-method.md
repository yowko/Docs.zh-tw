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
ms.openlocfilehash: 7b637889986425767fd7e1166c73df3301075422
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695266"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="dba22-102">ICorDebugObjectValue::IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="dba22-102">ICorDebugObjectValue::IsValueClass Method</span></span>

<span data-ttu-id="dba22-103">取得值，這個值會指出這個物件值是否為實值型別。</span><span class="sxs-lookup"><span data-stu-id="dba22-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba22-104">語法</span><span class="sxs-lookup"><span data-stu-id="dba22-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba22-105">參數</span><span class="sxs-lookup"><span data-stu-id="dba22-105">Parameters</span></span>  

 `pbIsValueClass`  
 <span data-ttu-id="dba22-106">擴展布林值的指標， `true` 如果物件值（以這個 "ICorDebugObjectValue" 表示）是實值型別，而不是參考型別，則為，否則 `pbIsValueClass` 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="dba22-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba22-107">需求</span><span class="sxs-lookup"><span data-stu-id="dba22-107">Requirements</span></span>  

 <span data-ttu-id="dba22-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dba22-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba22-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dba22-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dba22-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba22-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba22-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba22-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba22-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba22-112">See also</span></span>
