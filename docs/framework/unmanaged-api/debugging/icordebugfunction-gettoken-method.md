---
title: ICorDebugFunction::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56c8eba49260eba9e3e0ca7e9ab4c7cfcd3261f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995627"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="2d5ba-102">ICorDebugFunction::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="2d5ba-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="2d5ba-103">取得此函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2d5ba-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d5ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d5ba-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d5ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d5ba-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="2d5ba-106">[out]指標`mdMethodDef`參考此函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2d5ba-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d5ba-107">需求</span><span class="sxs-lookup"><span data-stu-id="2d5ba-107">Requirements</span></span>  
 <span data-ttu-id="2d5ba-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d5ba-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d5ba-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d5ba-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d5ba-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d5ba-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d5ba-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d5ba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
