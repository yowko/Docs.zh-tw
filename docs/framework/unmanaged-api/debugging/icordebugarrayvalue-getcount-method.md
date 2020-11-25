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
ms.openlocfilehash: cd45c6d515648819a83d4e9944eb20d5cd20dd86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698217"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="532de-102">ICorDebugArrayValue::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="532de-102">ICorDebugArrayValue::GetCount Method</span></span>

<span data-ttu-id="532de-103">取得陣列中的元素總數。</span><span class="sxs-lookup"><span data-stu-id="532de-103">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="532de-104">語法</span><span class="sxs-lookup"><span data-stu-id="532de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="532de-105">參數</span><span class="sxs-lookup"><span data-stu-id="532de-105">Parameters</span></span>  

 `pnCount`  
 <span data-ttu-id="532de-106">擴展陣列中元素總數的指標。</span><span class="sxs-lookup"><span data-stu-id="532de-106">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="532de-107">需求</span><span class="sxs-lookup"><span data-stu-id="532de-107">Requirements</span></span>  

 <span data-ttu-id="532de-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="532de-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="532de-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="532de-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="532de-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="532de-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="532de-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="532de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
