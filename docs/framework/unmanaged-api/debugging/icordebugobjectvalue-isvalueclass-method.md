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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b08937182797c8e94048d734d65473fad21b85cc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766306"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="3e97b-102">ICorDebugObjectValue::IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="3e97b-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="3e97b-103">取得值，指出這個物件的值是否為實值型別。</span><span class="sxs-lookup"><span data-stu-id="3e97b-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e97b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e97b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e97b-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e97b-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="3e97b-106">[out]為的布林值的指標`true`如果物件值，表示這個 「 ICorDebugObjectValue 」，是實值型別，而不是參考型別; 否則`pbIsValueClass`是`false`。</span><span class="sxs-lookup"><span data-stu-id="3e97b-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e97b-107">需求</span><span class="sxs-lookup"><span data-stu-id="3e97b-107">Requirements</span></span>  
 <span data-ttu-id="3e97b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e97b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e97b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e97b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e97b-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e97b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e97b-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e97b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e97b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e97b-112">See also</span></span>
