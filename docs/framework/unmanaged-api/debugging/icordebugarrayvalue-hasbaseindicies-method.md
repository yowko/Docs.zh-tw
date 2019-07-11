---
title: ICorDebugArrayValue::HasBaseIndicies 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c488ca3a77f2c2b2a40c6143989cd86adf071787
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737426"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="8afd3-102">ICorDebugArrayValue::HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="8afd3-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="8afd3-103">取得值，指出這個陣列的任何維度是否具有非零的基底索引。</span><span class="sxs-lookup"><span data-stu-id="8afd3-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="8afd3-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8afd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="8afd3-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="8afd3-106">[out]布林值的指標`true`如果這個的一或多個維度`ICorDebugArrayValue`物件的基底的索引為非零; 否則布林值是`false`。</span><span class="sxs-lookup"><span data-stu-id="8afd3-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8afd3-107">需求</span><span class="sxs-lookup"><span data-stu-id="8afd3-107">Requirements</span></span>  
 <span data-ttu-id="8afd3-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8afd3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8afd3-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8afd3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8afd3-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8afd3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8afd3-111">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8afd3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
