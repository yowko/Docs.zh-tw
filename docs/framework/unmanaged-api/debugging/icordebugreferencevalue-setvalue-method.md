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
ms.openlocfilehash: 804aa4a6508713b2d6f2d154fc47e09638994468
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747359"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="8ff28-102">ICorDebugReferenceValue::SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="8ff28-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="8ff28-103">設定指定的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="8ff28-103">Sets the specified memory address.</span></span> <span data-ttu-id="8ff28-104">也就是說，這個方法會設定這個 ICorDebugReferenceValue 指向物件。</span><span class="sxs-lookup"><span data-stu-id="8ff28-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff28-105">語法</span><span class="sxs-lookup"><span data-stu-id="8ff28-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff28-106">參數</span><span class="sxs-lookup"><span data-stu-id="8ff28-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="8ff28-107">[in]A`CORDB_ADDRESS`值，指定此物件的位址`ICorDebugReferenceValue`點。</span><span class="sxs-lookup"><span data-stu-id="8ff28-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff28-108">需求</span><span class="sxs-lookup"><span data-stu-id="8ff28-108">Requirements</span></span>  
 <span data-ttu-id="8ff28-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ff28-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff28-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ff28-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ff28-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ff28-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ff28-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff28-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
