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
ms.openlocfilehash: 3fdd3180a01e4609ac40fd358879c0d2569234ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728377"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="18236-102">ICorDebugReferenceValue::SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="18236-102">ICorDebugReferenceValue::SetValue Method</span></span>

<span data-ttu-id="18236-103">設定指定的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="18236-103">Sets the specified memory address.</span></span> <span data-ttu-id="18236-104">也就是說，這個方法會將此 ICorDebugReferenceValue 設定為指向物件。</span><span class="sxs-lookup"><span data-stu-id="18236-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18236-105">語法</span><span class="sxs-lookup"><span data-stu-id="18236-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18236-106">參數</span><span class="sxs-lookup"><span data-stu-id="18236-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="18236-107">在 `CORDB_ADDRESS` 值，指定此指向的物件位址 `ICorDebugReferenceValue` 。</span><span class="sxs-lookup"><span data-stu-id="18236-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18236-108">需求</span><span class="sxs-lookup"><span data-stu-id="18236-108">Requirements</span></span>  

 <span data-ttu-id="18236-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18236-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18236-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18236-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18236-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18236-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18236-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18236-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
