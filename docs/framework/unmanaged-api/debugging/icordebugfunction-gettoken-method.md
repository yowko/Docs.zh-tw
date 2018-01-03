---
title: "ICorDebugFunction::GetToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7edf1f9dadafd989197170123cb3cb470a5ea908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="8d731-102">ICorDebugFunction::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="8d731-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="8d731-103">取得此函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d731-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d731-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d731-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d731-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d731-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="8d731-106">[out]指標`mdMethodDef`參考此函式的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d731-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d731-107">需求</span><span class="sxs-lookup"><span data-stu-id="8d731-107">Requirements</span></span>  
 <span data-ttu-id="8d731-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d731-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d731-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d731-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d731-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d731-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d731-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d731-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
