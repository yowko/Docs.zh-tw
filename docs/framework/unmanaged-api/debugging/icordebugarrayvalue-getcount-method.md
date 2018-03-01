---
title: "ICorDebugArrayValue::GetCount 方法"
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
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a4dfdf6ad1fc50cbca039d50b32bc81b6b977ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="c2125-102">ICorDebugArrayValue::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="c2125-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="c2125-103">取得陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="c2125-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2125-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2125-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2125-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2125-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="c2125-106">[out]指向陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="c2125-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2125-107">需求</span><span class="sxs-lookup"><span data-stu-id="c2125-107">Requirements</span></span>  
 <span data-ttu-id="c2125-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2125-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2125-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2125-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2125-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2125-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2125-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2125-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
