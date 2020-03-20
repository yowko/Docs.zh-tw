---
title: ICorDebugArrayValue::GetDimensions 方法
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 35e043c56977bf644efe1dd9cee1409f50cc877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179020"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="1c600-102">ICorDebugArrayValue::GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="1c600-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="1c600-103">獲取此陣列的每個維度中的元素數。</span><span class="sxs-lookup"><span data-stu-id="1c600-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c600-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c600-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c600-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c600-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="1c600-106">[在]此 ICorDebugArrayValue 物件的維度數。</span><span class="sxs-lookup"><span data-stu-id="1c600-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="1c600-107">此值也是陣列的大小，`dims`因為它的大小等於`ICorDebugArrayValue`物件的維度數。</span><span class="sxs-lookup"><span data-stu-id="1c600-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="1c600-108">[出]整數陣列，每個陣列指定此`ICorDebugArrayValue`物件中維度中的元素數。</span><span class="sxs-lookup"><span data-stu-id="1c600-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c600-109">需求</span><span class="sxs-lookup"><span data-stu-id="1c600-109">Requirements</span></span>  
 <span data-ttu-id="1c600-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c600-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c600-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c600-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c600-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c600-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c600-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c600-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
