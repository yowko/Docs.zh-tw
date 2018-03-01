---
title: "ICorDebugCode::GetFunction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d05d5d7172a43ebaa04155fb42c2711eaf1ac085
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="fa0ba-102">ICorDebugCode::GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="fa0ba-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="fa0ba-103">取得與此 「 ICorDebugCode"相關聯 「 ICorDebugFunction"。</span><span class="sxs-lookup"><span data-stu-id="fa0ba-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa0ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa0ba-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa0ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa0ba-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="fa0ba-106">[out]函式的位址指標。</span><span class="sxs-lookup"><span data-stu-id="fa0ba-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa0ba-107">備註</span><span class="sxs-lookup"><span data-stu-id="fa0ba-107">Remarks</span></span>  
 <span data-ttu-id="fa0ba-108">`ICorDebugCode`和`ICorDebugFunction`維護一對一的關聯性。</span><span class="sxs-lookup"><span data-stu-id="fa0ba-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa0ba-109">需求</span><span class="sxs-lookup"><span data-stu-id="fa0ba-109">Requirements</span></span>  
 <span data-ttu-id="fa0ba-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa0ba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa0ba-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa0ba-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa0ba-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa0ba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa0ba-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa0ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa0ba-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa0ba-114">See Also</span></span>  
 
