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
ms.openlocfilehash: a9d1faf5a834cb5d9be19f995aaa3eee1202171b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727441"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="c2ffb-102">ICorDebugArrayValue::HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="c2ffb-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>

<span data-ttu-id="c2ffb-103">取得值，這個值會指出這個陣列的任何維度是否有非零的基底索引。</span><span class="sxs-lookup"><span data-stu-id="c2ffb-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ffb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2ffb-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2ffb-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2ffb-105">Parameters</span></span>  

 `pbHasBaseIndicies`  
 <span data-ttu-id="c2ffb-106">擴展布林值的指標， `true` 如果這個物件的一或多個維度 `ICorDebugArrayValue` 具有非零的基底索引，則為，否則布林值為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c2ffb-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ffb-107">需求</span><span class="sxs-lookup"><span data-stu-id="c2ffb-107">Requirements</span></span>  

 <span data-ttu-id="c2ffb-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2ffb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ffb-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2ffb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2ffb-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2ffb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2ffb-111">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ffb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
