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
ms.openlocfilehash: 418ebb51df3f2d86011ee2e77022c3ee5c7ac0b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088228"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="a67b2-102">ICorDebugArrayValue::HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="a67b2-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="a67b2-103">取得值，指出此陣列的任何維度是否有非零的基底索引。</span><span class="sxs-lookup"><span data-stu-id="a67b2-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a67b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a67b2-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a67b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="a67b2-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="a67b2-106">脫銷布林值的指標，如果這個 `ICorDebugArrayValue` 物件的一或多個維度具有非零的基底索引，則為 `true`;否則，布林值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a67b2-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a67b2-107">需求</span><span class="sxs-lookup"><span data-stu-id="a67b2-107">Requirements</span></span>  
 <span data-ttu-id="a67b2-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a67b2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a67b2-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a67b2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a67b2-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a67b2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a67b2-111">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a67b2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
