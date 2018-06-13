---
title: ICorDebugArrayValue::GetRank 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdac5bc1d205184771388b13e9b5380ff42bfba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401923"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="3c779-102">ICorDebugArrayValue::GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="3c779-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="3c779-103">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="3c779-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c779-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c779-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c779-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c779-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="3c779-106">[out]在這個維度數目的指標`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="3c779-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c779-107">需求</span><span class="sxs-lookup"><span data-stu-id="3c779-107">Requirements</span></span>  
 <span data-ttu-id="3c779-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c779-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c779-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c779-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c779-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c779-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c779-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c779-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
