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
ms.openlocfilehash: 892471e7b35b4f4093df3f86d4777947b6e484e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378309"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="0564f-102">ICorDebugReferenceValue::SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="0564f-102">ICorDebugReferenceValue::SetValue Method</span></span>
<span data-ttu-id="0564f-103">設定指定的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="0564f-103">Sets the specified memory address.</span></span> <span data-ttu-id="0564f-104">也就是說，這個方法會將此 ICorDebugReferenceValue 設定為指向物件。</span><span class="sxs-lookup"><span data-stu-id="0564f-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0564f-105">語法</span><span class="sxs-lookup"><span data-stu-id="0564f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0564f-106">參數</span><span class="sxs-lookup"><span data-stu-id="0564f-106">Parameters</span></span>  
 `value`  
 <span data-ttu-id="0564f-107">在`CORDB_ADDRESS`值，指定這個所指向之物件的位址 `ICorDebugReferenceValue` 。</span><span class="sxs-lookup"><span data-stu-id="0564f-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0564f-108">需求</span><span class="sxs-lookup"><span data-stu-id="0564f-108">Requirements</span></span>  
 <span data-ttu-id="0564f-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0564f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0564f-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0564f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0564f-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0564f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0564f-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0564f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
