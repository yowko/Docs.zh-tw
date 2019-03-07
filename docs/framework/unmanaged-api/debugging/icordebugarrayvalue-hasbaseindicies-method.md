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
ms.openlocfilehash: 49f5ed8b24d81ba8f32a9fe0ad7488693718bde9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468555"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="7109c-102">ICorDebugArrayValue::HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="7109c-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="7109c-103">取得值，指出這個陣列的任何維度是否具有非零的基底索引。</span><span class="sxs-lookup"><span data-stu-id="7109c-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7109c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7109c-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7109c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7109c-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="7109c-106">[out]布林值的指標`true`如果這個的一或多個維度`ICorDebugArrayValue`物件的基底的索引為非零; 否則布林值是`false`。</span><span class="sxs-lookup"><span data-stu-id="7109c-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7109c-107">需求</span><span class="sxs-lookup"><span data-stu-id="7109c-107">Requirements</span></span>  
 <span data-ttu-id="7109c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7109c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7109c-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7109c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7109c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7109c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7109c-111">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7109c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
