---
title: ICorDebugEval::IsActive 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fe29b3e35d2fbd42fac2d9ec1d1c594abe1239c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411154"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="10794-102">ICorDebugEval::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="10794-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="10794-103">取得值，指出目前是否正在執行此 ICorDebugEval 物件。</span><span class="sxs-lookup"><span data-stu-id="10794-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10794-104">語法</span><span class="sxs-lookup"><span data-stu-id="10794-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10794-105">參數</span><span class="sxs-lookup"><span data-stu-id="10794-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="10794-106">[out]值，指出這項評估是否作用中的指標。</span><span class="sxs-lookup"><span data-stu-id="10794-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10794-107">需求</span><span class="sxs-lookup"><span data-stu-id="10794-107">Requirements</span></span>  
 <span data-ttu-id="10794-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10794-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10794-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10794-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10794-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10794-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10794-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10794-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
