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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645717"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="86c35-102">ICorDebugArrayValue::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="86c35-102">ICorDebugArrayValue::GetCount Method</span></span>
<span data-ttu-id="86c35-103">取得陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="86c35-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c35-104">語法</span><span class="sxs-lookup"><span data-stu-id="86c35-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86c35-105">參數</span><span class="sxs-lookup"><span data-stu-id="86c35-105">Parameters</span></span>  
 `pnCount`  
 <span data-ttu-id="86c35-106">[out]指標的陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="86c35-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c35-107">需求</span><span class="sxs-lookup"><span data-stu-id="86c35-107">Requirements</span></span>  
 <span data-ttu-id="86c35-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86c35-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c35-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86c35-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86c35-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86c35-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86c35-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c35-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
