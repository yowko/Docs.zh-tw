---
title: ICorDebugObjectValue2::GetVirtualMethodAndType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 252a65c66764d60f5e307ba1eaad4ded34d9744d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162146"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="d9bbd-102">ICorDebugObjectValue2::GetVirtualMethodAndType 方法</span><span class="sxs-lookup"><span data-stu-id="d9bbd-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="d9bbd-103">尚未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="d9bbd-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9bbd-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9bbd-104">Syntax</span></span>  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9bbd-105">備註</span><span class="sxs-lookup"><span data-stu-id="d9bbd-105">Remarks</span></span>  
 <span data-ttu-id="d9bbd-106">取得的介面指標 」 ICorDebugFunction"和"ICorDebugType 」 執行個體表示的最具衍生性的方法和指定的成員參考的型別。</span><span class="sxs-lookup"><span data-stu-id="d9bbd-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9bbd-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9bbd-107">See also</span></span>
