---
title: ICorDebugReferenceValue::SetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59ef7bf8f17e79c9ae7b80dd314a5afce7fa9584
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474172"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="cf4bc-102">ICorDebugReferenceValue::SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="cf4bc-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="cf4bc-103">設定指定的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="cf4bc-103">Sets the specified memory address.</span></span> <span data-ttu-id="cf4bc-104">也就是說，這個方法會設定這個 ICorDebugReferenceValue 指向物件。</span><span class="sxs-lookup"><span data-stu-id="cf4bc-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="cf4bc-105">Syntax</span></span>  
  
```  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf4bc-106">參數</span><span class="sxs-lookup"><span data-stu-id="cf4bc-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="cf4bc-107">[in]A`CORDB_ADDRESS`值，指定此物件的位址`ICorDebugReferenceValue`點。</span><span class="sxs-lookup"><span data-stu-id="cf4bc-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf4bc-108">需求</span><span class="sxs-lookup"><span data-stu-id="cf4bc-108">Requirements</span></span>  
 <span data-ttu-id="cf4bc-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf4bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf4bc-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf4bc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf4bc-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf4bc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf4bc-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf4bc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
