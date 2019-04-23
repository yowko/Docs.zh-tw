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
ms.openlocfilehash: 71e32211e6ab16fb5e4e2c624dbad3af5fd6b09f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132006"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="b6b2d-102">ICorDebugObjectValue::IsValueClass 方法</span><span class="sxs-lookup"><span data-stu-id="b6b2d-102">ICorDebugObjectValue::IsValueClass Method</span></span>
<span data-ttu-id="b6b2d-103">取得值，指出這個物件的值是否為實值型別。</span><span class="sxs-lookup"><span data-stu-id="b6b2d-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6b2d-104">Syntax</span></span>  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b2d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6b2d-105">Parameters</span></span>  
 `pbIsValueClass`  
 <span data-ttu-id="b6b2d-106">[out]為的布林值的指標`true`如果物件值，表示這個 「 ICorDebugObjectValue 」，是實值型別，而不是參考型別; 否則`pbIsValueClass`是`false`。</span><span class="sxs-lookup"><span data-stu-id="b6b2d-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b2d-107">需求</span><span class="sxs-lookup"><span data-stu-id="b6b2d-107">Requirements</span></span>  
 <span data-ttu-id="b6b2d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b2d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b2d-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6b2d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6b2d-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6b2d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6b2d-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b2d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b2d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b2d-112">See also</span></span>
