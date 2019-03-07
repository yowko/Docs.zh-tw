---
title: ICorDebugArrayValue::GetCount 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d00c04f3719d6fb340541d3301d4dc4a3f95ca40
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495620"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="00319-102">ICorDebugArrayValue::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="00319-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="00319-103">取得陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="00319-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00319-104">語法</span><span class="sxs-lookup"><span data-stu-id="00319-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00319-105">參數</span><span class="sxs-lookup"><span data-stu-id="00319-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="00319-106">[out]指標的陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="00319-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00319-107">需求</span><span class="sxs-lookup"><span data-stu-id="00319-107">Requirements</span></span>  
 <span data-ttu-id="00319-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00319-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00319-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00319-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00319-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00319-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00319-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00319-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
