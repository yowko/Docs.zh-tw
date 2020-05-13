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
ms.openlocfilehash: e542145e888049231a6c5e4cccbb4ee96c62f98b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213253"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="90005-102">ICorDebugFunction::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="90005-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="90005-103">取得此函式的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="90005-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90005-104">語法</span><span class="sxs-lookup"><span data-stu-id="90005-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90005-105">參數</span><span class="sxs-lookup"><span data-stu-id="90005-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="90005-106">脫銷參考此函式之 `mdMethodDef` 中繼資料的 token 指標。</span><span class="sxs-lookup"><span data-stu-id="90005-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90005-107">需求</span><span class="sxs-lookup"><span data-stu-id="90005-107">Requirements</span></span>  
 <span data-ttu-id="90005-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90005-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90005-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90005-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90005-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90005-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90005-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90005-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
