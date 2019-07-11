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
ms.openlocfilehash: bcbe9a701b91a063e19fec5aae9cc2687b1f279f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766141"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="eb8d4-102">ICorDebugObjectValue2::GetVirtualMethodAndType 方法</span><span class="sxs-lookup"><span data-stu-id="eb8d4-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>
<span data-ttu-id="eb8d4-103">尚未實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="eb8d4-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb8d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb8d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb8d4-105">備註</span><span class="sxs-lookup"><span data-stu-id="eb8d4-105">Remarks</span></span>  
 <span data-ttu-id="eb8d4-106">取得的介面指標 」 ICorDebugFunction"和"ICorDebugType 」 執行個體表示的最具衍生性的方法和指定的成員參考的型別。</span><span class="sxs-lookup"><span data-stu-id="eb8d4-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8d4-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb8d4-107">See also</span></span>
