---
title: ICorDebugGenericValue::SetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6907cdf78fc70c75ddd711cd8593427857b172
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756887"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="1c9ac-102">ICorDebugGenericValue::SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="1c9ac-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="1c9ac-103">複製指定的緩衝區中的新值。</span><span class="sxs-lookup"><span data-stu-id="1c9ac-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c9ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c9ac-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c9ac-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c9ac-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="1c9ac-106">[in]要從中複製值的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="1c9ac-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c9ac-107">備註</span><span class="sxs-lookup"><span data-stu-id="1c9ac-107">Remarks</span></span>  
 <span data-ttu-id="1c9ac-108">若是參考類型，值會是參考，而不是內容。</span><span class="sxs-lookup"><span data-stu-id="1c9ac-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c9ac-109">需求</span><span class="sxs-lookup"><span data-stu-id="1c9ac-109">Requirements</span></span>  
 <span data-ttu-id="1c9ac-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c9ac-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c9ac-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c9ac-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c9ac-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c9ac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c9ac-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c9ac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
