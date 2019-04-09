---
title: ICorDebugCode::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0104a52c3aa206f86daff30d9d16298e6beae324
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099452"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="bb6bb-102">ICorDebugCode::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="bb6bb-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="bb6bb-103">取得與此 「 ICorDebugCode"相關聯 「 ICorDebugFunction"。</span><span class="sxs-lookup"><span data-stu-id="bb6bb-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb6bb-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb6bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb6bb-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="bb6bb-106">[out]函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="bb6bb-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb6bb-107">備註</span><span class="sxs-lookup"><span data-stu-id="bb6bb-107">Remarks</span></span>  
 `ICorDebugCode` <span data-ttu-id="bb6bb-108">和`ICorDebugFunction`維護一對一的關聯性。</span><span class="sxs-lookup"><span data-stu-id="bb6bb-108">and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6bb-109">需求</span><span class="sxs-lookup"><span data-stu-id="bb6bb-109">Requirements</span></span>  
 <span data-ttu-id="bb6bb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb6bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6bb-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb6bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb6bb-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb6bb-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bb6bb-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="bb6bb-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb6bb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb6bb-114">See also</span></span>
